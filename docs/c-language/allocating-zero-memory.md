---
title: "Asignar memoria cero | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asignación de memoria, memoria cero"
  - "memoria cero"
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Asignar memoria cero
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.10.3** El comportamiento de la función `calloc`, `malloc` o `realloc` si el tamaño solicitado es cero  
  
 Las funciones `calloc`, `malloc` y `realloc` aceptan cero como argumento.  No se asigna ninguna memoria real, pero se devuelve un puntero válido y el bloque de memoria se puede modificar después mediante realloc.  
  
## Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)