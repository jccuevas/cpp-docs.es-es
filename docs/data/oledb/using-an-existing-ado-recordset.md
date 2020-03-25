---
title: Utilizar un conjunto de registros ADO existente
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 48f6eb3bac34b37f495b9492e19b4197ed69cca3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209357"
---
# <a name="using-an-existing-ado-recordset"></a>Utilizar un conjunto de registros ADO existente

Para mezclar OLE DB plantillas de consumidor y objetos de datos activos (ADO), use ADO para abrir un conjunto de registros (correspondiente a un conjunto de filas en las plantillas de consumidor OLE DB). Cuando tenga un conjunto de registros, haga lo siguiente para conectarse a un conjunto de filas de OLE DB:

1. Llame a `QueryInterface` para los punteros de `IRowset` y `IAccessor`.

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk* apunta al objeto `IUnknown` del conjunto de registros ADO.

1. Adjunte el descriptor de acceso y el conjunto de filas a sus clases de plantilla de consumidor OLE DB apropiadas.

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>Consulte también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)
