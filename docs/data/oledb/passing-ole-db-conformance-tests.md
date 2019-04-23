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
ms.openlocfilehash: 9f78b16bc30651560137a39286460a8e5ceccd40
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037002"
---
# <a name="passing-ole-db-conformance-tests"></a>Superar las pruebas de conformidad de OLE DB

Para que los proveedores más coherente, el SDK de Data Access proporciona un conjunto de pruebas de conformidad de OLE DB. Las pruebas comprueban todos los aspectos de su proveedor de y proporcionan seguridad razonable de que el proveedor funciona como se esperaba. Puede encontrar las pruebas de conformidad de OLE DB en el SDK de Microsoft Data Access. En esta sección se centra en lo que debe hacer para pasar las pruebas de conformidad. Para obtener información acerca de cómo ejecutar las pruebas de conformidad de OLE DB, consulte el SDK.

## <a name="running-the-conformance-tests"></a>Ejecuta las pruebas de conformidad

En Visual C++ 6.0, las plantillas de proveedor OLE DB agregan un número de funciones de enlace para que pueda comprobar los valores y propiedades. La mayoría de estas funciones se agregaron en respuesta a las pruebas de conformidad.

> [!NOTE]
> Deberá agregar varias funciones de validación de su proveedor para pasar las pruebas de conformidad de OLE DB.

Este proveedor requiere dos rutinas de validación. La primera rutina, `CRowsetImpl::ValidateCommandID`, forma parte de la clase de conjunto de filas. Se llama durante la creación del conjunto de filas mediante las plantillas de proveedor. El ejemplo utiliza esta rutina para indicar a los consumidores que no es compatible con los índices. Es la primera llamada `CRowsetImpl::ValidateCommandID` (tenga en cuenta que el proveedor utiliza la `_RowsetBaseClass` typedef agregada en el mapa de interfaz para `CCustomRowset` en [proveedor de compatibilidad con los marcadores](../../data/oledb/provider-support-for-bookmarks.md), por lo que no tiene que escribir esa larga línea de plantilla argumentos). A continuación, devolver DB_E_NOINDEX si el parámetro de índice no es NULL (indica que el consumidor desea utilizar un índice en). Para obtener más información acerca de los identificadores de comando, vea la especificación de OLE DB y busque `IOpenRowset::OpenRowset`.

El código siguiente es el `ValidateCommandID` rutina de validación:

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

La llamada de plantillas de proveedor la `OnPropertyChanged` método cada vez que alguien cambie una propiedad del grupo DBPROPSET_ROWSET. Si desea controlar las propiedades de otros grupos, agrega al objeto adecuado (es decir, las comprobaciones de DBPROPSET_SESSION ir en la `CCustomSession` clase).

El código comprueba primero si la propiedad está vinculada a otra. Si la propiedad se está encadenando, Establece la propiedad DBPROP_BOOKMARKS en `True`. Apéndice C de la especificación de OLE DB contiene información acerca de las propiedades. Esta información también indica si la propiedad está encadenada a otra.

También puede agregar el `IsValidValue` rutinarias en el código. La llamada plantillas `IsValidValue` al intentar establecer una propiedad. Debe reemplazar este método si necesita un procesamiento adicional cuando se establece un valor de propiedad. Puede tener uno de estos métodos para cada conjunto de propiedades.

## <a name="see-also"></a>Vea también

[Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)