# Remote MCP Server Authentication Assessment

## Exposed Transports and Routes
- The server chooses its transport at runtime and, for HTTP mode, simply calls `mcp.run_streamable_http_async()` after logging the base and MCP endpoints—there is no additional guard layer in front of the HTTP listener.
- A `/health` route is registered via `@mcp.custom_route('/health')` that unconditionally returns a JSON "healthy" response, again without any access control hooks.

## Default Network Binding
- The default configuration binds the HTTP transport to `0.0.0.0:8000`, meaning the service listens on all network interfaces unless an operator overrides the host/port settings. No TLS or proxy configuration is specified in the shipped config file.

## Tool Accessibility
- All MCP tools—including state-changing operations such as `delete_entity_edge`, `delete_episode`, and `clear_graph`—are decorated directly with `@mcp.tool()` and rely solely on successful request handling. They perform no user authentication, authorization checks, or token validation before executing destructive actions against the backing graph store.

## Absence of Authentication/TLS Features
- Within the MCP server source and configuration, there are no options for HTTP basic auth, API tokens, OAuth, or TLS termination. The only authentication-related utilities present in the codebase target outbound cloud services (e.g., Azure AD tokens for LLM providers) rather than protecting inbound MCP traffic.

## Overall Assessment
- The remote MCP server, as currently implemented, exposes its HTTP and health endpoints publicly when bound to a routable interface. No in-server mechanisms enforce client authentication, authorization, or encrypted transport. Operators must therefore deploy the service behind an external gateway (reverse proxy, service mesh, VPN, etc.) to add TLS and authentication if exposure beyond localhost is required.
