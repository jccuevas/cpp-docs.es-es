---
title: Hacer referencia a una propiedad en un proveedor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3a034c1f925a5b5d422be234118782b283a3d74c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="referencing-a-property-in-your-provider"></a>Hacer referencia a una propiedad en un proveedor
Busque el grupo de propiedades y el identificador de propiedad para la propiedad que desee. Para obtener más información, consulte [propiedades de OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) en el *referencia del programador de OLE DB*.  
  
 En el siguiente ejemplo se da por supuesto que está intentando obtener una propiedad del conjunto de filas. El código para el uso de la sesión o el comando es similar, pero usa una interfaz diferente.  
  
 Crear un [CDBPropSet](../../data/oledb/cdbpropset-class.md) utilizando el grupo de propiedades como parámetro al constructor del objeto. Por ejemplo:  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
```  
  
 Llame a [AddProperty](../../data/oledb/cdbpropset-addproperty.md), pasándole el identificador de propiedad y un valor que se asignará a la propiedad. El tipo del valor depende de la propiedad que se está utilizando.  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IRowsetChange, true);  

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);  
```  
  
 Use la `IRowset` interfaz para llamar a **GetProperties**. Pasar la propiedad establecida como un parámetro. Este es el código final:  
  
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
  
## <a name="see-also"></a>Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)