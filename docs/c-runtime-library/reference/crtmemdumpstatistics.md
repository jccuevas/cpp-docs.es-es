---
title: _CrtMemDumpStatistics | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
caps.latest.revision: 15
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
ms.openlocfilehash: 3d5065e62248a89de8dbe0ae38f354e0ead40ba6
ms.lasthandoff: 02/24/2017

---
# <a name="crtmemdumpstatistics"></a>_CrtMemDumpStatistics
Vuelca la información del encabezado de depuración de un estado del montón especificado en un formato legible para el usuario (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _CrtMemDumpStatistics(   
   const _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `state`  
 Puntero al estado del montón que se va a volcar.  
  
## <a name="remarks"></a>Comentarios  
 La función `_CrtMemDumpStatistics` vuelca la información del encabezado de depuración de un estado del montón especificado en un formato legible para el usuario. La aplicación puede usar las estadísticas del volcado para realizar el seguimiento de las asignaciones y detectar problemas de memoria. El estado de la memoria puede contener un estado de montón concreto o la diferencia entre dos estados. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtMemDumpStatistics` se quitan durante el preprocesamiento.  
  
 El parámetro `state` debe ser un puntero a una estructura `_CrtMemState` que [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) ha rellenado o que [_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md) ha devuelto antes de que se llame a `_CrtMemDumpStatistics`. Si `state` es `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y no se realiza ninguna acción. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Para obtener más información sobre las funciones de estado del montón y la estructura `_CrtMemState`, consulte [Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para obtener más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|-------------|---------------------|----------------------|  
|`_CrtMemDumpStatistics`|\<crtdbg.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** solo versiones de depuración de [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 <xref:System.Diagnostics.PerformanceCounter?displayProperty=fullName>  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)
