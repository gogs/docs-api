# Branches

## List Branches

```
GET /repos/:owner/:repo/branches
```

### Response

```
Status: 200 OK
```
```json
[
   {
      "name":"master",
      "commit":{
         "id":"c1c220c4dd6df895965a02b8be575c5e2f78dfd1",
         "message":"A commit message. \n",
         "url":"Not implemented",
         "author":{
            "name":"Author Name",
            "email":"author@email.com",
            "username":""
         }
      }
   },
   {
      "name":"second-branch",
      "commit":{
         "id":"0a0fdf63c23af6a2836c426c5284136015ec2996",
         "message":"A second commit message.\n",
         "url":"Not implemented",
         "author":{
            "name":"Author Name",
            "email":"author@email.com",
            "username":""
         }
      }
   }
]
```

## Get Branch

```
GET /repos/:owner/:repo/branches/:branch
```

### Response

```
Status: 200 OK
```
```json
{
   "name":":branchname",
   "commit":{
      "id":"0a0fdf63c23af6a2836c426c5284136015ec2996",
      "message":"A second commit message.\n",
      "url":"Not implemented",
      "author":{
         "name":"Author Name",
         "email":"author@email.com",
         "username":""
      }
   }
}
```