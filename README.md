# healthylinkx-mcp-server
MCP interface to Healthylinkx functionality instead of an API. Allows integration with LLM apps and agents.

Healthylinkx helps you find doctors with the help of your social network. Think of Healthylinkx as a combination of Yelp, Linkedin and Facebook.

Healthylinkx is an early prototype that combines open data of doctors and specialists from the US Department of Health. It allows you to search for doctors based on location, specialization, genre or name.

Healthylinx is a classic three tiers app: front-end (ux), service API and data store. This architecture makes it very adequate to test different technologies and I use it for getting my hands dirty on new stuff.

This repo replaces the Healthylinkx API with a MCP Server. With this new interface you can integrate Healthylinkx with any LLM powered app or agent. 

We use different AWS resources: RDS for the datastore and Lambda for the MCP Server.

To know more about the datastore this repo has more details https://github.com/mulargui/healthylinkx-mysql.git

To build the MCP Server we used Anthropic's modelcontextprotocol SDK for Typescript: https://github.com/modelcontextprotocol/typescript-sdk. This SDK implements a server using express. AWS Lambda sounds like a natural choice to run a MCP Server in the cloud but due the SDK implements a web server, we used AWS Lambda Web Adapter to route Lambda requests to the web server; more details here: https://github.com/awslabs/aws-lambda-web-adapter/tree/main/examples/expressjs-zip

We used MCP Inspector to test the MCP Server. More about MCP Inspector here: https://github.com/modelcontextprotocol/inspector.


**Files and directories:**

/docs - Documentation of the code (partial) generated automatically.\
/mcp/src - code of the MCP Server.\
/mcp/test - Shellscript to use MCP Inspector in a container.\
/mcp/infra - code to deploy and delete the MCP Server using the AWS SDK for node.js.\
/config.json - Configuration values are in this file.\
/deploy.sh and remove.sh - shellscripts to deploy or remove all the infrastructure from/to AWS.\
/runlocally.sh - run the MCP Server locally in a container. Great for development and debugging.

Enjoy playing with MCP!!!
