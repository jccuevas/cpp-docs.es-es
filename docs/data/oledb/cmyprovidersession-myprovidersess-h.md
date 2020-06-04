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
ms.openlocfilehash: 4775f21c1e0fa7666d24b4d6a55e099bc6ae55a2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079758"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*Personalizado* de SESS. H contiene la declaración y la implementación del objeto de sesión OLE DB. El objeto de origen de datos crea el objeto de sesión y representa una conversación entre un consumidor y un proveedor. Pueden abrirse varias sesiones simultáneas para un origen de datos. La lista de herencia para `CCustomSession` sigue:

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

El objeto de sesión hereda de `IGetDataSource`, `IOpenRowset`, `ISessionProperties`y `IDBCreateCommand`. La interfaz de `IGetDataSource` permite que una sesión recupere el origen de datos que la creó. Esto resulta útil si necesita obtener propiedades del origen de datos que ha creado u otra información que el origen de datos puede proporcionar. La interfaz `ISessionProperties` controla todas las propiedades de la sesión. Las interfaces `IOpenRowset` y `IDBCreateCommand` se utilizan para realizar el trabajo de la base de datos. Si el proveedor admite comandos, implementa la interfaz `IDBCreateCommand`. Se usa para crear el objeto de comando que puede ejecutar comandos. El proveedor siempre implementa el objeto `IOpenRowset`. Se usa para generar un conjunto de filas a partir de un proveedor. Es un conjunto de filas predeterminado (por ejemplo, `"select * from mytable"`) de un proveedor.

El Asistente también genera tres clases de sesión: `CCustomSessionColSchema`, `CCustomSessionPTSchema`y `CCustomSessionTRSchema`. Estas sesiones se utilizan para los conjuntos de filas de esquema. Los conjuntos de filas de esquema permiten al proveedor devolver metadatos al consumidor sin que el consumidor tenga que ejecutar una consulta o capturar datos. La captura de metadatos puede ser mucho más rápida que encontrar las capacidades de un proveedor.

La especificación OLE DB requiere que los proveedores que implementan la interfaz `IDBSchemaRowset` admitan tres tipos de conjunto de filas de esquema: DBSCHEMA_COLUMNS, DBSCHEMA_PROVIDER_TYPES y DBSCHEMA_TABLES. El asistente genera implementaciones para cada conjunto de filas de esquema. Cada clase generada por el asistente contiene un método `Execute`. En este `Execute` método, puede devolver datos al proveedor sobre qué tablas, columnas y tipos de datos se admiten. Estos datos se conocen en tiempo de compilación.

## <a name="see-also"></a>Consulte también

[Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)<br/>
