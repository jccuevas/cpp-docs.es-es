---
title: _CrtMemDumpAllObjectsSince | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: 30d502daad881417035a10b0a7ef3f4efcc41b4f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

Vuelca información sobre objetos en el montón desde el inicio de la ejecución del programa o desde un estado del montón especificado (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parámetros

*estado* puntero al estado del montón a iniciar el volcado desde o **NULL**.

## <a name="remarks"></a>Comentarios

El **_CrtMemDumpAllObjectsSince** función vuelca la información de encabezado de depuración de objetos asignados en el montón en un formato legible para el usuario. La aplicación puede usar la información del volcado para realizar el seguimiento de las asignaciones y detectar problemas de memoria. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtMemDumpAllObjectsSince** se quitan durante el preprocesamiento.

**_CrtMemDumpAllObjectsSince** utiliza el valor de la *estado* parámetro para determinar dónde iniciar la operación de volcado de memoria. Para iniciar el volcado desde un estado del montón especificado, el *estado* parámetro debe ser un puntero a un **_CrtMemState** estructura que ha sido rellenada por [_CrtMemCheckpoint](crtmemcheckpoint.md) antes de **_CrtMemDumpAllObjectsSince** se llamó. Cuando *estado* es **NULL**, la función empieza el volcado desde el principio de la ejecución del programa.

Si la aplicación ha instalado una función de enlace de volcado de memoria mediante una llamada a [_CrtSetDumpClient](crtsetdumpclient.md), a continuación, cada vez que **_CrtMemDumpAllObjectsSince** vuelca información sobre un **_CLIENT_BLOCK** tipo de bloque, llama a la función de volcado proporcionada por la aplicación también. De forma predeterminada, los bloques de tiempo de ejecución de C internos (**_CRT_BLOCK**) no se incluyen en las operaciones de volcado de memoria. El [_CrtSetDbgFlag](crtsetdbgflag.md) función puede utilizarse para activar el **_CRTDBG_CHECK_CRT_DF** de bits de **_crtDbgFlag** para incluir estos bloques. Además, los bloques marcados como liberados u omitidos (**_FREE_BLOCK**, **_IGNORE_BLOCK**) no se incluyen en el volcado de memoria.

Para obtener más información sobre las funciones de estado del montón y la **_CrtMemState** estructura, vea [funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar **_CrtMemDumpAllObjectsSince**, consulte [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
