# Setting Up Environments

If for example, if you have a `/login` endpoint that returns a token.

1. Create a new environment in postman.
2. Create a variable called token that has no initial value.
3. The in your `/login` request, go to the Tests tabs
4. Click on Post-response
5. Copy and paste the js code below
6. This will run that script every time that your `/login` request is processed, and set token
7. In your subsequent requests that need the token. Just make sure it uses token by using double braces.
   ex. Authorization, Bearer `{{token}}`

```js
const jsonData = pm.response.json();
pm.environment.set("token", jsonData.token);
```
