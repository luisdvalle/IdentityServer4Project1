# IdentityServer4Project1

The code on this solution is based on the Quickstarts available at http://docs.identityserver.io

Quickstarts included here are:

<ul>
  <li>Setup and overview</li>
  <li>Protecting an API using Client Credentials</li>
</ul>

The structure of this solution is the following

Auth Service - Web API - Client 

<img src="https://github.com/luisdvalle/IdentityServer4Project1/blob/master/IDServer4-overview.png" />

## Components structure

### Auth Service

* Provides the authentication/authorisation service
* Defines resources (e.g. APIs) and clients
* Nuget packages: 
	** IdentityServer4
* Implementation:
	** Add Middleware to the pipeline - app.UseIdentityServer()
	** Register DI - services.AddIdentityService()
	** Configure scopes and clients -> ApiResource and Client objects

### Web API

* Provides a service (resource)
* Nuget packages: 
	** IdentityServer4.AccessTokenValidation
* Implementation:
	** Controller with Authorize attribute
	** Add Midleware to pipeline - app.UseAuthentication()
	** Register DI - services.AddAuthentication().AddIdentityServerAuthentication()

### Client

* Accesses Web API
* Nuget packages: 
	** IdentityModel
* Implementation:
	** Discover Auth Service Enpoints
	** Request Token to Auth Service
	** Send request to Web API with that (Access) Token