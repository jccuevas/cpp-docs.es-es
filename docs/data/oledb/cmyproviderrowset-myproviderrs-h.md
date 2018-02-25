---
title: CMyProviderRowset (MyProviderRS.H) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6a4a786a5980763a0588456004efafc02978365e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cmyproviderrowset-myproviderrsh"></a>CMyProviderRowset (MyProviderRS.H)
El asistente genera una entrada para el objeto de conjunto de filas. En este caso, se denomina `CMyProviderRowset`. El `CMyProviderRowset` clase hereda de una clase de proveedor OLE DB denominada `CRowsetImpl`, que implementa todas las interfaces necesarias para el objeto de conjunto de filas. El código siguiente muestra la cadena de herencia para `CRowsetImpl`:  
  
```  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T >>  
```  
  
 `CRowsetImpl` También usa el `IAccessor` y `IColumnsInfo` interfaces. Usa estas interfaces para los campos de salida en las tablas. La clase también proporciona una implementación para **IRowsetIdentity**, lo que permite al consumidor determinar si dos filas son idénticas. El `IRowsetInfo` interfaz implementa las propiedades para el objeto de conjunto de filas. El **IConvertType** interfaz permite al proveedor resolver las diferencias entre los tipos de datos requeridos por el consumidor y los utilizados por el proveedor.  
  
 El `IRowset` interfaz controla en realidad la recuperación de datos. El consumidor llama primero a un método denominado `GetNextRows` para devolver un identificador a una fila, conocido como un **HROW**. El consumidor llama a continuación, **IRowset:: GetData** con que **HROW** para recuperar los datos solicitados.  
  
 `CRowsetImpl` También toma varios parámetros de plantilla. Estos parámetros permiten determinar cómo `CRowsetImpl` clase administra los datos. El `ArrayType` argumento le permite determinar el mecanismo de almacenamiento se utiliza para almacenar los datos de fila. El **RowClass** parámetro especifica la clase que contiene un **HROW**.  
  
 El **RowsetInterface** parámetro le permite usar la `IRowsetLocate` o `IRowsetScroll` interfaz. El `IRowsetLocate` y `IRowsetScroll` interfaces se heredan de `IRowset`. Por lo tanto, las plantillas de proveedor OLE DB deben proporcionar un tratamiento especial para estas interfaces. Si desea utilizar cualquiera de estas interfaces, debe utilizar este parámetro.  
  
## <a name="see-also"></a>Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)