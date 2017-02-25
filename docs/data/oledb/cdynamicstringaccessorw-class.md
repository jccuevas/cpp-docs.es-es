---
title: "CDynamicStringAccessorW (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessorW"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicStringAccessorW (clase)"
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDynamicStringAccessorW (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite obtener acceso a un origen de datos cuando no se conoce el esquema de la base de datos \(estructura subyacente\).  
  
## Sintaxis  
  
```  
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;  
```  
  
## Comentarios  
 Ambos solicitud que el proveedor que todos los datos se obtiene acceso desde el almacén de datos como datos de cadena, sólo `CDynamicStringAccessor` solicita datos de cadena Unicode.  
  
 `CDynamicStringAccessorW` hereda **GetString** y `SetString` de `CDynamicStringAccessor`.  Cuando utiliza estos métodos en un objeto de `CDynamicStringAccessorW` , ***BaseType*** es **WCHAR**.  
  
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