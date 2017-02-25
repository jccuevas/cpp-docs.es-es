---
title: "/STACK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/STACK (opción de editbin)"
  - "STACK (opción de editbin)"
  - "-STACK (opción de editbin)"
  - "pila, establecer el tamaño"
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /STACK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/STACK:reserve[,commit]  
```  
  
## Comentarios  
 Esta opción establece el tamaño de la pila en bytes y utiliza argumentos en notación decimal o en la notación del lenguaje C.  La opción \/STACK sólo se aplica a un archivo ejecutable.  
  
 El argumento *reserve* especifica la asignación total de memoria virtual de la pila.  EDITBIN redondeará el valor especificado a los 4 bytes más próximos.  
  
 El argumento opcional `commit` está sujeto a interpretación por el sistema operativo.  En Windows NT, Windows 95 y Windows 98, `commit` especifica la cantidad de memoria física que se debe asignar de una sola vez.  La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación.  Si se asigna un valor más alto a `commit`, se ahorrará tiempo cuando la aplicación necesite más espacio de la pila, pero aumentarán los requisitos de memoria y, posiblemente, el tiempo de inicio.  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)