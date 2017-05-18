---
title: _STATIC_ASSERT (macro) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _STATIC_ASSERT
dev_langs:
- C++
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 265796cdebbed1c0a067c44bbe6b71077be44a2b
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="staticassert-macro"></a>_STATIC_ASSERT (Macro)
Evalúa una expresión durante el tiempo de compilación y genera un error cuando el resultado es `FALSE`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
_STATIC_ASSERT(  
    booleanExpression  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `booleanExpression`  
 Expresión (incluidos los punteros) que se evalúa como un valor distinto de cero (`TRUE`) o 0 (`FALSE`).  
  
## <a name="remarks"></a>Comentarios  
 Esta macro es similar a las [macros _ASSERT y _ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), salvo que `booleanExpression` se evalúa en tiempo de compilación en lugar de hacerlo en tiempo de ejecución. Si `booleanExpression` se evalúa como `FALSE` (0), se genera el [error del compilador C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md).  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se comprueba si `sizeof` de un `int` es mayor o igual a 2 bytes y si `sizeof` de un `long` es igual a 1 byte. El programa no se compilará y generará el [error del compilador C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) porque un `long` es mayor que 1 byte.  
  
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
  
## <a name="requirements"></a>Requisitos  
  
|Macro|Encabezado necesario|  
|-----------|---------------------|  
|`_STATIC_ASSERT`|\<crtdbg.h>|  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)
