---
title: "/HEAP | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/heap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asignación de montones, establecer tamaño del montón"
  - "HEAP (opción de editbin)"
  - "-HEAP (opción de editbin)"
  - "/HEAP (opción de editbin)"
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /HEAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el tamaño de la pila en bytes.  Esta opción sólo se aplica a los archivos ejecutables.  
  
```  
  
/HEAP:  
reserve[,commit]  
  
```  
  
## Comentarios  
 El argumento de `reserve` especifica la asignación inicial total del montón en memoria virtual.  De forma predeterminada, el tamaño de la pila es 1 MB.  [Referencia de EDITBIN](../../build/reference/editbin-reference.md) reúne el valor especificado al múltiplo más cercano de 4 bytes.  
  
 El argumento opcional `commit` está sujeto a interpretación por el sistema operativo.  En un sistema operativo Windows, especifica la cantidad inicial de memoria física para asignar, y la cantidad de memoria adicional para asignar a la pila debe ser expandida.  La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación.  Un valor más alto de `commit` permite al sistema asigna memoria menos a menudo cuando la aplicación necesita más espacio de pila pero aumenta los requisitos de memoria y posiblemente la duración del inicio de la aplicación.  El valor de `commit` debe ser menor o igual que el valor de `reserve` .  
  
 Especifique los valores de `reserve` y de `commit` en notación de decimal o hexadecimal o octal del lenguaje C.  Por ejemplo, un valor de 1 MB se puede especificar como 1048576 en decimal, o como 0x100000 en hexadecimal, o como 04000000 en octal.  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)