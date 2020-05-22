---
version: 0.2.2
---

# Authn


## Index

- [Authn](#authn)
  - [Index](#index)
  - [How to use](#how-to-use)
    - [Resource Owner Password Credentials](#resource-owner-password-credentials)
    - [Refresh Token](#refresh-token)
    - [Client Credentials](#client-credentials)
    - [Authorization Code](#authorization-code)
    - [Implicit](#implicit)
    - [Service Account (jwt-bearer)](#service-account-jwt-bearer)
    - [JWT Claims](#jwt-claims)
    - [JWT examples](#jwt-examples)
  - [Service Account](#service-account)
    - [Assertion for oauth](#assertion-for-oauth)


## How to use


**NOTE: this examples are very simple and don't describe with enough detail concepts like `application`. To
learn more about them, go the [Confluence documentation](https://mmsistemas.atlassian.net/wiki/spaces/TECH/pages/745799877/Squad+-+Login-API)**

### Resource Owner Password Credentials

This grant type is meant for clients that are strongly trusted by the authorization server
(in this case Authn) and **MUST NEVER** be used by third parties!

On the other hand, this grant type requires that the client authenticates with `client_id` and `client_secret`. Therefore, it **MUST NEVER**
be used in a SPA client because the browser has no means to store this credentials securely.

Here there is a video from OpenID's founder Nat Sakimura explaining the reasons why we must not use password grant type.
https://www.youtube.com/watch?v=qMtYaDmhnHU&feature=youtu.be

Once you understand these important limitations and given a `client_id` and a `client_secret` you can make
a login request like the following one:

```shell
curl -X POST \
  https://<authn_host>/oauth/token \
  -H 'Authorization: Basic S2dWeERwczBvZlNoS2c5dWtQZ0s6d3lNcm1JdWhBWFVSbjdaRy1RZWM4TzRxbUVoV0ppQ1JJQnFlZHY2a0p2cz0=' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'grant_type=password&password=123456&username=622607757'
```

- `Authorization` header is a basic authentication that contains the client credentials formatted as `<client_id>:<client_secret>` and encoded with `base64`.
- `grant_type` parameter defines the OAuth2 flow that is going to be used; in this case `password`.
- `username` is the identifier of the user (resource owner) that the client is trying to authenticate.
- `password` is a secret used to verify the identity of the resource owner that is requesting access.

If the request is successful, you should get a response like the following:

```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsImtpZCI6IjYwZTBjNDM4LTAwNGMtNDlmMC04MzUzLWZkMDYxNTkxMWMwOSIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJBdWRpZW5jZSIsImNpZCI6IjYxQnFpT2tuSkJ5UWRCU3dLdjhsIiwiZXhwIjoxNTUyNDI4NjQzLCJncm91cHMiOlsiY3VzdG9tZXIiXSwiaWF0IjoxNTUyMzQyMjQzLCJpc3MiOiJsdW1pZXJlLmF1dGgubWFzbW92aWwuY29tIiwic2NvcGVzIjoiYXBpOmV2ZXJ5dGhpbmciLCJzdWIiOiI2MjI2MDc3NTcifQ.k9NwTKQM8u4aq-w3TXtszknOtGDgwFss4aunCgcw1VOIpYP35jlNN9GIN-Slt7kaHwruaI1BF9JShta3CQcrVD8b7YJHe3DWm8e0o7e32fXm5OdfIt4Uw6Hpn344A5jfmUefWGLqulqWL2sDfhx1hhXXfMpZrSuSVxYfow2FsvP_Q2dJfU1y-3gtvTm9eFcFl5szE2Wj4dZf-4ewH4uvzWlgkqLjpX3mfewITdmK5ME0lDUU0MUafeVPvz77TfMyv_smzqtkyg0jf_X9XxdRdkcXjH-uvNuBxIgenWsGBFXZeBFxZyEUuPLOPCHfTtDu-Jg126p9zusjfkFFpp-wbA",
  "expires_in": 3600,
  "refresh_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaWQiOiI2MUJxaU9rbkpCeVFkQlN3S3Y4bCJ9.umCmY1DD7piI--itKuRLeg3kPIuDWVFCqT67rMLU1pUH9t_WOOatFEPbk_TcdnWbr2Uf-_VQDIDCIqrxP5nCmUwEFs3vTfF4pJghEiBX8HK0lQ1gjiVj6bX8xG7kk-1jD5C1pWTymuCANjN9WyyS6P_XRUEy1ogU4cV64RlYfe30Nd5J1kzFKQdEfnkxq1PfBJxaH4pey8NSvEaPU8sELqXIj9Ak6sJ5L1FEioGZUc1jxEhogS4QZooEJQDkM3ZAHN0fikrBRn1NIp1VcXag251YMjhywkZKgdlUNQC8OkPxqrpujrZDH8sBzvDKlfz6WF8BNMcu13KVD3rMcMF1kA",
  "token_type": "Bearer"
}
```

- `access_token` is a signed JWT used by a user to authenticate himself against Istio's service mesh.
- `expires_in` is the time that the access_token will be valid. Once it expires, the access_token won't be valid and the user won't be able to authenticate with it.
- `refresh_token` is another signed JWT, that is used to obtain a new access_token once it expires. It is used with the [refresh grant type](#refresh-token).
- `token_type` defines the type of the access_token that has been generated. This will normally be used in the Authorization header to indicate which kind of authentication has the request.
- `require_password_change` defines if the user must be change the password.

In the case of Agent login with uuid, before oauth call, you must be get a valid uuid with a call like this:

```shell
curl -X POST \
  https://api.dev.ovid-project.com/login/uuid \
  -H 'Authorization: Basic aXRtYXNtb3ZpbDo3NEFxckprWG1CZzFSNVNNL0xxWmJ0cGdXVXhaQld6S2tnMUl4NWIr' \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
    "username": "MYSFID"
}'
```

And then you could call to authn for a token with username (sfid) and password (uuid).


### Refresh Token

Like in the [password grant type](#resource-owner-password-credentials) you **MUST** respect the premise of **NEVER** use this grant type in a public client like a SPA. The browser has 
no means to securely store a `client_secret` or a `refresh_token`.

To refresh a token, you can use a request like the following one:

```shell
curl -X POST \
  https://<authn_host>/oauth/token \
  -H 'Authorization: Basic S2dWeERwczBvZlNoS2c5dWtQZ0s6d3lNcm1JdWhBWFVSbjdaRy1RZWM4TzRxbUVoV0ppQ1JJQnFlZHY2a0p2cz0=' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'grant_type=refresh_token&refresh_token=eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaWQiOiI2MUJxaU9rbkpCeVFkQlN3S3Y4bCJ9.umCmY1DD7piI--itKuRLeg3kPIuDWVFCqT67rMLU1pUH9t_WOOatFEPbk_TcdnWbr2Uf-_VQDIDCIqrxP5nCmUwEFs3vTfF4pJghEiBX8HK0lQ1gjiVj6bX8xG7kk-1jD5C1pWTymuCANjN9WyyS6P_XRUEy1ogU4cV64RlYfe30Nd5J1kzFKQdEfnkxq1PfBJxaH4pey8NSvEaPU8sELqXIj9Ak6sJ5L1FEioGZUc1jxEhogS4QZooEJQDkM3ZAHN0fikrBRn1NIp1VcXag251YMjhywkZKgdlUNQC8OkPxqrpujrZDH8sBzvDKlfz6WF8BNMcu13KVD3rMcMF1kA'
```

- `Authorization` header is a basic authentication that contains the client credentials formatted as `<client_id>:<client_secret>` and encoded with `base64`.
- `grant_type` parameter defines the OAuth2 flow that is going to be used; in this case `refresh_token`.
- `refresh_token` is the refresh token itself. 

If everything worked as expected, you should get an identical response to the [password grant type](#resource-owner-password-credentials).

### Client Credentials
The Client Credentials Grant (defined in RFC 6749, section 4.4) allows an application to request an Access Token using its Client Id and Client Secret. It is used for non interactive applications (a CLI, a daemon, or a Service running on your backend) where the token is issued to the application itself, instead of an end user.

To use this flow, make sure you that your application has the Client Credentials grant type enabled.

### Authorization Code
This authentication flow is the recommended because the client doesn't need to manage the resource owner's (end user)
credentials. Instead, it is the authorization server itself the one and only responsible of managing those credentials.

To use this flow, you can follow these steps:

1. Given a client, go to a URL with this format:
```
https://<authn_host>/oauth/authorize?client_id=<client_id>&response_type=code&state=<state_token>&code_challenge=<code_challenge_token>&redirect_uri=<redirect_uri>
```
2. <a id="login-page">A default login page should appear. Put your credentials in it and log in.
![image](https://user-images.githubusercontent.com/14878669/58792371-55d44580-85f4-11e9-8915-03b68bddabe5.png)</a>

- `authn_host`: the authn host for the desired [environment](#environments).
- `response_type`: the type of response of the authorize request. Defines if the flow used is authorization code or implicit. In this case **must** be `code`.
- `state`: optional parameter that preserves some state object set by the client in the Authorization request and makes it available to the client in the response. Commonly used to avoid CSRF attacks. More about that on [this page](https://auth0.com/docs/protocols/oauth2/oauth-state#csrf-attacks).
- `code_challenge` (optional): OAuth2 public clients utilizing the Authorization Code Grant are susceptible to the authorization code interception attack. This string helps mitigating against the threat usually through the use of Proof Key for Code Exchange (PKCE). More about the motivation and code challenge genearation on [this page](https://tools.ietf.org/html/rfc7636).
- `redirect_uri`: if the client is registered with multiple redirect uris you must indicate which one you want to be redirect to. Otherwise the request will fail with code 401.

3. If the credentials are valid, Authn will redirect you to your `redirect_uri` with the autogenerated query param `code` and the `state` if it was previously defined:
```
https://<redirect_uri>?code=TgradaHhSEOIhe2pEAzS9A
```

4. Make a POST request with the code obtained to get an access token:
```shell
curl -X POST https://<authn_host>/oauth/token
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'grant_type=authorization_code&code=TgradaHhSEOIhe2pEAzS9A&client_id=<client_id>&client_secret=<client_secret>&redirect_uri=<redirect_uri>&code_verifier=<code_challenge_token>'
```

- `code_challenge_token` (optional): is the same as the previous parameter used in `code_challenge` and it is used to confirm that the client that generated it is the same as the one requesting the access_token.

If everything worked as expected you should get our usual response:
```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsImtpZCI6IjAwNjEyN2U5LWZiYTgtNGNmNC1iYzlhLTRjNmUzODQ2MWQwMSIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJBdWRpZW5jZSIsImNpZCI6IlR0c2RtZWJQY1F0RW52THNLdzd4IiwiZXhwIjoxNTU5MjI4MjI4LCJncm91cHMiOlsiY3VzdG9tZXIiXSwiaWF0IjoxNTU5MjI0NjI4LCJpc3MiOiJsdW1pZXJlZmlyZWl2YW4uYXV0aC5tYXNtb3ZpbC5jb20iLCJzY29wZXMiOiJhcGk6ZXZlcnl0aGluZyIsInN1YiI6IjYyMjYwNzc1NyIsInRpZCI6IjZlN2IxNzJmLTIyNjUtNDY1Mi1hYTI5LWVmM2EwOGI5YTYwZCJ9.ZgbFsuLXL1cnUYhJFk6IevhSkHsgVDks6b7xFYePjLZQ0Cu2itz61qJVr7bi3uN0YNTtmbaTtnkdOn6KJAjEAOYT0fIsA2MI_84bds0uP6niuDaibfWa-C_mmErxS9VcXe5cTsLwvl11gmvHeq05vszT8JN5vTXRn_MIK_lYGifG0tmFWFlB-_d409jF4KytVXMM5oqvaNAb7sZBK6RefrVTkHFEvx0U0g3F1WvtpBYGAIFksfn45BHPMEyXIXgRpsH0iJ6fwEacwwOTsaLDxmU57CumuCLxRE18KcIIdAKcgKlA1LROB-Y7Vx_YRQBXRmV2RvarGKy__Bm6RcA7qw",
  "expires_in": 3600,
  "refresh_token": "eyJhbGciOiJSUzI1NiIsImtpZCI6IjAwNjEyN2U5LWZiYTgtNGNmNC1iYzlhLTRjNmUzODQ2MWQwMSIsInR5cCI6IkpXVCJ9.eyJjaWQiOiJUdHNkbWViUGNRdEVudkxzS3c3eCIsImV4cCI6MTU1OTMxMTAyOCwiaWF0IjoxNTU5MjI0NjI4LCJ0aWQiOiI2ZTdiMTcyZi0yMjY1LTQ2NTItYWEyOS1lZjNhMDhiOWE2MGQifQ.TPF-w5uwmvpCNB7_U9DHy6hKQUkr604FiKZtl7c1qrQ6mZ1lzate-6xc755DBqgol9mVUTfV3zz1Vgo7DbAsMiJgjL7pMydOzFW7Z9OYCsRodIBIkoX0bVo0x1Hj-51xOo5OplKI5thpwiLj4JaerJU-bFSW6CsY3SkuWwUVYvnsGafxAQlMAigd9wbySMvSb-2zbWdX18nkbByoZ-bV9z_-atW3aPafZLOdwLU4rt1voQV4mCh7MD45-sFD4NeIp922Y5T2GyDV6dVdK77Tv5f16OvuBEaprHaPAeL-vuuAP9IPqj1J7Gt0Jcmt4wfVORIxbJpWpwMa5G8sxD6zww",
  "token_type": "Bearer"
}
```

### Implicit
This authentication flow is a subset of the previous one. It is intended for SPAs and in some cases for mobile apps.
The procedure is almost the same as the described for the authorization code but omitting the last step.

To request a token using this method follow this steps:
1. Given a client, go to a URL with this format (note that in this case the `response_type` is **token** and
`code_challenge` is not present):
```
https://<authn_host>/oauth/authorize?client_id=<client_id>&response_type=token&state=<state_token>&redirect_uri=<redirect_uri>
```

2. Replicate [step 2 for authorization code](#login-page).

3. If everything worked as expected you will be redirected to your `redirect_uri` with a url "hash" containing
the response and looks like this:
```
https://<redirect_uri>//#access_token=eyJhbGciOiJSUzI1NiIsImtpZCI6ImFkNzBlZTJkLTE1NTktNDczZS1hNWExLTRmZDA5Y2EwYzFkNSIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJBdWRpZW5jZSIsImNpZCI6IkZpYVpEdUhodjFzZ0lhM3RqOGZGIiwiZXhwIjoxNTU5NTcwMjA2LCJncm91cHMiOlsiY3VzdG9tZXIiXSwiaWF0IjoxNTU5NTY2NjA2LCJpc3MiOiJsdW1pZXJlZmlyZWl2YW4uYXV0aC5tYXNtb3ZpbC5jb20iLCJzY29wZXMiOiJhcGk6ZXZlcnl0aGluZyIsInN1YiI6IjYyMjYwNzc1NyIsInRpZCI6IjE1Y2E1ZjJmLTUzMjMtNGU3Zi04MGVjLTc4OWZkNzQ5ODE2OCJ9.lLxwgqAaRiyKA5UHJU2-7WGb8-ADYoSu_YYgnlzMKYFUvbZqOgnVtuRKE4utL553r617r7n5zvpgpqL_ahJryEGAJOsODTdkjsGfIdJE7jUluJhthR_gv7JFR9SpJWevlQBmhnu5dz6eCCzfSKz_GRCYxi8IZrp0KyqFTxf8xdEQdDMWI1JrVw550gwAp4i4hE_kivKsP4zKqld7VGqokiBf2STTFSJrL_yjdkhAlHACHo0RFd9YZLmPVu3MruGq8ghItTWCVVfmPe6rTGquyMjO-Syqx7k6GUlLowEy3RW-CYKOm4t0V7BvbPHQgRBEg-aSMRGCSjc6RPH-pgGFOA&expires_in=3600&token_type=Bearer
```

**NOTE: the response is returned after the URL hash to avoid being logged in the browser's history.**

### Service Account (jwt-bearer)

This grant type requires that the client authenticates with [assertion](#assertion-for-oauth). This assertion must be created with the RSA keys provided by Authn when registering this [Service Account](#service-account) 

If the response includes an access token, you can use the access token to call a MasMovil API. (If the response does not include an access token, your JWT and token request might not be properly formed, or the service account might not have permission to access to MasMovil's APIs)

When the access token expires, your application generates another JWT, signs it, and requests another access token.

![Flow Assertion](/pkg/auth/authn/doc/flujoAssertion.png)

You can make a login request like the following one:

```shell
curl --location --request POST 'https://<authn_host>/oauth/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'assertion=eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IjVmYjkyOWE5LWZiMTktNDdjYy04ZWI4LTEwZjZmMzkwNzlhMiJ9.eyJpc3MiOiJ2b2RhZm9uZUBQejdRM0lkQ0xMdDZzS29EdEwxdi5hdXRoLm1hc21vdmlsLmNvbSIsInNjb3BlIjoibXlzaW0uZWRpdG9yLmZ1bGxjb250cm9sIiwiYXVkIjoiaHR0cDovL2xvY2FsaG9zdDo4MDgwL29hdXRoL3Rva2VuIiwiZXhwIjoxNTc4MjM0NTQ4LCJpYXQiOjE1NzgyMzA5NDh9.Ce6moAK0-qXcnMEa_ohcdGgdcjWZXSrXf3IHF02JNbB5ICenxkq7VdNwiSvZikf76tIzrbZUl1HO3262s4Ycp0Hie3yJe0OwME1CDynlJiynzyhwq2ne0R5YlLRW5eXTYwpmwo9sikAK1I0xUqfyMF-F9A15K-cgTGVLWBx3HlWff8wXEFbLeJVXBPTm5NCOKOGvTQDqlP-AtFg6DDVFcpWbAw7S_4VIuePS_Kekh5-eLTwub1rNXMpQ3KWm-DLiL1TKYXrIcyzfV1gYpkzxKig8Z2FhKBtyVODy8z8e8gOs8LP1yJRunFO47wJqkcs1vVd4AAECIfvuFrnu-cPFNA' \
--data-urlencode 'grant_type=urn:ietf:params:oauth:grant-type:jwt-bearer'
```

- `grant_type` parameter defines the OAuth2 flow that is going to be used; in this case `urn:ietf:params:oauth:grant-type:jwt-bearer`.
- `assertion` is the [assertion](#assertion-for-oauth) created through the RSA keys provided by Authn.

If the request is successful, you should get a response like the following:

```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsImtpZCI6ImY3ZWZiY2JkLTM5ZDAtNDhlYS04YzU3LTMyMzk5OTFjNjA2ZSIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJ2b2RhZm9uZUBCTTVpY2hiZ0Q1Q3RUc0R0QXFuUi5hdXRoLm1hc21vdmlsLmNvbSIsImNpZCI6IkJNNWljaGJnRDVDdFRzRHRBcW5SIiwiZXhwIjoxNTc4NDA1MzAzLCJpYXQiOjE1NzgzOTgxMDMsImlzcyI6Imh0dHA6Ly9hcGk6ODA4MC9vYXV0aC90b2tlbiIsIm1vaSI6MSwic2NvcGUiOiJteXNpbS5lZGl0b3IuZnVsbGNvbnRyb2wiLCJzdWIiOiJ2b2RhZm9uZUBCTTVpY2hiZ0Q1Q3RUc0R0QXFuUi5hdXRoLm1hc21vdmlsLmNvbSIsInRpZCI6ImVlZjYyMzRjLTgyMTMtNGNjYi05YmJhLTNiM2RmZmNkMjc5YiJ9.W_AlzK9WQdibK-1ZO4N1_DubxvK-q0R0oLxXSuFhTLSSrdAALFLNkMozCQd-tEBA1JnxmC628j0VCJQ9zw6wxQ70ryN5293YrivNlREmZ4RbjrZMyGlY2vfd30lFWKR3xmlb7p24Sl5-0Fo9OpiWgTaStWVtvLVmadmGwDHx2LpKSqnA3nQgUYczuU50DadqLGRrBD5QvEzzCYlzwSDwtLN5h1bGRTVCIcyxpsnyLg7lW8NM5DFhkKRLr0b-o_01bsmM03aNmXzO3kLajf7L1eczUPi4iUkhRE1ETRdNVqKuOqfupEan405rM-P9LevYjJoOVZ420IAW9l_S78Fu8A",
  "expires_in": 3600,
  "token_type": "Bearer"
}
```

- `access_token` is a signed JWT used by a user to authenticate himself against Istio's service mesh.
- `expires_in` is the time that the access_token will be valid. Once it expires, the access_token won't be valid and the user won't be able to authenticate with it.
- `token_type` defines the type of the access_token that has been generated. This will normally be used in the Authorization header to indicate which kind of authentication has the request.

### JWT Claims

The `access_token` has these claims:
- `sub`: username with the user has done login
- `iss`: Issuer of the application who created and signed this token
- `iat`: Issued at (seconds since Unix epoch)
- `exp`: Expiration time (seconds since Unix epoch)
- `tenant`: Tenant ID to set customer's context. OPTIONAL
- `groups`: Groups to which the user belongs. OPTIONAL
- `roles`: Roles assigned to the users. OPTIONAL
- `provider_internal_id`: Internal customer Id of provider (only qvantel) OPTIONAL
- `app_metadata_roles`: Custom data set of the app. For example in login by uuid, in this section will be the custom roles of the app. OPTIONAL
- `aud`: Audience. Who or What the token is intended for.
- `scope`: NOT USE FOR THE MOMENT 
- `cid`: internal code. No public
- `tid`: internal code. No public
- `family_name`: OPTIONAL. Only with active directory provider
- `given_name`: OPTIONAL. Only with active directory provider
- `name`: OPTIONAL. Only with active directory provider

The `refresh_token` has these claims:
- `sub`: username with the user has done login
- `iat`: Issued at (seconds since Unix epoch)
- `exp`: Expiration time (seconds since Unix epoch)
- `cid`: internal code. No public
- `tid`: internal code. No public

### JWT examples

With these examples you can test them in https://jwt.io/ to see the payload information.

Response customer login for Yoigo or MasMovil
```base64
eyJhbGciOiJSUzI1NiIsImtpZCI6ImQ1ZjcyM2I4LTU2NTYtNGQ5My1hMDAwLTA2MWZhZjFlY2ExZSIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJoZWltZGFsbC5hdXRoLm1hc21vdmlsLmNvbSIsImNpZCI6IjRhekgzb01hQXlBVVFlN0llNkJrIiwiZXhwIjoxNTg2MzU1NTc2LCJncm91cHMiOiJjdXN0b21lciIsImlhdCI6MTU4NjM1MTk3NiwiaXNzIjoiaGVpbWRhbGwuYXV0aC5tYXNtb3ZpbC5jb20iLCJtb2kiOjIsInNjb3BlIjoiYXBpOmV2ZXJ5dGhpbmciLCJzdWIiOiJmdW5ra3lzczFAaG90bWFpbC5jb20iLCJ0ZW5hbnQiOiIyIiwidGlkIjoiOTU1MWU0MzEtODdhZC00MWI2LTg1MDYtMWI5YjhiZTM3ODQwIiwidXNlcl9tZXRhZGF0YSI6eyJncm91cHMiOlsiY3VzdG9tZXIiXX19.OYkt_XoVZw1TyJizkmGWH71y8iwmQx95gHDfUj5vxqCHHcIUZXG4siCtlTZCxUo-Ppxa-SDEwIIf5BEP3zJ7cc-t_ua5AAlPRtEFVRP81-5fBcwT1xKq8-J7Agfg_YXPIX7TnYt5Q7DA0AxWzHiEJ11HCzCWXK2ofShoTSgej80v5eRfGRUpycBUbEgsrnD0doF9YH4QZcrxVFpZ-O7hwH6fp5JmZjH46kUYV0c1TQgMF0WH48tfQWyMGapdylJtus5vZV3WK1AOhtwubGaa1xmWJXn1LdzxvDMh3at_h2XeLq_eTti6IPPlqYZesI97XNtJ1NYAsdzQTeKFwS1Pjg
```

Response agent uuid login for Qvantel agents
```base64
eyJhbGciOiJSUzI1NiIsImtpZCI6ImQ1ZjcyM2I4LTU2NTYtNGQ5My1hMDAwLTA2MWZhZjFlY2ExZSIsInR5cCI6IkpXVCJ9.eyJhcHBfbWV0YWRhdGEiOnsicm9sZXMiOlsiRFVBTFBST0ZJTEUiLCJSRUFET05MWSJdfSwiYXBwX21ldGFkYXRhX3JvbGVzIjoiRFVBTFBST0ZJTEUgUkVBRE9OTFkiLCJhdWQiOiJoZWltZGFsbC5hdXRoLm1hc21vdmlsLmNvbSIsImNpZCI6ImFXVkd3emNBZ3VqNnJTbDExQ1E5IiwiZXhwIjoxNTg2MzU1NTc4LCJncm91cHMiOiJhZ2VudCIsImlhdCI6MTU4NjM1MTk3OCwiaXNzIjoiaGVpbWRhbGwuYXV0aC5tYXNtb3ZpbC5jb20iLCJyb2xlcyI6IlJFVEVOQ0lPTiIsInNjb3BlIjoiYXBpOmV2ZXJ5dGhpbmciLCJzdWIiOiJBRTAwMDEiLCJ0aWQiOiIwZDNhZmYzZS02ODFkLTQzZDktOGFkMC0wMTVlZDdjYzhmMTciLCJ1c2VyX21ldGFkYXRhIjp7Imdyb3VwcyI6WyJhZ2VudCJdLCJyb2xlcyI6WyJSRVRFTkNJT04iXSwic2ZpZCI6IkFFMDAwMSJ9fQ.BLQflnTqbAnClwMrK--Kn0PyZNbAAlaIKGz9qHi80SoyM3i0F_lvFe-ZEVtxYRFjl6WufJowlFwJcjI4Uk4QA9ujs2c3zbxf-oBJVEe-Raxu04ltRNp95J_LvWbx1qJ93FMVDa7tZlIc0vrIR_uRCfzY-Wyh0YjSamAnFHJsYtvXZQ96ExEMhh15S56wJC_rIX0fhlgQ3hIHP07dqm5ReDDK3UMChaEnyyjl-1NvavVblJvxv-uWYFsHhr34VttPY2X0mrA9bZsdnJSJnuVPkfeR5Vj2eYjeAGnE9lw4bMIxJ6DWDMrPdmTOAvFRxqnbGMEWVz7iYJufJfRG2IlyUw
```

## Service Account
A service account is an identity that can be used by an instance or an application to execute requests to the MAS-STACK API without involving a humanoid user.

When a service account is created, Authn will provide a json like this:
```
{
    "private_key_id": "7524f047-83e4-4194-988e-9eb772e51405",
    "private_key": "-----BEGIN RSA PRIVATE KEY-----\nMIIEpAIBAAKCAQEApB8CNN7RyN4vo7O3J9iR+3JUAj0AlHbMPZKXxOgkc6LbvjZX\nFuSUVQL4wppw8iI0ZIkTt42L/NIIA2M/u/6Jewgi7MCn0ClrnS2Wr/evPSJ0lxR/\nQLK6HSTEoKf7Ea7f9pkVrhiRD8lc6igmSUJJKFTPCuO5/iKufd+xaNTMGvRTTIFr\nSKHBMPVgbP2aVjGziD9IZD0iW8zhPekFwUnPYRNrLc62MJfQNG/4m6g3XSEnMlhe\n7okUYV9rLORXMWWDuaD7kmP+hgXbDMV7EyJehJR8DhFNRBgQyaTpsk+QM15m7rwP\ntTOI3miUO2wbHo........ib746MjJrtK05oVi2/Q==\n-----END RSA PRIVATE KEY-----\n",
    "client_email": "thirdparty@gMj7jdyiF8xefBgLJnU1.auth.masmovil.com",
    "client_id": "gMj7jdyiF8xefBgLJnU1",
    "type": "service_account",
    "token_uri": "https://authn.sta.k8s.masmovil.com/oauth/token",
    "auth_uri": "https://authn.sta.k8s.masmovil.com/oauth/authorize",
    "project_id": "addfakQlgpccgrWHTzht"
}
```

That is, an RSA key pair is created, which will be used to sign the JWT (assertion) that must be sent to Authn in the OAuth flow to obtain an access_token.


### Assertion for oauth
To limit access to resources are defined as Oauth scopes that potentially limit access to the resource through the specific API. These scopes could be included in the assertion as a claim that the instance or app creates.

This assertion must be composed in the payload of:
- `iss` The email address (client_email) of the service account.
- `scope` A space-delimited list of the permissions that the application requests. It's optional
- `aud` A descriptor of the intended target of the assertion. When making an access token request this value is: 

    | Enviroment   | URL   |
    |---|---|
    |STA|https://authn.sta.k8s.masmovil.com/oauth/token|
    |PROD|https://authn.k8s.masmovil.com/oauth/token|
- `exp` The expiration time of the assertion, specified as seconds since 00:00:00 UTC, January 1, 1970. This value has a maximum of 1 hour after the issued time.
- `iat` The time the assertion was issued, specified as seconds since 00:00:00 UTC, January 1, 1970..

Service accounts rely on the RSA SHA-256 algorithm and the JWT token format. As a result, the JSON representation of the header is as follows:
```
{
  "alg": "RS256",
  "typ": "JWT",
  "kid": "5fb929a9-fb19-47cc-8eb8-10f6f39079a2"
}
```

In the header the assertion must be composed with:
- `alg` Encryption algorithm. Always RS256
- `typ` Type of token. Always JWT
- `kid` Specify your service account's private key ID. You can find this value in the private_key_id field of your service account JSON file.

The signing algorithm in the JWT header must be used when computing the signature. The only signing algorithm supported by the Authn is RSA using SHA-256 hashing algorithm. This is expressed as RS256 in the alg field in the JWT header.

Sign the UTF-8 representation of the input using SHA256withRSA (also known as RSASSA-PKCS1-V1_5-SIGN with the SHA-256 hash function) with the private key obtained from the Authn. The output will be a byte array.

The signature must then be Base64url encoded. The header, claim set, and signature are concatenated together with a period (.) character. The result is the JWT. It should be the following (line breaks added for clarity):

```
{Base64url encoded header}.
{Base64url encoded claim set}.
{Base64url encoded signature}
````



