---
title: CCustomRowset (CustomRS.H) | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
- ccustomrowset
- customrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 211c83ec63611c493f03e48b58619caca373ce65
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216362"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

El asistente genera una entrada para el objeto de conjunto de filas. En este caso, se llama `CCustomRowset`. El `CCustomRowset` clase hereda de una clase de proveedor OLE DB denominada `CRowsetImpl`, que implementa todas las interfaces necesarias para el objeto de conjunto de filas. El código siguiente muestra la cadena de herencia para `CRowsetImpl`:

```cpp
template <class T, class Storage, class CreatorClass, 
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, 
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` También usa el `IAccessor` y `IColumnsInfo` interfaces. Usa estas interfaces para campos de salida en las tablas. La clase también proporciona una implementación para `IRowsetIdentity`, que permite al consumidor determinar si dos filas son los mismos. El `IRowsetInfo` interfaz implementa propiedades para el objeto de conjunto de filas. El `IConvertType` interfaz permite al proveedor resolver las diferencias entre los tipos de datos solicitados por el consumidor y los utilizados por el proveedor.

El `IRowset` interfaz realmente controla la recuperación de datos. El consumidor llama primero a un método llamado `GetNextRows` para devolver un identificador a una fila, conocida como un `HROW`. El consumidor, a continuación, llama a `IRowset::GetData` con que `HROW` para recuperar los datos solicitados.

`CRowsetImpl` También toma varios parámetros de plantilla. Estos parámetros permiten determinar cómo el `CRowsetImpl` clase controla los datos. El `ArrayType` argumento le permite determinar el mecanismo de almacenamiento se usa para almacenar los datos de fila. El *RowClass* parámetro especifica la clase que contiene un `HROW`.

El *RowsetInterface* parámetro le permite también usar el `IRowsetLocate` o `IRowsetScroll` interfaz. El `IRowsetLocate` y `IRowsetScroll` interfaces se heredan de `IRowset`. Por lo tanto, las plantillas de proveedor OLE DB deben proporcionar un tratamiento especial para estas interfaces. Si desea utilizar cualquiera de estas interfaces, deberá usar este parámetro.

## <a name="see-also"></a>Vea también

[Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)<br/>
