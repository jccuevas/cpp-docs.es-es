---
title: Hacer referencia a una propiedad en un proveedor
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: d70a1901c457d9fbdbe8712d84999e256a54d0c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209798"
---
# <a name="referencing-a-property-in-your-provider"></a>Hacer referencia a una propiedad en un proveedor

Busque el grupo de propiedades y el identificador de propiedad de la propiedad que desee. Para obtener más información, vea [OLE DB Properties](/previous-versions/windows/desktop/ms722734(v=vs.85)) en la **Referencia del programador de OLE DB**.

En el ejemplo siguiente se da por supuesto que está intentando obtener una propiedad del conjunto de filas. El código para usar la sesión o el comando es similar, pero usa una interfaz diferente.

Cree un objeto [CDBPropSet](../../data/oledb/cdbpropset-class.md) mediante el grupo de propiedades como parámetro para el constructor. Por ejemplo:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

Llame a [AddProperty](../../data/oledb/cdbpropset-addproperty.md), pasándole el identificador de propiedad y un valor que se va a asignar a la propiedad. El tipo del valor depende de la propiedad que esté usando.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

Use la interfaz `IRowset` para llamar a `GetProperties`. Pase el conjunto de propiedades como parámetro. Este es el código final:

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

## <a name="see-also"></a>Consulte también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
