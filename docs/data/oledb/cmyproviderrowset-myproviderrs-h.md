---
title: CMyProviderRowset (MyProviderRS.H) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 936c8fe849e2eb92b8eb46170fc3e67842ad6beb
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338855"
---
# <a name="cmyproviderrowset-myproviderrsh"></a>CMyProviderRowset (MyProviderRS.H)
El asistente genera una entrada para el objeto de conjunto de filas. En este caso, se denomina `CMyProviderRowset`. El `CMyProviderRowset` clase hereda de una clase de proveedor OLE DB denominada `CRowsetImpl`, que implementa todas las interfaces necesarias para el objeto de conjunto de filas. El código siguiente muestra la cadena de herencia para `CRowsetImpl`:  
  
```cpp  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T >>  
```  
  
 `CRowsetImpl` También usa el `IAccessor` y `IColumnsInfo` interfaces. Usa estas interfaces para campos de salida en las tablas. La clase también proporciona una implementación para `IRowsetIdentity`, que permite al consumidor determinar si dos filas son idénticas. El `IRowsetInfo` interfaz implementa propiedades para el objeto de conjunto de filas. El `IConvertType` interfaz permite al proveedor resolver las diferencias entre los tipos de datos solicitados por el consumidor y los utilizados por el proveedor.  
  
 El `IRowset` interfaz realmente controla la recuperación de datos. El consumidor llama primero a un método llamado `GetNextRows` para devolver un identificador a una fila, conocida como un `HROW`. El consumidor, a continuación, llama a `IRowset::GetData` con que `HROW` para recuperar los datos solicitados.  
  
 `CRowsetImpl` También toma varios parámetros de plantilla. Estos parámetros permiten determinar cómo el `CRowsetImpl` clase controla los datos. El `ArrayType` argumento le permite determinar el mecanismo de almacenamiento se usa para almacenar los datos de fila. El *RowClass* parámetro especifica la clase que contiene un `HROW`.  
  
 El *RowsetInterface* parámetro le permite también usar el `IRowsetLocate` o `IRowsetScroll` interfaz. El `IRowsetLocate` y `IRowsetScroll` interfaces se heredan de `IRowset`. Por lo tanto, las plantillas de proveedor OLE DB deben proporcionar un tratamiento especial para estas interfaces. Si desea utilizar cualquiera de estas interfaces, deberá usar este parámetro.  
  
## <a name="see-also"></a>Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)