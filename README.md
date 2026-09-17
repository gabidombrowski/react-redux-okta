# Use Redux to Manage Authenticated State in a React App

This is the demo app for the Okta Developer blog post
[How to Build a Secure React and Fastify API App](https://developer.okta.com/blog/2022/12/06/react-fastify-postgres).

It shows a React app that signs users in with Okta and then keeps the
authenticated user's profile in two places:

- **Redux** ([src/redux-state/userProfileSlice.tsx](src/redux-state/userProfileSlice.tsx))
  holds the email, given name, and family name.
- **React Context** ([src/components/home.tsx](src/components/home.tsx))
  holds the username and locale.

The dashboard reads from both so you can compare the two approaches side by side.

The project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app)
using the [Redux Toolkit](https://redux-toolkit.js.org/) TypeScript template.

## Prerequisites

- [Node.js](https://nodejs.org/) and npm
- An [Okta Developer account](https://developer.okta.com/signup/)

## Create an Okta application

Create a Single-Page App integration in your Okta org, either through the Admin
Console or the [Okta CLI](https://cli.okta.com/), with these settings:

| Setting | Value |
| --- | --- |
| Sign-in redirect URI | `http://localhost:3000/login/callback` |
| Sign-out redirect URI | `http://localhost:3000` |

Note the **Client ID** and your org's **Issuer** URL. You will need both below.

## Configure the app

Create a `.env` file in the project root:

```
REACT_APP_OKTA_ISSUER=https://{yourOktaDomain}/oauth2/default
REACT_APP_OKTA_CLIENTID={yourClientId}
REACT_APP_OKTA_BASE_REDIRECT_URI=http://localhost:3000
```

`.env` is ignored by git so your credentials stay local.

## Run the app

```bash
npm install
npm start
```

Open [http://localhost:3000](http://localhost:3000), click **Login**, and sign
in with a user from your Okta org. After the redirect you will land on the
dashboard. Click **Show more** to see the profile fields pulled from Redux and
from Context.

## Other scripts

- `npm test` runs the test suite in watch mode.
- `npm run build` creates a production build in the `build` folder.

## Learn more

- [Okta React SDK](https://github.com/okta/okta-react)
- [Okta Auth JS](https://github.com/okta/okta-auth-js)
- [Redux Toolkit](https://redux-toolkit.js.org/)
- [React Context](https://react.dev/learn/passing-data-deeply-with-context)
