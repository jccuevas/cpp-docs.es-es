---
title: _CrtMemCheckpoint | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
dev_langs:
- C++
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 5f9b0615a51318ea0e783a90d7a450b6e11372d2
ms.lasthandoff: 02/24/2017

---
# <a name="crtmemcheckpoint"></a>_CrtMemCheckpoint
Obtiene el estado actual del montón de depuración y lo almacena en una estructura de `_CrtMemState` proporcionada por la aplicación (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _CrtMemCheckpoint(  
   _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `state`  
 Puntero a la estructura de `_CrtMemState` que se va a rellenar con el punto de control de memoria.  
  
## <a name="remarks"></a>Comentarios  
 La función `_CrtMemCheckpoint` crea una instantánea del estado actual del montón de depuración en cualquier momento determinado. Esta instantánea la pueden usar otras funciones de estado del montón, como [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md), para ayudar a detectar pérdidas de memoria y otros problemas. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtMemState` se quitan durante el preprocesamiento.  
  
 La aplicación debe pasar un puntero a una instancia de la estructura de `_CrtMemState` previamente asignada, definida en Crtdbg.h, en el parámetro `state` . Si `_CrtMemCheckpoint` encuentra un error durante la creación del punto de control, la función genera un informe de depuración de `_CRT_WARN` en el que se describe el problema.  
  
 Para obtener más información sobre las funciones de estado del montón y la estructura `_CrtMemState`, consulte [Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para obtener más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Si `state` es `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establecen en `EINVAL` y la función vuelve.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtMemCheckpoint`|\<crtdbg.h>, \<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** solo versiones de depuración de la UCRT.  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md)
