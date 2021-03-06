---
title: "Handling errors in the TOM API (AMO-TOM) | Microsoft Docs"
description: Learn how to use exceptions to report error conditions to the user in Analysis Services Management Objects (AMO) Tabular Object Model (TOM).
ms.date: 07/20/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan

---
# Handling errors in the TOM API (AMO-TOM)

[!INCLUDE[ssas-appliesto-sql2016-later-aas-pbip](../includes/ssas-appliesto-sql2016-later-aas-pbip.md)]

A common practice for managed libraries like Analysis Services Management Objects (AMO) Tabular Object Model (TOM) is to use exceptions as a mechanism for reporting error conditions to the user.  

When an error is detected in AMO-TOM, besides throwing few standard .NET exceptions like **ArgumentException** and **InvalidOperationException**, TOM also can throw several TOM-specific exceptions.  

TOM exceptions are derived from [AmoException Class](https://msdn.microsoft.com/library/microsoft.analysisservices.amoexception.aspx), covering both AMO- and TOM-specific exceptions. 

To illustrate exception handling in TOM, let's review one of the more common exceptions, which is [OperationException Class](https://msdn.microsoft.com/library/microsoft.analysisservices.operationexception.aspx).

**OperationException** is thrown when a user initiates an operation on the Analysis Services server and the server fails to perform an operation, either because the action was illegal, or because of another internal or external error. 

When thrown,** OperationException** object will contain a list of XMLA errors returned by the server. 

Note that the server will not accept changes that are invalid. If this occurs, revert the **Model** tree back into the last known good state using the [UndoLocalChanges Method](https://msdn.microsoft.com/library/microsoft.analysisservices.tabular.model.undolocalchanges.aspx), correct the model, then resubmit. 

## Code Example: handle exceptions 
 
```csharp
 try 
 { 
  // Change the Model, for example create a table. 
  // … 
   model.saveChanges(); 
 } 
  catch(operationException ex) 
 { 
  foreach(XmlaError err in ex.Results.OfType<XmlaError>().cast<XmlaError>()) 
  { 
   Console.WriteLine("Error returned from the server:" + err.Messsage ); 
  } 
 } 
```

## Next steps

Other relevant exceptions include the following:

- [TomInternalException Class](https://msdn.microsoft.com/library/microsoft.analysisservices.tabular.tominternalexception.aspx)
- [TomValidationException Class](https://msdn.microsoft.com/library/microsoft.analysisservices.tabular.tomvalidationexception.aspx)
- [JsonSerializationException class](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_JsonSerializationException.htm)
