# Members

## Add or update organization membership

In order to create or update a user's membership with an organization, the authenticated user must be an organization owner.

```
PUT /orgs/:orgname/memberships/:username
```

### Parameters

|Name|Type|Description|
|----|----|-----------|
|role|string|**Required** The role to give the user in the organization. Can be one of: **admin** - The user will become an owner of the organization; **member** - The user will become a non-owner member of the organization.|