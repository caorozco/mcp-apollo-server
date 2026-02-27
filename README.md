# mcp-apollo-server

## Deployment Procedure

1. Edit mcp.yaml file to include existing apollo graphQL endpoint and Authorization
2. Edit schema.graphql to include the schema of the existing apollo instance
3. Include required operations (queries & mutations)
4. Create docker image "docker build -f mcp.Dockerfile -t nextgenoss-mcp ."
5. Create docker container "sudo docker run -p 8002:8000 --env-file .env -v $(pwd)/mcp.yaml:/mcp.yaml nextgenoss-mcp /mcp.yaml"
6. Test with MCP Inspector "npx @modelcontextprotocol/inspector http://127.0.0.1:8002/mcp --transport http"
7. Create MCP Client 