# Easy token

A Solid Community Server recipe with the easy-token registration page.

Status: Currently a working POC, but some improvement remains, including a decent amount of code cleaning ( see TODO below ).

## Description

Easy-token is a CSS component that improve registration flow when creating a Pod with an existing WebID.

Easy-token allows verifying WebIDs ownership by simply clicking a button instead of manually adding a verification token.

## Problem

When creating a new Pod with an existing WebID, CSS would ask the user to prove that their own the given WebID by adding a verification token to their WebID document ( see screenshot below). To do so, the user would do the following steps:
 1. Open a pod browser (such as Penny) in a new window
 1. Log in to the pod browser
 1. Browse to the WebID document
 1. Copy past the verification token triple and add it to the WebID document ( this operation can be complicated for newcomers)

## Solution

The proposed solution is to automate the former steps with a simple button. The steps to verify the WebID are the following:
 1. click the "Proove that I own this webId" button
 1. login to your IDP
The script will do the rest.

## Screenshot
| without easy-token | with easy-token | 
|---|---|
| ![image](https://user-images.githubusercontent.com/60817856/157554175-0916dbf0-ae4d-481a-9b49-9d4d0067de0a.png) | ![image](https://user-images.githubusercontent.com/60817856/157554525-be9421ae-31e8-48ac-9cc8-48347d38f539.png)
| 

 
## Install

```
git clone https://github.com/joeitu/easy-token.git
cd easy-token
npm ci
npm run start -- -c ./config/default-easy-token.json
```


## Usage

Assuming that you already have a WebID, you can now go to the registration page `/idp/register/` and choose the option to *Use my existing WebID to access my Pod*

Enter your WebID host and click the *Verify my WebID* button. You should be redirected to your IDP provider, log in with your credential, and done! Now you can finish the registration form as usual.

## TODO's
 - [ ] Clean and refactore code
    - [ ] Simplify config import
 - [ ] Add a function that check that the verification toekn is correclty added to the WebID document
    - [ ] Display an error or validation message
 - [ ] Don't fail quietly, display error message to the user 
 - [ ] remove oidcIssuerRegistrationToken after registration
 - [ ] add oidcIssuer to the webId document after registration?
 - [ ] Make a NPM package
