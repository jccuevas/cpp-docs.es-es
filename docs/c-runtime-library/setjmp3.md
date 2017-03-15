---
title: "_setjmp3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_setjmp3"
apilocation: 
  - "msvcrt.dll"
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "setjmp3"
  - "_setjmp3"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_setjmp3 (función)"
  - "setjmp3 (función)"
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _setjmp3
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Función de CRT interna.  Nueva implementación de la función `setjmp`.  
  
## Sintaxis  
  
```  
int _setjmp3(    OUT jmp_buf env,    int count,    (optional parameters) );  
```  
  
#### Parámetros  
 \[out\] `env`  
 Dirección del búfer para almacenar la información de estado.  
  
 \[in\] `count`  
 Número de `DWORD` de información adicionales que hay almacenados en los `optional parameters`.  
  
 \[in\] `optional parameters`  
 Datos adicionales insertados por la función intrínseca `setjmp`.  El primer `DWORD` es un puntero de función que sirve para desenredar datos extra y regresar a un estado de registro no volatile.  El segundo `DWORD` es el nivel de intento que se va a restaurar.  Cualquier otro dato extra se guarda en la matriz de datos genéricos de `jmp_buf`.  
  
## Valor devuelto  
 Siempre devuelve 0.  
  
## Comentarios  
 No use esta función en un programa de C\+\+.  Se trata de una función intrínseca que no admite C\+\+.  Para obtener más información acerca de cómo se usa `setjmp`, vea [Usar setjmp\/longjmp](../cpp/using-setjmp-longjmp.md).  
  
## Requisitos  
  
## Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [setjmp](../c-runtime-library/reference/setjmp.md)