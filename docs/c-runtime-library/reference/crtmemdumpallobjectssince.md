---
title: _CrtMemDumpAllObjectsSince
ms.date: 11/04/2016
api_name:
- _CrtMemDumpAllObjectsSince
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
ms.openlocfilehash: 9e3793e9b88c593968b108e2801e24476417603c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942364"
---
# <a name="_crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

Vuelca información sobre objetos en el montón desde el inicio de la ejecución del programa o desde un estado del montón especificado (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Puntero al estado del montón desde el que se va a iniciar el volcado o **NULL**.

## <a name="remarks"></a>Comentarios

La función **_CrtMemDumpAllObjectsSince** vuelca la información del encabezado de depuración de los objetos asignados en el montón en un formato legible para el usuario. La aplicación puede usar la información del volcado para realizar el seguimiento de las asignaciones y detectar problemas de memoria. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a **_CrtMemDumpAllObjectsSince** se quitan durante el preprocesamiento.

**_CrtMemDumpAllObjectsSince** usa el valor del parámetro *State* para determinar dónde iniciar la operación de volcado. Para iniciar el volcado desde un estado del montón especificado, el parámetro *State* debe ser un puntero a una estructura _ **crtmemstate** que [_CrtMemCheckpoint](crtmemcheckpoint.md) ha rellenado antes de que se llamara a **_CrtMemDumpAllObjectsSince** . Cuando el *Estado* es **null**, la función inicia el volcado desde el inicio de la ejecución del programa.

Si la aplicación ha instalado una función de enlace de volcado llamando a _ [crtsetdumpclient](crtsetdumpclient.md), cada vez que **_CrtMemDumpAllObjectsSince** vuelca información sobre un tipo de bloque _ **client_block** , llama al volcado proporcionado por la aplicación. también. De forma predeterminada, los bloques internos en tiempo de ejecución de C (_**crt_block**) no se incluyen en las operaciones de volcado de memoria. La función _ [crtsetdbgflag](crtsetdbgflag.md) se puede usar para activar el bit **_CRTDBG_CHECK_CRT_DF** de _ **crtdbgflag** para incluir estos bloques. Además, los bloques marcados como liberados u omitidos ( **_FREE_BLOCK**, **_IGNORE_BLOCK**) no se incluyen en el volcado de memoria.

Para obtener más información sobre las funciones de estado del montón y la estructura _ **crtmemstate** , consulte [funciones de generación de informes de estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

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
