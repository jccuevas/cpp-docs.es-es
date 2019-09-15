---
title: _CrtCheckMemory
ms.date: 11/04/2016
api_name:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: 7e458825a81b7032310458ccda52d9299e126a35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938861"
---
# <a name="_crtcheckmemory"></a>_CrtCheckMemory

Confirma la integridad de los bloques de memoria asignados en el montón de depuración (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **_CrtCheckMemory** devuelve true; de lo contrario, la función devuelve FALSE.

## <a name="remarks"></a>Comentarios

La función **_CrtCheckMemory** valida la memoria asignada por el administrador del montón de depuración comprobando el montón base subyacente e inspeccionando cada bloque de memoria. Si se encuentra un error o una incoherencia de memoria en el montón base subyacente, la información de encabezado de depuración o los búferes de sobrescritura, **_CrtCheckMemory** genera un informe de depuración con información que describe la condición de error. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a **_CrtCheckMemory** se quitan durante el preprocesamiento.

El comportamiento de **_CrtCheckMemory** se puede controlar estableciendo los campos de bits de la marca _ [crtdbgflag](../../c-runtime-library/crtdbgflag.md) mediante la función _ [crtsetdbgflag](crtsetdbgflag.md) . Al activar el campo de bits **_CRTDBG_CHECK_ALWAYS_DF** en se produce una llamada a **_CrtCheckMemory** cada vez que se solicita una operación de asignación de memoria. Aunque este método ralentiza la ejecución, es útil para detectar errores rápidamente. Al desactivar el campo de bits **_CRTDBG_ALLOC_MEM_DF** , **_CrtCheckMemory** no comprueba el montón y devuelve inmediatamente **true**.

Dado que esta función devuelve **TRUE** o **FALSE**, se puede pasar a una de las macros [_ASSERT](assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración. En el ejemplo siguiente se genera un error de aserción si se detectan daños en el montón:

```C
_ASSERTE( _CrtCheckMemory( ) );
```

Para obtener más información sobre cómo se puede usar **_CrtCheckMemory** con otras funciones de depuración, consulte [funciones de generación de informes de estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para obtener información general sobre la administración de memoria y el montón de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar **_CrtCheckMemory**, consulte [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
