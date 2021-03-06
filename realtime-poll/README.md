# hasura-realtime-poll

A demo application to showcase real-time capabilities of [Hasura GraphQL
Engine](https://github.com/hasura/graphql-engine).

[![Edit realtime-poll](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/github/hasura/graphql-engine/tree/master/community/sample-apps/realtime-poll?fontsize=14)

The Realtime Poll application is built using React and is powered by Hasura
GraphQL Engine over YugabyteDB. It has an interface for users to cast vote on a
poll and the results are updated in the on-screen bar chart, in real-time.

The application makes use of Hasura GraphQL Engine's real-time capabilities
using `subscription`. There is no backend code involved. The application is
hosted on GitHub pages and the Yugabyte+GraphQL Engine is running on YugabyteDB.
  
# Running the app yourself

- Deploy GraphQL Engine on Hasura Cloud and setup Yugabyte Cloud Instance:
  
  [![Deploy to Hasura Cloud](https://graphql-engine-cdn.hasura.io/img/deploy_to_hasura.png)](https://cloud.hasura.io/)
- Get the Hasura app URL (say `hasura-yb-demo.hasura.app`)
- Clone this repo:
  ```bash
  git clone https://github.com/yugabyte/yugabyte-graphql-apps
  cd realtime-poll
  ```
- [Install Hasura CLI](https://hasura.io/docs/latest/graphql/core/hasura-cli/install-hasura-cli.html)
- Goto `hasura/` and edit `config.yaml`:
  ```yaml
  endpoint: https://hasura-yb-demo.hasura.app
  ```
- Apply the migrations:
  ```bash
  hasura migrate apply --database-name yugabyte-cloud-instance
  ```
- Edit `HASURA_GRAPHQL_ENGINE_HOSTNAME` and `hasura_secret` in `src/apollo.js` and set it to the
  Hasura app URL:
  ```js
  export const HASURA_GRAPHQL_ENGINE_HOSTNAME = 'hasura-yb-demo.hasura.app';
  const hasura_secret = '';
  ```
  Note: Obtain `hasura_secret` from Hasura Cloud Console.
- Run the app (go the root of repo):
  ```bash
  npm install
  npm start
  ```
