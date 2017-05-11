---
title: _CrtDoForAllClientObjects | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
dev_langs:
- C++
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: df96a24b04473099daaca29472f90c9770181e82
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects
Llama a una función proporcionada por la aplicación para todos los tipos `_CLIENT_BLOCK` del montón (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _CrtDoForAllClientObjects(   
   void ( * pfn )( void *, void * ),  
   void *context  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pfn`  
 Puntero a la función de devolución de llamada proporcionada por la aplicación. El primer parámetro de esta función señala a los datos. El segundo parámetro es el puntero de contexto que se pasa a la llamada a `_CrtDoForAllClientObjects`.  
  
 `context`  
 Puntero al contexto proporcionado por la aplicación que se va a pasar a la función proporcionada por la aplicación.  
  
## <a name="remarks"></a>Comentarios  
 La función `_CrtDoForAllClientObjects` busca en la lista vinculada del montón bloques de memoria con el tipo `_CLIENT_BLOCK` y llama a la función proporcionada por la aplicación cuando se encuentra un bloque de este tipo. El bloque encontrado y el parámetro `context` se pasan como argumentos a la función proporcionada por la aplicación. Durante la depuración, una aplicación puede realizar el seguimiento de un grupo específico de asignaciones llamando explícitamente a las funciones del montón de depuración para asignar memoria y especificando que se asigne a los bloques el tipo de bloque `_CLIENT_BLOCK` . A continuación, se puede realizar el seguimiento y la notificación de estos bloques por separado durante la detección de pérdidas y la creación de informes sobre el estado de la memoria.  
  
 Si el campo de bits `_CRTDBG_ALLOC_MEM_DF` de la marca [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) no está activado, el resultado de `_CrtDoForAllClientObjects` se devuelve inmediatamente. Si no se define [_DEBUG](../../c-runtime-library/debug.md) , las llamadas a `_CrtDoForAllClientObjects` se quitan durante el preprocesamiento.  
  
 Para más información sobre el tipo `_CLIENT_BLOCK` y cómo lo pueden usar otras funciones de depuración, vea [Types of blocks on the debug heap](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).  
  
 Si `pfn` es `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establecen en `EINVAL` y la función vuelve.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtDoForAllClientObjects`|\<crtdbg.h>, \<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** solo versiones de depuración de las bibliotecas en tiempo de ejecución de C universales.  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)   
 [Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details)   
 [_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)
