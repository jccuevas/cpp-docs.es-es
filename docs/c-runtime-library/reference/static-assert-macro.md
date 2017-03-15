---
title: "_STATIC_ASSERT (Macro) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "_STATIC_ASSERT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_STATIC_ASSERT (macro)"
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _STATIC_ASSERT (Macro)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Evaluar una expresión en tiempo de compilación y genere un error cuando el resultado es `FALSE`.  
  
## Sintaxis  
  
```  
_STATIC_ASSERT(  
    booleanExpression  
);  
```  
  
#### Parámetros  
 `booleanExpression`  
 Expresión \(punteros incluida que se evalúa como cero \(`TRUE`\) o 0 \(`FALSE`\).  
  
## Comentarios  
 Esta macro se parece a [macros \_ASSERT y \_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), salvo que `booleanExpression` se evalúa en tiempo de compilación en lugar de en tiempo de ejecución.  Si `booleanExpression` se evalúa como `FALSE` \(0\), se genera [Error del compilador C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) .  
  
## Ejemplo  
 En este ejemplo, comprobamos si `sizeof``int` sea mayor que o igual a 2 bytes y si `sizeof``long` es 1 bytes.  El programa no se compilará y generará [Error del compilador C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) porque `long` es mayor de 1 byte.  
  
```  
// crt__static_assert.c  
  
#include <crtdbg.h>  
#include <stdio.h>  
  
_STATIC_ASSERT(sizeof(int) >= 2);  
_STATIC_ASSERT(sizeof(long) == 1);  // C2466  
  
int main()  
{  
    printf("I am sure that sizeof(int) will be >= 2: %d\n",  
        sizeof(int));  
    printf("I am not so sure that sizeof(long) == 1: %d\n",  
        sizeof(long));  
}  
```  
  
## Requisitos  
  
|Macro|Encabezado necesario|  
|-----------|--------------------------|  
|`_STATIC_ASSERT`|\<crtdbg.h\>|  
  
## Equivalente en .NET Framework  
 [System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_ASSERT, \_ASSERTE, \_ASSERT\_EXPR \(macros\)](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)