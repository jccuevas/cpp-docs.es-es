---
title: _query_new_mode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _query_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- query_new_mode
- _query_new_mode
dev_langs:
- C++
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 38b5022412f3f07806fcb7a2cea373457c8b405f
ms.lasthandoff: 02/24/2017

---
# <a name="querynewmode"></a>_query_new_mode
Devuelve un entero que indica el nuevo modo de controlador establecido por `_set_new_mode` para `malloc`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int _query_new_mode(  
   void   
);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el nuevo modo de controlador actual; es decir, 0 o 1 para `malloc`. Un valor devuelto de 1 indica que, en caso de error para asignar memoria, `malloc` llama a la rutina del nuevo controlador; un valor devuelto de 0 indica lo contrario.  
  
## <a name="remarks"></a>Comentarios  
 La función `_query_new_mode` de C++ devuelve un entero que indica el nuevo modo de controlador establecido por la función [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) de C++ para [malloc](../../c-runtime-library/reference/malloc.md). El nuevo modo de controlador indica si, en caso de error para asignar memoria, `malloc` va a llamar a la rutina del nuevo controlador según lo establecido por [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md). De forma predeterminada, `malloc` no llama a la rutina del nuevo controlador en caso de error. Puede usar `_set_new_mode` para invalidar este comportamiento de manera que, en caso de error, `malloc` llame a la rutina del nuevo controlador de la misma manera que el operador **new** cuando se produce un error al asignar memoria. Para obtener más información, vea la descripción de los [operadores new y delete](../../cpp/new-and-delete-operators.md) en la referencia del lenguaje de C++.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_query_new_mode`|\<new.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_query_new_handler](../../c-runtime-library/reference/query-new-handler.md)
