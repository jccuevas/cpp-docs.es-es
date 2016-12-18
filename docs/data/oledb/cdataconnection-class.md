---
title: "CDataConnection (Clase) | Microsoft Docs"
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
  - "ATL::CDataConnection"
  - "ATL.CDataConnection"
  - "CDataConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataConnection (clase)"
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Administra la conexión con el origen de datos.  
  
## Sintaxis  
  
```  
class CDataConnection  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[CDataConnection](../../data/oledb/cdataconnection-cdataconnection.md)|Constructor.  Crea instancias e inicializa un objeto de `CDataConnection` .|  
|[Copiar](../../data/oledb/cdataconnection-copy.md)|Crea una copia de una conexión de datos existentes.|  
|[Abrir](../../data/oledb/cdataconnection-open.md)|Abra una conexión a un origen de datos mediante una cadena de inicialización.|  
|[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)|Abre una nueva sesión en la conexión actual.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador BOOL](../../data/oledb/cdataconnection-operator-bool.md)|Determina si la sesión actual está abierto o no.|  
|[bool de operador](../../data/oledb/cdataconnection-operator-bool-ole-db.md)|Determina si la sesión actual está abierto o no.|  
|[operador CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)|Devuelve una referencia al objeto contenido de `CDataSource` .|  
|[operador CDataSource\*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)|Devuelve un puntero al objeto contenido de `CDataSource` .|  
|[operador CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)|Devuelve una referencia al objeto contenido de `CSession` .|  
|[operador CSession\*](../../data/oledb/cdataconnection-operator-csession-star.md)|Devuelve un puntero al objeto contenido de `CSession` .|  
  
## Comentarios  
 `CDataConnection` es una clase útil para crear clientes porque encapsula objetos necesarios \(origen de datos y sesión\) y algunos de trabajo necesario al conectarse a un origen de datos  
  
 Sin `CDataConnection`, tendrá que crear un objeto de `CDataSource` , llamar al método de [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) , después para crear una instancia de un objeto de [CSession](../../data/oledb/csession-class.md) , llamar al método de [Abierta](../../data/oledb/csession-open.md) , después para crear un objeto de [CCommand](../../data/oledb/ccommand-class.md) y llamar al **Abierta**\* métodos.  
  
 Con `CDataConnection`, debe crear un objeto de conexión, se pasa una cadena de inicialización, utiliza sólo esa conexión a comandos abierto.  Si va a utilizar la conexión a la base de datos reiteradamente, es conveniente mantener la conexión abierta, y `CDataConnection` proporciona una manera cómoda de ello.  
  
> [!NOTE]
>  Si está creando una aplicación de base de datos que necesite controlar sesiones múltiples, necesitará utilizar [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)