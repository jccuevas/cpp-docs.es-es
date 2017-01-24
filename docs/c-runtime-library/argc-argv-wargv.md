---
title: "__argc, __argv, __wargv | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__wargv"
  - "__argv"
  - "__argc"
apilocation: 
  - "msvcrt120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__argv"
  - "__argc"
  - "__wargv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__argc"
  - "__argv"
  - "__wargv"
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __argc, __argv, __wargv
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La variable global `__argc` es un recuento del número de argumentos de línea de comandos que se pasa al programa.  `__argv` es un puntero a una matriz de cadenas de carácter de un solo byte o de carácter multibyte que contienen los argumentos del programa, mientras que `__wargv` es un puntero a una matriz de cadenas de carácter ancho que contienen los argumentos del programa.  Estas variables globales proporcionan los argumentos para `main` o `wmain`.  
  
## Sintaxis  
  
```  
extern int __argc; extern char ** __argv; extern wchar_t ** __wargv;  
```  
  
## Comentarios  
 En un programa que usa la función `main`,  `__argc` y `__argv` se inicializan cuando se inicia el programa mediante una línea de comandos que se usa para iniciar el programa.  La línea de comandos se analiza en argumentos individuales y los comodines se expanden.  El número de argumentos se asigna a `__argc` y las cadenas de argumento se asignan en el montón, al tiempo que un puntero a la matriz de argumentos se asigna a `__argv`.  En un programa compilado para usar caracteres anchos y una función `wmain`, los argumentos se analizan y los comodines se expanden como cadenas de carácter ancho, y un puntero a la matriz de cadenas de argumento se asigna a `__wargv`.  
  
 En código portable, recomendamos usar argumentos pasados a `main` para obtener los argumentos de línea de comandos en el programa.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE no definido|\_UNICODE definido|  
|--------------------|---------------------------|------------------------|  
|`__targv`|`__argv`|`__wargv`|  
  
## Requisitos  
  
|Variable global|Encabezado necesario|  
|---------------------|--------------------------|  
|`__argc`, `__argv`, `__wargv`|\<stdlib.h\>, \<cstdlib\> \(C\+\+\)|  
  
 `__argc`, `__argv` y `__wargv` son extensiones de Microsoft.  Para obtener información sobre la compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Variables globales](../c-runtime-library/global-variables.md)   
 [main: inicio de programa](../cpp/main-program-startup.md)   
 [Usar wmain en vez de main](../cpp/using-wmain-instead-of-main.md)