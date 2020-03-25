---
title: Superar las pruebas de conformidad de OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: eda4dccda147ddd4776bb56e649f539a7550abd1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209802"
---
# <a name="passing-ole-db-conformance-tests"></a>Superar las pruebas de conformidad de OLE DB

Para que los proveedores sean más coherentes, el SDK de acceso a datos proporciona un conjunto de pruebas de conformidad OLE DB. Las pruebas comprueban todos los aspectos de su proveedor y proporcionan una garantía razonable de que el proveedor funciona según lo previsto. Puede encontrar las pruebas de conformidad de OLE DB en el SDK de Microsoft Data Access. Esta sección se centra en lo que debe hacer para pasar las pruebas de conformidad. Para obtener información sobre cómo ejecutar las pruebas de conformidad de OLE DB, vea el SDK de.

## <a name="running-the-conformance-tests"></a>Ejecutar las pruebas de conformidad

En Visual C++ 6,0, las plantillas de proveedor de OLE DB agregaron varias funciones de enlace para que pueda comprobar los valores y las propiedades. La mayoría de estas funciones se agregaron en respuesta a las pruebas de conformidad.

> [!NOTE]
> Debe agregar varias funciones de validación para que el proveedor pase las pruebas de conformidad OLE DB.

Este proveedor requiere dos rutinas de validación. La primera rutina, `CRowsetImpl::ValidateCommandID`, forma parte de la clase de conjunto de filas. Se llama durante la creación del conjunto de filas por parte de las plantillas de proveedor. En el ejemplo se utiliza esta rutina para indicar a los consumidores que no admiten índices. La primera llamada es `CRowsetImpl::ValidateCommandID` (tenga en cuenta que el proveedor usa el `_RowsetBaseClass` typedef agregado en el mapa de interfaz para `CCustomRowset` en la [compatibilidad del proveedor](../../data/oledb/provider-support-for-bookmarks.md)con los marcadores, por lo que no tiene que escribir esa línea larga de argumentos de plantilla). A continuación, devuelva DB_E_NOINDEX si el parámetro de índice no es NULL (esto indica que el consumidor quiere usar un índice en EE. UU.). Para obtener más información acerca de los identificadores de comando, consulte la especificación de OLE DB y busque `IOpenRowset::OpenRowset`.

El código siguiente es la rutina de validación `ValidateCommandID`:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H
// Class: CCustomRowset

HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)
{
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);
   if (hr != S_OK)
      return hr;

   if (pIndexID != NULL)
      return DB_E_NOINDEX;    // Doesn't support indexes

   return S_OK;
}
```

Las plantillas de proveedor llaman al método `OnPropertyChanged` cada vez que alguien cambia una propiedad en el grupo de DBPROPSET_ROWSET. Si desea controlar las propiedades de otros grupos, agréguelos al objeto adecuado (es decir, DBPROPSET_SESSION comprobaciones van en la clase `CCustomSession`).

El código comprueba primero para ver si la propiedad está vinculada a otra. Si la propiedad se está encadenando, establece la propiedad DBPROP_BOOKMARKS en `True`. El Apéndice C de la especificación de OLE DB contiene información sobre las propiedades. Esta información también indica si la propiedad está encadenada a otra.

Es posible que también desee agregar la rutina `IsValidValue` al código. Las plantillas llaman a `IsValidValue` cuando se intenta establecer una propiedad. Invalide este método si necesita un procesamiento adicional al establecer un valor de propiedad. Puede tener uno de estos métodos para cada conjunto de propiedades.

## <a name="see-also"></a>Consulte también

[Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)
