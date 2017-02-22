---
title: "Operadores de incremento y decremento prefijos | Microsoft Docs"
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
  - "operadores de decremento"
  - "operadores de decremento, sintaxis"
  - "operadores de incremento, tipos de"
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Operadores de incremento y decremento prefijos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A los operadores unarios \(`++` y **––**\) se les denomina operadores de incremento o decremento de "prefijo" cuando los operadores de incremento o decremento aparecen delante del operando.  El incremento y decremento de postfijo tiene una prioridad mayor que el incremento y decremento de prefijo.  El tipo del operando debe ser entero, flotante o de puntero y debe ser una expresión de valor L modificable \(una expresión sin el atributo **const**\).  El resultado es un valor L.  
  
 Cuando el operador aparece delante de su operando, el operando se incrementa o se reduce y su nuevo valor es el resultado de la expresión.  
  
 Un operando de tipo entero o flotante aumenta o disminuye en el valor entero 1.  El tipo del resultado es el mismo que el tipo del operando.  Un operando de tipo de puntero aumenta o disminuye en el tamaño del objeto al que apunta.  Un puntero incrementado apunta al siguiente objeto; un puntero disminuido apunta al objeto anterior.  
  
## Ejemplo  
 En este ejemplo se muestra el operador unario de decremento de prefijo:  
  
```  
if( line[--i] != '\n' )  
    return;  
```  
  
 En este ejemplo, la variable `i` se reduce antes de utilizarse como subíndice de `line`.  
  
## Vea también  
 [Operadores unarios de C](../c-language/c-unary-operators.md)