const loginUrl = 'http://192.168.50.103:3000/api/v1/auth/login';

const username = 'a@gmail.com';
const password = '111111111';

const getTokenRequest = {
  method: 'POST',
  url: loginUrl,
  body: {
      mode: 'formdata',
      formdata: [
          { key: 'username', value: username },
          { key: 'password', value: password }
      ]
  }
};

pm.sendRequest(getTokenRequest, (err, response) => {
  const jsonResponse = response.json();
  const newAccessToken = jsonResponse.access_token;

  console.log(newAccessToken);

  pm.collectionVariables.set('AUTH_BEARER_TOKEN', "Bearer " + newAccessToken);
});
