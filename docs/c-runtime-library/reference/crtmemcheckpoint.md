---
title: _CrtMemCheckpoint | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37333b2b4621b9434a9fe1a924162957d5ea824f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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
 La función `_CrtMemCheckpoint` crea una instantánea del estado actual del montón de depuración en cualquier momento determinado. Esta instantánea la pueden usar otras funciones de estado del montón, como [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md) , para ayudar a detectar pérdidas de memoria y otros problemas. Si no se define [_DEBUG](../../c-runtime-library/debug.md) , las llamadas a `_CrtMemState` se quitan durante el preprocesamiento.  
  
 La aplicación debe pasar un puntero a una instancia de la estructura de `_CrtMemState` previamente asignada, definida en Crtdbg.h, en el parámetro `state` . Si `_CrtMemCheckpoint` encuentra un error durante la creación del punto de control, la función genera un informe de depuración de `_CRT_WARN` en el que se describe el problema.  
  
 Para más información sobre las funciones de estado del montón y la estructura `_CrtMemState` , vea [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details). Para más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).  
  
 Si `state` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Parameter Validation](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establecen en `EINVAL` y la función vuelve.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtMemCheckpoint`|\<crtdbg.h>, \<errno.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
 **Bibliotecas:** solo versiones de depuración de la UCRT.  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md)