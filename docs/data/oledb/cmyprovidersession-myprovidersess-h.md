---
title: CCustomSession (CustomSess.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidersession
- myprovidersess.h
- ccustomsession
- customsess.h
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
- CCustomSession class in CustomSess.H
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
ms.openlocfilehash: 75d0c8d871ca736be5e2c33829296b2760092e14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568017"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*Custom*Sess.H contiene la declaración e implementación para el objeto de sesión de OLE DB. El objeto de origen de datos crea el objeto de sesión y representa una conversación entre un consumidor y proveedor. Varias sesiones simultáneas pueden estar abiertas para un origen de datos. La lista de herencia para `CCustomSession` sigue:

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSession
class ATL_NO_VTABLE CCustomSession : 
   public CComObjectRootEx<CComSingleThreadModel>,
   public IGetDataSourceImpl<CCustomSession>,
   public IOpenRowsetImpl<CCustomSession>,
   public ISessionPropertiesImpl<CCustomSession>,
   public IObjectWithSiteSessionImpl<CCustomSession>,
   public IDBSchemaRowsetImpl<CCustomSession>,
   public IDBCreateCommandImpl<CCustomSession, CCustomCommand>
```

El objeto de sesión se hereda de `IGetDataSource`, `IOpenRowset`, `ISessionProperties`, y `IDBCreateCommand`. El `IGetDataSource` interfaz permite a una sesión recuperar el origen de datos que lo creó. Esto es útil si tiene que obtener las propiedades del origen de datos que ha creado u otra información que puede proporcionar el origen de datos. El `ISessionProperties` interfaz controla todas las propiedades de la sesión. El `IOpenRowset` y `IDBCreateCommand` interfaces se usan para realizar el trabajo de base de datos. Si el proveedor admite comandos, implementa el `IDBCreateCommand` interfaz. Sirve para crear el objeto de comando que se puede ejecutar comandos. El proveedor siempre implementa la `IOpenRowset` objeto. Sirve para generar un conjunto de filas de un proveedor. Es un conjunto de filas predeterminado (por ejemplo, `"select * from mytable"`) de un proveedor.

El asistente también genera tres clases de sesión: `CCustomSessionColSchema`, `CCustomSessionPTSchema`, y `CCustomSessionTRSchema`. Estas sesiones se utilizan para conjuntos de filas de esquema. Conjuntos de filas de esquema que el proveedor pueda devolver los metadatos al consumidor sin que el consumidor de tener que ejecutar una consulta o la captura de datos. La búsqueda de metadatos puede ser mucho más rápida que buscar las capacidades del proveedor.

La especificación OLE DB requiere que los proveedores que implementan el `IDBSchemaRowset` tipos de conjunto de filas de esquema de compatibilidad con tres interfaz: DBSCHEMA_COLUMNS, DBSCHEMA_PROVIDER_TYPES y DBSCHEMA_TABLES. El asistente genera las implementaciones para cada conjunto de filas de esquema. Cada clase generada por el Asistente contiene un `Execute` método. En este `Execute` método, puede devolver datos al proveedor sobre qué tablas, columnas y tipos de datos que admite. Estos datos se conocen en tiempo de compilación.

## <a name="see-also"></a>Vea también

[Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)<br/>
