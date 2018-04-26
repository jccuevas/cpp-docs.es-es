---
title: _CrtDumpMemoryLeaks | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
dev_langs:
- C++
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fb0ebfe1017f6315d60528c5f6196131704c5d0f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

Vuelca todos los bloques de memoria del montón de depuración cuando se ha producido una fuga de memoria (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>Valor devuelto

**_CrtDumpMemoryLeaks** devuelve TRUE si se encuentra una pérdida de memoria. De lo contrario, la función devuelve el FALSE.

## <a name="remarks"></a>Comentarios

El **_CrtDumpMemoryLeaks** función determina si se ha producido una pérdida de memoria desde el inicio de la ejecución del programa. Cuando se encuentra una pérdida, la información de encabezado de depuración de todos los objetos del montón se vuelca en un formato legible para usuario. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtDumpMemoryLeaks** se quitan durante el preprocesamiento.

**_CrtDumpMemoryLeaks** se suele denominar al final de la ejecución del programa para comprobar que se ha liberado toda la memoria asignada por la aplicación. Puede llamar a la función automáticamente cuando finaliza el programa activando el **_CRTDBG_LEAK_CHECK_DF** campo de bits de la [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) marca mediante el [_CrtSetDbgFlag](crtsetdbgflag.md)(función).

**_CrtDumpMemoryLeaks** llamadas [_CrtMemCheckpoint](crtmemcheckpoint.md) para obtener el estado actual del montón y, a continuación, examina el estado de bloques que no se han liberado. Cuando se encuentra un bloque no liberado, **_CrtDumpMemoryLeaks** llamadas [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) para volcar la información de todos los objetos asignados en el montón desde el principio de la ejecución del programa.

De forma predeterminada, los bloques de tiempo de ejecución de C internos (**_CRT_BLOCK**) no se incluyen en las operaciones de volcado de memoria. El [_CrtSetDbgFlag](crtsetdbgflag.md) función puede utilizarse para activar el **_CRTDBG_CHECK_CRT_DF** de bits de **_crtDbgFlag** para incluir estos bloques en el proceso de detección de pérdidas.

Para obtener más información sobre las funciones de estado del montón y la **_CrtMemState** estructura, vea [funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar **_CrtDumpMemoryLeaks**, consulte [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
