---
title: CMyProviderSession (MyProviderSess.H) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidersession
- myprovidersess.h
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2d74c79535a97e8864ad55d3b0cfb35f98bb5ba4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106101"
---
# <a name="cmyprovidersession-myprovidersessh"></a>CMyProviderSession (MyProviderSess.H)

MyProviderSess.H contiene la declaración e implementación para el objeto de sesión de OLE DB. El objeto de origen de datos crea el objeto de sesión y representa una conversación entre un consumidor y proveedor. Varias sesiones simultáneas pueden estar abiertas para un origen de datos. La lista de herencia para `CMyProviderSession` sigue:  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSession  
class ATL_NO_VTABLE CMyProviderSession :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IGetDataSourceImpl<CMyProviderSession>,  
   public IOpenRowsetImpl<CMyProviderSession>,  
   public ISessionPropertiesImpl<CMyProviderSession>,  
   public IObjectWithSiteSessionImpl<CMyProviderSession>,  
   public IDBSchemaRowsetImpl<CMyProviderSession>,  
   public IDBCreateCommandImpl<CMyProviderSession, CMyProviderCommand>  
```  
  
El objeto de sesión se hereda de `IGetDataSource`, `IOpenRowset`, `ISessionProperties`, y `IDBCreateCommand`. El `IGetDataSource` interfaz permite a una sesión recuperar el origen de datos que lo creó. Esto es útil si tiene que obtener las propiedades del origen de datos que ha creado u otra información que puede proporcionar el origen de datos. El `ISessionProperties` interfaz controla todas las propiedades de la sesión. El `IOpenRowset` y `IDBCreateCommand` interfaces se usan para realizar el trabajo de base de datos. Si el proveedor admite comandos, implementa el `IDBCreateCommand` interfaz. Sirve para crear el objeto de comando que se puede ejecutar comandos. El proveedor siempre implementa la `IOpenRowset` objeto. Sirve para generar un conjunto de filas simple de un proveedor. Es un conjunto de filas predeterminado (por ejemplo, `"select * from mytable"`) de un proveedor.  
  
El asistente también genera tres clases de sesión: `CMyProviderSessionColSchema`, `CMyProviderSessionPTSchema`, y `CMyProviderSessionTRSchema`. Estas sesiones se utilizan para conjuntos de filas de esquema. Conjuntos de filas de esquema que el proveedor pueda devolver los metadatos al consumidor sin que el consumidor de tener que ejecutar una consulta o la captura de datos. La búsqueda de metadatos puede ser mucho más rápida que el de detectar las capacidades de un proveedor.  
  
La especificación OLE DB requiere que los proveedores que implementan el `IDBSchemaRowset` tipos de conjunto de filas de esquema de compatibilidad con tres interfaz: DBSCHEMA_COLUMNS, DBSCHEMA_PROVIDER_TYPES y DBSCHEMA_TABLES. El asistente genera las implementaciones para cada conjunto de filas de esquema. Cada clase generada por el Asistente contiene un `Execute` método. En este `Execute` método, puede devolver datos al proveedor sobre qué tablas, columnas y tipos de datos que admite. Estos datos normalmente se conocen en tiempo de compilación.  
  
## <a name="see-also"></a>Vea también  

[Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)