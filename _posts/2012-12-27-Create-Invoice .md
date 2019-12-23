---
category: Stuff
path: '/stuff'
title: 'Create Invoice'
type: 'GET'

layout: nil
---

### Create Invoice Request
[Xero Invoice  fields](https://developer.xero.com/documentation/api/invoices)
	````
	try{
		BreadwinnerAPI.RequestObject req = new  BreadwinnerAPI.RequestObject();	
		Invoice xi = new Invoice ();
		xi.invoiceType='Invoice'; 
		xi.InvoiceNumber = 'inv-123';
		xi.DueDate = string.valueof(system.today());
		Invoice.LineItemWrapper li = new Invoice.LineItemWrapper();
		li.ItemCode = ''; li.Description ='li desc'; li.AccountCode='200';li.UnitAmount=300;li.Quantity=3;
		list<Invoice.LineItemWrapper> lineitems = new list<Invoice.LineItemWrapper>();
		lineitems.add(li);
		xi.LineItems = lineitems;
		xi.ClientId = '39efa556-8dda-4c81-83d3-a631e59eb6d3';
		req.xeroInvoice= xi;
		BreadwinnerAPI.ResponseObject res =  BreadwinnerAPI.call('createInvoice', req);
		if(res.errors.size()>0){
			for(BreadwinnerAPI.Error er :res.errors){
				System.debug(er); 
			}
		}
		system.debug('created Invoice/////////' +res);
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

