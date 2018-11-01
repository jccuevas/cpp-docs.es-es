---
title: Hacer referencia a una propiedad en un proveedor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e88dcc168df6b6b315f73e2eb595f55668fd2493
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074870"
---
# <a name="referencing-a-property-in-your-provider"></a>Hacer referencia a una propiedad en un proveedor

Busque el grupo de propiedades y el identificador de propiedad para la propiedad que desee. Para obtener más información, consulte [propiedades de OLE DB](/previous-versions/windows/desktop/ms722734) en el *referencia del programador de OLE DB*.

En el siguiente ejemplo se da por supuesto que está intentando obtener una propiedad del conjunto de filas. El código para el uso de la sesión o el comando es similar, pero usa una interfaz diferente.

Crear un [CDBPropSet](../../data/oledb/cdbpropset-class.md) utilizando el grupo de propiedades como parámetro al constructor de objeto. Por ejemplo:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

Llame a [AddProperty](../../data/oledb/cdbpropset-addproperty.md), pasándole el identificador de propiedad y un valor que se asignará a la propiedad. El tipo del valor depende de la propiedad que se usa.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

Use la `IRowset` interfaz para llamar a `GetProperties`. Pase la propiedad establecida como un parámetro. Este es el código final:

```cpp
CAgentRowset<CCustomCommand>* pRowset = (CAgentRowset<CCustomCommand>*) pThis;

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