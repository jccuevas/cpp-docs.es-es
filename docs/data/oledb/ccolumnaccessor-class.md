---
title: "CColumnAccessor (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CColumnAccessor"
  - "ATL::CColumnAccessor"
  - "ATL.CColumnAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CColumnAccessor (clase)"
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CColumnAccessor (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera insertó código de consumidor.  
  
## Sintaxis  
  
```  
class CColumnAccessor : public CAccessorBase  
```  
  
## Comentarios  
 En el código insertado, cada columna se enlaza como descriptor independiente.  Debe tener en cuenta que esta clase se utiliza en el código insertado \(por ejemplo, es posible que encuentre al depurar\), pero normalmente nunca tiene que usar la o sus métodos directamente.  
  
 `CColumnAccessor` implementa los siguientes métodos de código auxiliar, correspondientes en funcionalidad a otros métodos de clase de descriptor de acceso:  
  
-   constructor de`CColumnAccessor`The; crea instancias e inicializa el objeto de `CColumnAccessor` .  
  
-   memoria de`CreateAccessor`Allocates para estructuras de enlace de columna e inicializa los miembros de datos de columna.  
  
-   **BindColumns** enlaza las columnas a los descriptores de acceso.  
  
-   Búferes de**SetParameterBuffer**Allocates para los parámetros.  
  
-   `AddParameter` agrega una entrada de parámetro a las estructuras de entrada de parámetros.  
  
-   **HasOutputColumns** determina si el descriptor de acceso ha generado columnas  
  
-   **HasParameters** determina si el descriptor de acceso tiene parámetros.  
  
-   `BindParameters` enlaza los parámetros creados a las columnas.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)