---
title: CMyProviderSession (MyProviderSess.H) | Documentos de Microsoft
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
ms.openlocfilehash: 5f5243edcbc6ad7781eb13caf6ec72021fd83506
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmyprovidersession-myprovidersessh"></a>CMyProviderSession (MyProviderSess.H)
MyProviderSess.H contiene la declaración y la implementación para el objeto de sesión de OLE DB. El objeto de origen de datos crea el objeto de sesión y representa una conversación entre un consumidor y proveedor. Varias sesiones simultáneas pueden estar abiertas para un origen de datos. La lista de herencia de `CMyProviderSession` sigue:  
  
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
  
 El objeto de sesión hereda de **IGetDataSource**, `IOpenRowset`, **ISessionProperties**, y **IDBCreateCommand**. El **IGetDataSource** interfaz permite a una sesión recuperar el origen de datos que lo creó. Esto es útil si necesita obtener propiedades del origen de datos que creó u otra información que puede proporcionar el origen de datos. El **ISessionProperties** interfaz controla todas las propiedades de la sesión. El `IOpenRowset` y **IDBCreateCommand** interfaces se utilizan para realizar el trabajo de base de datos. Si el proveedor admite comandos, implementa la **IDBCreateCommand** interfaz. Se utiliza para crear el objeto de comando que se puede ejecutar comandos. El proveedor siempre implementa la `IOpenRowset` objeto. Se utiliza para generar un conjunto de filas simple de un proveedor. Es un conjunto de filas predeterminado (por ejemplo, `"select * from mytable"`) de un proveedor.  
  
 El asistente también genera tres clases de sesión: `CMyProviderSessionColSchema`, `CMyProviderSessionPTSchema`, y `CMyProviderSessionTRSchema`. Estas sesiones se utilizan para conjuntos de filas de esquema. Conjuntos de filas de esquema permiten al proveedor devolver metadatos al consumidor sin que el consumidor tenga que ejecutar una consulta o la captura de datos. La búsqueda de metadatos puede ser mucho más rápida que la detección de capacidades de un proveedor.  
  
 La especificación de OLE DB requiere que los proveedores que implementan la **IDBSchemaRowset** tipos de conjunto de filas de esquema de compatibilidad con tres de interfaz: **DBSCHEMA_COLUMNS**, **DBSCHEMA_PROVIDER_TYPES** , y `DBSCHEMA_TABLES`. El asistente generará implementaciones para cada conjunto de filas de esquema. Cada clase generada por el Asistente contiene un `Execute` método. En este `Execute` método, puede devolver datos al proveedor sobre qué tablas, columnas y tipos de datos que admite. Estos datos normalmente se conocen en tiempo de compilación.  
  
## <a name="see-also"></a>Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)