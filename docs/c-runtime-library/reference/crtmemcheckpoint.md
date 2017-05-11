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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 1904bf5c2632b0913db8e5a9fb838a602615cb45
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

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
  
 Si `state` es `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establecen en `EINVAL` y la función vuelve.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtMemCheckpoint`|\<crtdbg.h>, \<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** solo versiones de depuración de la UCRT.  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md)
