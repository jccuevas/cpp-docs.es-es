---
title: "Caracteres anchos | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "caracteres anchos"
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Caracteres anchos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.1.3.4** Valor de una constante de caracteres enteros que contiene más de un carácter o una constante de caracteres anchos que contiene más de un carácter multibyte  
  
 La constante de caracteres normales "ab" tiene el valor entero \(int\)0x6162.  Cuando hay más de un byte, los bytes de lectura anteriores se desplazan a la izquierda según el valor de **CHAR\_BIT** y el byte siguiente se compara mediante el operador OR bit a bit con los bits inferiores de **CHAR\_BIT**.  El número de bytes de la constante de caracteres multibyte no puede superar sizeof\(int\), que es 4 para el código de 32 bits de destino.  
  
 La constante de caracteres multibyte se lee como se indica arriba y se convierte en una constante de caracteres anchos mediante la función en tiempo de ejecución `mbtowc`.  Si el resultado no es una constante de caracteres anchos válida, se produce un error.  En cualquier caso, el número de bytes examinados por la función `mbtowc` se limita al valor de `MB_CUR_MAX`.  
  
## Vea también  
 [Characters](../c-language/characters.md)