---
title: "Hacer referencia a una propiedad en un proveedor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "proveedores OLE DB, propiedades"
  - "referencias, a propiedades de proveedores"
  - "referencias a propiedades de proveedores"
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Hacer referencia a una propiedad en un proveedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Busque el grupo de propiedades y el identificador de propiedad para la propiedad que desee.  Para obtener más información, vea [Propiedades de OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) en la *Referencia del programador de OLE DB*.  
  
 En el siguiente ejemplo se supone que intenta obtener el valor de una propiedad del conjunto de filas.  El código necesario para utilizar la sesión o el comando es similar, pero utiliza una interfaz diferente.  
  
 Cree un objeto [CDBPropSet](../../data/oledb/cdbpropset-class.md) con el grupo de propiedades como parámetro para el constructor.  Por ejemplo:  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
```  
  
 Llame a [AddProperty](../../data/oledb/cdbpropset-addproperty.md) pasándole el identificador de propiedad y un valor que se debe asignar a la propiedad.  El tipo del valor depende de la propiedad que vaya a utilizar.  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
propset.AddProperty(DBPROP_IRowsetChange, true);  
propset.AddProperty(DBPROP_UPDATABILITY,  
DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);  
```  
  
 Utilice la interfaz `IRowset` para llamar a **GetProperties**.  Pase el conjunto de propiedades como un parámetro.  A continuación se muestra el código final:  
  
```  
CAgentRowset<CMyProviderCommand>* pRowset = (CAgentRowset<CMyProviderCommand>*) pThis;  
  
CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;  
  
DBPROPIDSET set;  
set.AddPropertyID(DBPROP_BOOKMARKS);  
DBPROPSET* pPropSet = NULL;  
ULONG ulPropSet = 0;  
HRESULT hr;  
  
if (spRowsetProps)  
   hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);  
  
if (pPropSet)  
{  
   CComVariant var = pPropSet->rgProperties[0].vValue;  
   CoTaskMemFree(pPropSet->rgProperties);  
   CoTaskMemFree(pPropSet);  
  
   if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))  
   {  
      ...  // Use property here  
   }  
}  
```  
  
## Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)