---
title: _CrtDumpMemoryLeaks
ms.date: 11/04/2016
api_name:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
ms.openlocfilehash: dae93577f5c0c0297606577c05d6b6ef2040c831
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938826"
---
# <a name="_crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

Vuelca todos los bloques de memoria del montón de depuración cuando se ha producido una fuga de memoria (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>Valor devuelto

_ **Crtdumpmemoryleaks** devuelve true si se encuentra una pérdida de memoria. De lo contrario, la función devuelve el FALSE.

## <a name="remarks"></a>Comentarios

La función _ **crtdumpmemoryleaks** determina si se ha producido una fuga de memoria desde el inicio de la ejecución del programa. Cuando se encuentra una pérdida, la información de encabezado de depuración de todos los objetos del montón se vuelca en un formato legible para usuario. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a _ **crtdumpmemoryleaks** se quitan durante el preprocesamiento.

A menudo se llama a _ **crtdumpmemoryleaks** al final de la ejecución del programa para comprobar que se ha liberado toda la memoria asignada por la aplicación. Se puede llamar a la función automáticamente cuando finaliza el programa activando el campo de bits **_CRTDBG_LEAK_CHECK_DF** de la marca _ [crtdbgflag](../../c-runtime-library/crtdbgflag.md) mediante la función _ [crtsetdbgflag](crtsetdbgflag.md) .

_ **Crtdumpmemoryleaks** llama a [_CrtMemCheckpoint](crtmemcheckpoint.md) para obtener el estado actual del montón y, a continuación, examina el estado para detectar bloques que no se han liberado. Cuando se encuentra un bloque no liberado, _ **crtdumpmemoryleaks** llama a [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) para volcar la información de todos los objetos asignados en el montón desde el inicio de la ejecución del programa.

De forma predeterminada, los bloques internos en tiempo de ejecución de C (_**crt_block**) no se incluyen en las operaciones de volcado de memoria. La función _ [crtsetdbgflag](crtsetdbgflag.md) se puede usar para activar el bit **_CRTDBG_CHECK_CRT_DF** de _ **crtdbgflag** para incluir estos bloques en el proceso de detección de pérdidas.

Para obtener más información sobre las funciones de estado del montón y la estructura _ **crtmemstate** , consulte [funciones de generación de informes de estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar _ **crtdumpmemoryleaks**, vea [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
