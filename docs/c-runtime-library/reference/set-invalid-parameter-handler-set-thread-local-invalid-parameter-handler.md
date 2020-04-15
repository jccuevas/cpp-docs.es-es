---
title: _set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler
ms.date: 4/2/2020
api_name:
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
- _o__set_invalid_parameter_handler
- _o__set_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_invalid_parameter_handler
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
ms.openlocfilehash: 0637937d4596d28875c40efec62f79a32f533dcf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337681"
---
# <a name="_set_invalid_parameter_handler-_set_thread_local_invalid_parameter_handler"></a>_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler

Establece una función a la que se llamará cuando CRT detecte un argumento no válido.

## <a name="syntax"></a>Sintaxis

```C
_invalid_parameter_handler _set_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
```

### <a name="parameters"></a>Parámetros

*pNew*<br/>
El puntero de función al nuevo controlador de parámetros no válidos.

## <a name="return-value"></a>Valor devuelto

Puntero al controlador de parámetros no válidos antes de la llamada.

## <a name="remarks"></a>Observaciones

Muchas funciones de tiempo de ejecución de C comprueban la validez de los argumentos pasados. Si se pasa un argumento no válido, la función puede establecer el número de error **errno** o devolver un código de error. En estos casos, también se llama al controlador de parámetros no válidos. El tiempo de ejecución de C proporciona un controlador de parámetros no válidos global predeterminado que finaliza el programa y muestra un mensaje de error en tiempo de ejecución. Puede usar el **_set_invalid_parameter_handler** para establecer su propia función como el controlador de parámetros globales no válidos. El tiempo de ejecución de C también admite un controlador de parámetros no válidos de subproceso local. Si un controlador de parámetros local de subproceso se establece en un subproceso mediante **_set_thread_local_invalid_parameter_handler**, las funciones en tiempo de ejecución de C a las que se llama desde el subproceso usan ese controlador en lugar del controlador global. Solo se puede especificar una función a la vez como controlador global de argumentos no válidos. Solo se puede especificar una función como controlador de argumentos no válidos de subproceso local por cada subproceso, aunque puede haber diferentes subprocesos que tengan diferentes controladores de subproceso local. De esta manera, puede cambiar el controlador usado en una parte del código sin que afecte al comportamiento de otros subprocesos.

Cuando el tiempo de ejecución llama a la función de parámetro no válido, suele significar que se ha producido un error irrecuperable. La función del controlador de parámetros no válidos que proporcione debe guardar todos los datos que pueda contener y luego debe anularse. No debe devolver el control a la función principal, a menos que esté seguro de que el error es recuperable.

La función de controlador de parámetros no válidos debe tener el siguiente prototipo:

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

El argumento *expression* es una representación de cadena amplia de la expresión de argumento que generó el error. El argumento *function* es el nombre de la función CRT que recibió el argumento no válido. El argumento *file* es el nombre del archivo de origen CRT que contiene la función. El argumento *de línea* es el número de línea de ese archivo. Se reserva el último argumento. Todos los parámetros tienen el valor **NULL** a menos que se utilice una versión de depuración de la biblioteca CRT.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_invalid_parameter_handler**, **_set_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib> o \<stdlib.h>|

Las funciones **_set_invalid_parameter_handler** y **_set_thread_local_invalid_parameter_handler** son específicas de Microsoft. Para obtener información sobre la compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa un controlador de errores de parámetros no válidos para imprimir la función que recibió el parámetro no válido, así como el archivo y la línea en los orígenes de CRT. Al usar la biblioteca de depuración de CRT, los errores de parámetros no válidos también generan una aserción, que se deshabilita en este ejemplo mediante [_CrtSetReportMode](crtsetreportmode.md).

```C
// crt_set_invalid_parameter_handler.c
// compile with: /Zi /MTd
#include <stdio.h>
#include <stdlib.h>
#include <crtdbg.h>  // For _CrtSetReportMode

void myInvalidParameterHandler(const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf(L"Invalid parameter detected in function %s."
            L" File: %s Line: %d\n", function, file, line);
   wprintf(L"Expression: %s\n", expression);
   abort();
}

int main( )
{
   char* formatString;

   _invalid_parameter_handler oldHandler, newHandler;
   newHandler = myInvalidParameterHandler;
   oldHandler = _set_invalid_parameter_handler(newHandler);

   // Disable the message box for assertions.
   _CrtSetReportMode(_CRT_ASSERT, 0);

   // Call printf_s with invalid parameters.

   formatString = NULL;
   printf(formatString);
}
```

```Output
Invalid parameter detected in function common_vfprintf. File: minkernel\crts\ucrt\src\appcrt\stdio\output.cpp Line: 32
Expression: format != nullptr
```

## <a name="see-also"></a>Consulte también

[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[Versiones mejoradas de seguridad de las funciones de CRT](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
