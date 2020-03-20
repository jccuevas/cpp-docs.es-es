---
title: CCustomRowset (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyproviderrowset
- ccustomrowset
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
ms.openlocfilehash: 2c84ff359bdbb39f281928fa0135edd40b1f7d20
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545808"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

El asistente genera una entrada para el objeto de conjunto de filas. En este caso, se denomina `CCustomRowset`. La clase `CCustomRowset` hereda de una clase de proveedor de OLE DB denominada `CRowsetImpl`, que implementa todas las interfaces necesarias para el objeto de conjunto de filas. En el código siguiente se muestra la cadena de herencia para `CRowsetImpl`:

```cpp
template <class T, class Storage, class CreatorClass, 
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, 
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` también utiliza las interfaces `IAccessor` y `IColumnsInfo`. Usa estas interfaces para los campos de salida de las tablas. La clase también proporciona una implementación de `IRowsetIdentity`, que permite al consumidor determinar si dos filas son iguales. La interfaz de `IRowsetInfo` implementa propiedades para el objeto de conjunto de filas. La interfaz de `IConvertType` permite al proveedor resolver las diferencias entre los tipos de datos solicitados por el consumidor y los utilizados por el proveedor.

La interfaz de `IRowset` controla realmente la recuperación de datos. En primer lugar, el consumidor llama a un método llamado `GetNextRows` para devolver un identificador a una fila, lo que se conoce como `HROW`. A continuación, el consumidor llama a `IRowset::GetData` con ese `HROW` para recuperar los datos solicitados.

`CRowsetImpl` también toma varios parámetros de plantilla. Estos parámetros permiten determinar el modo en que la clase `CRowsetImpl` controla los datos. El argumento `ArrayType` permite determinar qué mecanismo de almacenamiento se utiliza para almacenar los datos de fila. El parámetro *RowClass* especifica qué clase contiene una `HROW`.

El parámetro *RowsetInterface* permite usar también la interfaz `IRowsetLocate` o `IRowsetScroll`. Las interfaces `IRowsetLocate` y `IRowsetScroll` heredan de `IRowset`. Por lo tanto, las plantillas de proveedor de OLE DB deben proporcionar un control especial para estas interfaces. Si desea utilizar cualquiera de estas interfaces, debe usar este parámetro.

## <a name="see-also"></a>Consulte también

[Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)<br/>
