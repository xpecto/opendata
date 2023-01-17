# opendata
open definitions and data sources for the investment world

## importing and exporting data to the xpecto server

xpecto has implemented an API to import and export data in the opendata format.

For testing the API xpecto has configured a test-sytem. 
To get the accessdata to the testsystem please contact the xpecto AG under https://www.xpectotalonec.com/unternehmen/kontakt/.

# license

See the license file in the repository when you want to modify the format.

# opendata and login "with"

## motivation

If new customers want to sign up on a platform, it should be possible
to re-use their existing profiles from other platforms. 
Interoperability between platforms will be key in the future.

xpecto suggests to use the OpenID-Connect Standard for that matter. 
The customer should choose which data he wants to share with the new platform. 


## user journey

The user starts the profile sharing with a known process:

- user visits the new platform and wants to sign up
- user clicks on "Login with PLATFORM" Button
- user is forwarded to foreign platform and logs in
- user gives consent to share his data (and selects the bits he wants to share)
- data will be transmitted securely to requesting platform
- customer is automatically registered and does not need to enter or legitimate on new platform

Platforms need to agree on biliteral agreements to allow customers to share their profiles.
Platforms need to exchange keys in order to setup secure data flow.
We suggest to pay 5-15€ per new profile shared between platforms which includes a valid legitimation. 

### control flow

We suggest to use the Authorization code flow described here https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth

### scopes/claims possible profile data on OpenID-Connect 

We suggest to use the following custom-scopes and claims:

- openid (mandatory, needed for openid)
- email (mandatory, see https://openid.net/specs/openid-connect-core-1_0.html#StandardClaims)
- email_verifed (mandatory, see https://openid.net/specs/openid-connect-core-1_0.html#StandardClaims)
- opendata_person (mandatory)
   A opendata_person json property is added to the response of the userinfo-request. The data provided aligns with the person.json Schema defined by the opendata-specification above. The supplied person-data should include all the bits, the customer wanted to share. Minimum would be address & contact info. Legitimation and Bank accounts/Wallets would be perfect for a seamless user experience.


