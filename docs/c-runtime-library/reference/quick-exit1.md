---
title: quick_exit1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: quick_exit
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
- quick_exit
- process/quick_exit
- stdlib/quick_exit
dev_langs: C++
helpviewer_keywords: quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fb6a8bdea6cb37bd70d6aeda490e2470aa74e999
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="quickexit"></a>quick_exit
Provoca la finalización del programa normal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec(noreturn) void quick_exit(  
    int status  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 status  
 El código de estado que se devolverá al entorno de host.  
  
## <a name="return-value"></a>Valor devuelto  
 La función `quick_exit` no puede volver a su llamador.  
  
## <a name="remarks"></a>Comentarios  
 La función `quick_exit` provoca la finalización del programa normal. No llama a ninguna función registrada por `atexit`, `_onexit` o a los controladores de señales registrados por la función `signal` . El comportamiento es indefinido si se llama a `quick_exit` más de una vez o si se se llama también a la función `exit` .  
  
 La función `quick_exit` llama, en el orden el último en entrar es el primero en salir (LIFO), a las funciones registradas por `at_quick_exit`, excepto las funciones a las que ya se ha llamado cuando se registró la función.  El comportamiento es indefinido si se realiza una llamada [longjmp](../../c-runtime-library/reference/longjmp.md) durante una llamada a una función registrada que finalizaría la llamada a la función.  
  
 Después de llamarse a las funciones registradas, `quick_exit` invoca `_Exit` con el valor valor `status` para devolver el control al entorno de host.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`quick_exit`|\<process.h> o \<stdlib.h>|  
  
 Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec (Funciones)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn (Funciones)](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)