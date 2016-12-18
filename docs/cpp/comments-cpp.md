---
title: "Comentarios en C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "comentarios en código, C++"
  - "comentarios, código C++"
  - "comentarios, documentar código"
  - "espacio en blanco, comentarios en C++"
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comentarios en C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un comentario es texto que el compilador omite pero que es útil para los programadores.  Los comentarios se usan normalmente para anotar código para su referencia futura.  El compilador los trata como si fueran espacios en blanco.  Puede usar comentarios en las pruebas para desactivar algunas líneas de código; sin embargo, para esto es mejor utilizar directivas de preprocesador `#if`\/`#endif` porque se puede incluir entre ellas código que contiene comentarios, pero no se pueden anidar comentarios.  
  
 Los comentarios de C\+\+ se escriben de una de las maneras siguientes:  
  
-   Los caracteres `/*` \(barra diagonal, asterisco\), seguidos de cualquier secuencia de caracteres \(incluidas nuevas líneas\), seguidos de los caracteres `*/`.  Esta sintaxis es la misma que para ANSI C.  
  
-   Los caracteres `//` \(dos barras diagonales\), seguidos de cualquier secuencia de caracteres.  Una nueva línea que no va precedida inmediatamente de una barra diagonal inversa finaliza esta forma de comentario.  Por tanto, normalmente se denomina "comentario de una sola línea".  
  
 Los caracteres de comentario \(`/*`, `*/` y `//`\) no tienen ningún significado especial dentro de una constante de caracteres, un literal de cadena o un comentario.  Por tanto, los comentarios que usan la primera sintaxis no se pueden anidar.  
  
## Vea también  
 [Convenciones léxicas](../cpp/lexical-conventions.md)