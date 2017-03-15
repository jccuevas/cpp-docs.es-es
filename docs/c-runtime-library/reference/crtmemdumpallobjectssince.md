---
title: _CrtMemDumpAllObjectsSince | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: e94e06d8a1c597b0b7353dee9ae9b2988e1e7b26
ms.lasthandoff: 02/24/2017

---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince
Vuelca información sobre objetos en el montón desde el inicio de la ejecución del programa o desde un estado del montón especificado (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      void _CrtMemDumpAllObjectsSince(   
   const _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `state`  
 Puntero al estado del montón desde el que se va a iniciar el volcado o **NULL**.  
  
## <a name="remarks"></a>Comentarios  
 La función `_CrtMemDumpAllObjectsSince` vuelca, con un formato legible para el usuario, la información de encabezado de depuración de objetos asignados en el montón. La aplicación puede usar la información del volcado para realizar el seguimiento de las asignaciones y detectar problemas de memoria. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtMemDumpAllObjectsSince` se quitan durante el preprocesamiento.  
  
 `_CrtMemDumpAllObjectsSince` utiliza el valor del parámetro `state` para determinar dónde iniciar la operación de volcado. Para iniciar el volcado desde un estado del montón especificado, el parámetro `state` debe ser un puntero a una estructura **_CrtMemState** que [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) ha rellenado antes de que se llamara a `_CrtMemDumpAllObjectsSince`. Cuando `state` es **NULL**, la función empieza el volcado desde el inicio de la ejecución del programa.  
  
 Si la aplicación ha instalado una función de enlace de volcado llamando a [_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md), cada vez que `_CrtMemDumpAllObjectsSince` vuelca información sobre un tipo de bloque `_CLIENT_BLOCK`, llama también a la función de volcado suministrada por la aplicación. De forma predeterminada, los bloques internos en tiempo de ejecución de C (`_CRT_BLOCK`) no se incluyen en las operaciones de volcado de la memoria. Se puede usar la función [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) para activar el bit `_CRTDBG_CHECK_CRT_DF` de **_crtDbgFlag** de forma que incluya estos bloques. Además, los bloques marcados como liberados u omitidos (**_FREE_BLOCK**, **_IGNORE_BLOCK**) no se incluyen en el volcado de memoria.  
  
 Para obtener más información sobre las funciones de estado del montón y la estructura `_CrtMemState`, consulte [Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para obtener más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de cómo usar `_CrtMemDumpAllObjectsSince`, consulte [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)
