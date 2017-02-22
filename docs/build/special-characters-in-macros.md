---
title: "Caracteres especiales en las macros | Microsoft Docs"
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
  - "caracteres especiales, en macros NMAKE"
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Caracteres especiales en las macros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un signo de número \(\#\) después de una definición especifica un comentario.  Para especificar un signo de número literal en una macro, se ha de utilizar un signo de intercalación \(^\), como en ^\#.  
  
 Un signo de moneda \($\) especifica una llamada de macro.  Para especificar un signo $ literal, se ha de utilizar $$.  
  
 Para ampliar una definición a una nueva línea, la línea ha de terminar con una barra inversa \(\\\).  Cuando se llama a una macro, la barra inversa y el carácter de nueva línea se reemplazan por un espacio.  Para especificar una barra inversa literal al final de la línea, ha de ir precedida de un signo de intercalación \(^\) o incluirse a continuación de ella un especificador de comentario \(\#\).  
  
 Para especificar un carácter de nueva línea literal, la línea ha de terminar con un signo de intercalación \(^\), como en el siguiente caso:  
  
```  
CMDS = cls^  
dir  
```  
  
## Vea también  
 [Definir una macro NMAKE](../build/defining-an-nmake-macro.md)