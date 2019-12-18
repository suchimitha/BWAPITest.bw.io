---
category: Stuff
path: '/stuff'
title: 'Update Xero Contact'
type: 'GET'

layout: nil
---

### Update Customer Request
[Xero Customer fields](https://developer.xero.com/documentation/api/contacts#POST)
	````
	try{
		BreadwinnerAPI.RequestObject req = new  BreadwinnerAPI.RequestObject();	
		AccountWrapper str = new AccountWrapper();
		str.name='MY5 NAME Test Create -'; 
		str.contactId ='tempId';		
		req.xeroCustomer = str;

		BreadwinnerAPI.ResponseObject res =  BreadwinnerAPI.call('updateCustomer', req);
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

