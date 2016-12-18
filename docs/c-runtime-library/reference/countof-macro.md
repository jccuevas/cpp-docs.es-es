---
title: "_countof (Macro) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_countof"
  - "countof"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_countof (macro)"
  - "countof (macro)"
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _countof (Macro)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el número de elementos de una matriz asignada estáticamente.  
  
## Sintaxis  
  
```  
size_t _countof(   
   array  
);  
```  
  
#### Parámetros  
 `array`  
 Nombre de una matriz.  
  
## Valor devuelto  
 Número de elementos de la matriz, expresados como un `size_t`.  
  
## Comentarios  
 Asegúrese de que `array` es realmente una matriz, no un puntero.  En C, `_countof` producirá resultados erróneos si `array` es un puntero.  En C\+\+, `_countof` no se compilará si `array` es un puntero.  
  
## Requisitos  
  
|Macro|Encabezado necesario|  
|-----------|--------------------------|  
|`_countof`|\<stdlib.h\>|  
  
## Ejemplo  
  
```  
// crt_countof.cpp  
#define _UNICODE  
#include <stdio.h>  
#include <stdlib.h>  
#include <tchar.h>  
  
int main( void )  
{  
   _TCHAR arr[20], *p;  
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );  
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );  
   // In C++, the following line would generate a compile-time error:  
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)  
  
   _tcscpy_s( arr, _countof(arr), _T("a string") );  
   // unlike sizeof, _countof works here for both narrow- and wide-character strings  
}  
```  
  
  **sizeof\(arr\) \= 40 bytes**  
**\_countof\(arr\) \= 20 elementos**   
## Vea también  
 [sizeof \(Operador\)](../../cpp/sizeof-operator.md)