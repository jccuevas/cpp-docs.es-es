---
title: "CMyProviderSession (MyProviderSess.H) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cmyprovidersession"
  - ""myprovidersess.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMyProviderSession (clase): MyProviderSess.H"
  - "proveedores OLE DB, archivos generados por el asistente"
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderSession (MyProviderSess.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MyProviderSess.H contiene la declaración y la implementación del objeto de sesión de OLE DB.  El objeto de origen de datos crea el objeto de sesión y representa una conversación entre un consumidor y un proveedor.  Es posible abrir varias sesiones simultáneas para un origen de datos.  A continuación se muestra la lista de herencia para `CMyProviderSession`:  
  
```  
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
  
 El objeto de sesión hereda de **IGetDataSource**, `IOpenRowset`, **ISessionProperties** e **IDBCreateCommand**.  La interfaz **IGetDataSource** permite a una sesión recuperar el origen de datos que la creó.  Esto es útil si necesita obtener propiedades del origen de datos que creó u otros datos que el origen de datos puede proporcionar.  La interfaz **ISessionProperties** controla todas las propiedades de la sesión.  Las interfaces `IOpenRowset` e **IDBCreateCommand** se utilizan para hacer el trabajo de la base de datos.  Si el proveedor admite comandos, implementa la interfaz **IDBCreateCommand**.  Se utiliza para crear el objeto de comando que puede ejecutar comandos.  El proveedor siempre implementa el objeto `IOpenRowset`.  Se utiliza para generar un único conjunto de filas de un proveedor.  Éste es un conjunto de filas predeterminado \(por ejemplo, `"select * from mytable"`\) de un proveedor.  
  
 El asistente también generará tres clases de sesión: `CMyProviderSessionColSchema`, `CMyProviderSessionPTSchema` y `CMyProviderSessionTRSchema`.  Estas sesiones se utilizan para conjuntos de filas de esquema.  Los conjuntos de filas de esquema permiten al proveedor devolver metadatos al consumidor sin que el consumidor tenga que ejecutar una consulta o buscar datos.  La búsqueda de metadatos puede ser mucho más rápida que tener que detectar las capacidades de un proveedor.  
  
 La especificación OLE DB requiere que los proveedores que implementen la interfaz **IDBSchemaRowset** admitan tres tipos de conjuntos de filas de esquema: **DBSCHEMA\_COLUMNS**, **DBSCHEMA\_PROVIDER\_TYPES** y `DBSCHEMA_TABLES`.  El asistente generará implementaciones para cada conjunto de filas de esquema.  Cada clase generada por el asistente contiene un método `Execute`.  En este método `Execute`, se pueden devolver al proveedor datos acerca de para qué tablas, columnas y tipos de datos desea ofrecer compatibilidad.  Estos datos se suelen conocer en tiempo de compilación.  
  
## Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)