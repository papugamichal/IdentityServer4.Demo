# IdentityServer4.Demo
Demo instance of IdentityServer4 preconfigred to be OAuth2.0 token provider for RabbitMq Management UI and Rabbit clients like MassTransit.  

Setup requirements: 
- Visual Studio 2019
- .NET Core 3.0 SDK
- Postman (optional, for manual tests)

---
There are two preconfigures users bob/bob & alice/alice.
Bob
 - Roles: Admin (dummy), RabbitManagement_Administrator
 
Alice 
  - Roles: RabbitManagement_Policymaker

---
For manual test purposes we can use Postman to fetch access token (JWT).
1. Management UI client was configure Client with Implicit grant type.
  - Open blank request tab
  - Open Auth tab and select Type: OAuth 2.0
  - Select Get New Access Token and fill reqire fields - do not forget to select Grant Type - Implicit
	-	Example working configuration with RabbitMq:
		![RabbitImplicit](https://user-images.githubusercontent.com/57910336/69492333-da1bcd00-0ea1-11ea-8750-d42151ed38a0.PNG)
 
 	-	Select Request Token, you will be redirect to IdentityServer login page. Login here with bob or alice credenctials.
	
		![RabbitImplicitLogin](https://user-images.githubusercontent.com/57910336/69492334-da1bcd00-0ea1-11ea-9149-20bc5651292a.PNG)
	
	- Confirm requested Scopes:
	
		![RabbitImplicitScopes](https://user-images.githubusercontent.com/57910336/69492335-dab46380-0ea1-11ea-98c4-ffceb4995abd.PNG)

	- Generated Token is copy in Postman window
	
		![RabbitImplicitToken](https://user-images.githubusercontent.com/57910336/69492332-da1bcd00-0ea1-11ea-8f33-c80c5d4fb74a.PNG)

 	
2. Rabbit Clients configured in code ex. C# uses IdentityServer client configured with ClientCredenctials GrantType. In Postman we can simulate this token request by HTTP POST request to IdentityServer /connect/token endpoint.
  - Open blank request tab
  - Open Body tab and select from-data option:
 	-	Example working configuration
		![RabbitClientCredenctials](https://user-images.githubusercontent.com/57910336/69492705-1f41fe00-0ea6-11ea-9c54-56d8db255ddd.PNG)
	
	- Generated Token is copy in Postman window
		![RabbitClientCredenctials_2](https://user-images.githubusercontent.com/57910336/69492706-1f41fe00-0ea6-11ea-8e6f-ffcdb7e25166.PNG)
	
	- That generated token can be passed as password 
	
	
