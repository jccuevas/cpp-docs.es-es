---
title: "Pseudodestinos | Microsoft Docs"
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
  - "Make (archivos), pseudodestinos"
  - "NMAKE (programa), pseudodestinos"
  - "NMAKE (programa), destinos"
  - "pseudodestinos y NMAKE"
  - "marcas de tiempo, pseudodestinos del archivo make"
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Pseudodestinos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un pseudodestino es una etiqueta que se utiliza en lugar de un nombre de archivo en una línea de dependencia.  Se interpreta como un archivo que no existe y que, por tanto, no está actualizado.  NMAKE supone que la marca de tiempo de un pseudodestino es la más reciente de todos sus dependientes.  Si no tiene dependientes, se supone la hora actual.  Si un pseudodestino se usa como destino, siempre se ejecutan sus comandos.  Un pseudodestino utilizado como un dependiente también debe aparecer como un destino en otra dependencia.  Sin embargo, esa dependencia no necesita tener un bloque de comandos.  
  
 Los nombres de pseudodestinos siguen las reglas de sintaxis de los nombres de archivos para los destinos.  Sin embargo, si el nombre no tiene una extensión \(es decir, no contiene un punto\), puede superar el límite de 8 caracteres correspondiente a los nombres de archivos y puede tener una longitud de hasta 256 caracteres.  
  
## Vea también  
 [Destinos](../build/targets.md)