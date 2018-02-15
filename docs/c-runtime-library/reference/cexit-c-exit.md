---
title: _cexit, _c_exit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _c_exit
- _cexit
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cexit
- c_exit
- _c_exit
- cexit
dev_langs:
- C++
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 825ed933d5a164fd6a07f13319d30fdf97a928e1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cexit-cexit"></a>_cexit, _c_exit
Realiza operaciones de limpieza y vuelve sin finalizar el proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _cexit( void );  
void _c_exit( void );  
```  
  
## <a name="remarks"></a>Comentarios  
 La función `_cexit` llama, por orden de último en entrar, primero en salir (LIFO), a las funciones que se registran mediante `atexit` y `_onexit`. Después, `_cexit` vacía todos los búferes de E/S y cierra todas las secuencias abiertas antes de volver. `_c_exit` es el mismo que `_exit` pero vuelve al proceso de llamada sin procesar `atexit` o `_onexit` ni vaciar los búferes de secuencia. El comportamiento de `exit`, `_exit`, `_cexit` y `_c_exit` se muestra en la siguiente tabla.  
  
|Función|Comportamiento|  
|--------------|--------------|  
|`exit`|Realiza los procedimientos completos de finalización de la biblioteca de C, finaliza el proceso y se cierra con el código de estado especificado.|  
|`_exit`|Realiza los procedimientos rápidos de finalización de la biblioteca de C, finaliza el proceso y se cierra con el código de estado especificado.|  
|`_cexit`|Realiza procedimientos completos de finalización de la biblioteca de C y vuelve al autor de la llamada, pero no finaliza el proceso.|  
|`_c_exit`|Realiza procedimientos rápidos de finalización de la biblioteca de C y vuelve al autor de la llamada, pero no finaliza el proceso.|  
  
 Cuando se llama a las funciones `_cexit` o `_c_exit`, no se llama a los destructores de ningún objeto temporal o automático que exista en el momento de la llamada. Un objeto automático es el que se define en una función en la que el objeto no se declara como estático. Un objeto temporal es el que crea el compilador. Para destruir un objeto automático antes de llamar a `_cexit` o `_c_exit`, llame explícitamente al destructor del objeto, tal y como se indica a continuación:  
  
```  
myObject.myClass::~myClass( );  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_cexit`|\<process.h>|  
|`_c_exit`|\<process.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec (Funciones)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn (Funciones)](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)