# mcp-apollo-server

## Deployment Procedure

1. Edit mcp.yaml file to include existing apollo graphQL endpoint and Authorization.
2. Edit schema.graphql to include the schema of the existing apollo instance
3. Include the required operations (queries & mutations) in /operations folder or update mcp.yaml to use apollo operations collection (source & id). The collection should be in the apollo studio account included in the .env file.
4. Create the docker image "docker build -f mcp.Dockerfile -t nextgenoss-mcp ."
5. Execute the docker container "docker run -p 8002:8000 --env-file .env -v ${pwd}/mcp.yaml:/mcp.yaml nextgenoss-mcp /mcp.yaml"
6. Test the server and the tools with MCP Inspector "docker run --rm -e HOST=0.0.0.0 -p 6274:6274 -p 6277:6277 ghcr.io/modelcontextprotocol/inspector:latest" - localhost:6274 - MCP_URL: http://host.docker.internal:8002/mcp
7. Create an MCP Client. 