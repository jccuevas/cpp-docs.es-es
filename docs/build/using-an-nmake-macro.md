---
title: "Utilizar una macro NMAKE | Microsoft Docs"
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
  - "macros, NMAKE"
  - "NMAKE (macros), utilizar"
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Utilizar una macro NMAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para usar una macro, se ha de encerrar su nombre entre paréntesis precedido por un signo de moneda \($\), como se muestra a continuación.  
  
## Sintaxis  
  
```  
$(macroname)  
```  
  
## Comentarios  
 No se permiten espacios.  Los paréntesis son opcionales si *macroname* es un carácter único.  La cadena de definición reemplaza a $\(*macroname*\); una macro no definida se reemplaza por una cadena nula.  
  
## ¿Sobre qué desea obtener más información?  
 [Sustitución de macros](../build/macro-substitution.md)  
  
## Vea también  
 [Las macros y NMAKE](../build/macros-and-nmake.md)