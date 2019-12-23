---
category: Stuff
path: '/stuff'
title: 'Create Xero Contact'
type: 'GET'

layout: nil
---


### Create Customer Request
[Xero Customer fields](https://developer.xero.com/documentation/api/contacts#POST)

	````
	try{
		BreadwinnerAPI.RequestObject req = new  BreadwinnerAPI.RequestObject();	
		AccountWrapper str = new AccountWrapper();
		str.name='MY5 NAME Test Create -';             
		req.xeroCustomer = str;

		BreadwinnerAPI.ResponseObject res =  BreadwinnerAPI.call('createCustomer', req);
		if(res.errors.size()>0){
			for(BreadwinnerAPI.Error er :res.errors){
				System.debug(er); 
			}
		}
		system.debug('created customer/////////' +res);
	}catch(Exception ex){
		System.debug('Exception occurred while creating customers in Xero.'+ex.getStackTraceString());
	}
```

### Response

Sends back a collection of things.

```Status: 200 OK```
```{
    {
        id: thing_1,
        name: 'My first thing'
    }
}```

