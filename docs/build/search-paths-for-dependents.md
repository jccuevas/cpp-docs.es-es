---
title: "Rutas de b&#250;squeda para dependientes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dependientes, NMAKE"
  - "NMAKE (programa), dependientes"
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Rutas de b&#250;squeda para dependientes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada dependiente tiene una ruta de búsqueda opcional, que se especifica según se indica a continuación:  
  
## Sintaxis  
  
```  
{directory[;directory...]}dependent  
```  
  
## Comentarios  
 NMAKE busca primero un dependiente en el directorio actual y, a continuación, en directorios siguiendo el orden especificado.  Una macro puede especificar una parte o la totalidad de una ruta de búsqueda.  Los nombres de directorios se encierran entre llaves \({ }\); si hay varios directorios, se separan con un punto y coma \(;\).  No se permiten espacios ni tabulaciones.  
  
## Vea también  
 [Dependientes](../build/dependents.md)