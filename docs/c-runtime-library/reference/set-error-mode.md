---
title: _set_error_mode
ms.date: 11/04/2016
apiname:
- _set_error_mode
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: 8c95ed45423b791a688f05ea30f48e188826a797
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502315"
---
# <a name="seterrormode"></a>_set_error_mode

Modifica **__error_mode** para determinar una ubicación no predeterminada donde el tiempo de ejecución de C escribe un mensaje de error para un error que podría finalizar el programa.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _set_error_mode(
   int mode_val
);
```

### <a name="parameters"></a>Parámetros

*mode_val*<br/>
Destino de los mensajes de error.

## <a name="return-value"></a>Valor devuelto

Devuelve el valor anterior o -1 si se produce un error.

## <a name="remarks"></a>Comentarios

Controla el receptor de salida de error estableciendo el valor de **__error_mode**. Por ejemplo, puede dirigir la salida a un error estándar o usar el **MessageBox** API.

El *mode_val* parámetro puede establecerse en uno de los valores siguientes.

|Parámetro|Descripción|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|El receptor de errores viene determinada por **__app_type**.|
|**_OUT_TO_STDERR**|El receptor de errores es un error estándar.|
|**_OUT_TO_MSGBOX**|El receptor de errores es un cuadro de mensaje.|
|**_REPORT_ERRMODE**|Informe actual **__error_mode** valor.|

Si se pasa un valor distinto de los de la lista, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **_set_error_mode** establece **errno** a **EINVAL** y devuelve -1.

Cuando se usa con un [assert](assert-macro-assert-wassert.md), **_set_error_mode** muestra la instrucción con errores en el cuadro de diálogo y ofrece la posibilidad de elegir el **omitir** botón para que pueda Continúe ejecutar el programa.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_error_mode**|\<stdlib.h>|

## <a name="example"></a>Ejemplo

```C
// crt_set_error_mode.c
// compile with: /c
#include <stdlib.h>
#include <assert.h>

int main()
{
   _set_error_mode(_OUT_TO_STDERR);
   assert(2+2==5);
}
```

```Output
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Vea también

[assert (macro), _assert, _wassert](assert-macro-assert-wassert.md)<br/>
