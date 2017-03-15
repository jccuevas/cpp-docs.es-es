---
title: "CDynamicStringAccessorA (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessorA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicStringAccessorA (clase)"
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDynamicStringAccessorA (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite obtener acceso a un origen de datos cuando no se conoce el esquema de la base de datos \(estructura subyacente\).  
  
## Sintaxis  
  
```  
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;  
```  
  
## Comentarios  
 Ambos solicitud que el proveedor que todos los datos se obtiene acceso desde el almacén de datos como datos de cadena, sólo `CDynamicStringAccessor` solicita datos de cadena ANSI.  
  
 `CDynamicStringAccessorA` hereda **GetString** y `SetString` de `CDynamicStringAccessor`.  Cuando utiliza estos métodos en un objeto de `CDynamicStringAccessorA` , ***BaseType*** es **char**.  
  
## Requisitos  
 **Encabezado**: atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor \(Clase\)](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor \(Clase\)](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor \(Clase\)](../../data/oledb/cdynamicstringaccessor-class.md)