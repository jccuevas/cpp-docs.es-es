---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 4/2/2020
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
- _o__invalid_parameter_noinfo
- _o__invalid_parameter_noinfo_noreturn
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CORECRT/_invalid_parameter
- _invalid_parameter
- CORECRT/_invalid_parameter_noinfo
- _invalid_parameter_noinfo
- CORECRT/_invalid_parameter_noinfo_noreturn
- _invalid_parameter_noinfo_noreturn
- CORECRT/_invoke_watson
- _invoke_watson
ms.assetid: a4d6f1fd-ce56-4783-8719-927151a7a814
ms.openlocfilehash: 7138e9cb7381e4d40911054e1473536b6e639e2d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919821"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

Estas funciones se usan en la biblioteca en tiempo de ejecución de C para controlar los parámetros no válidos que se han pasado a las funciones de la biblioteca CRT. El código también puede usar estas funciones para admitir el control predeterminado o personalizable de los parámetros no válidos.

## <a name="syntax"></a>Sintaxis

```C
extern "C" void __cdecl
_invalid_parameter(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);

extern "C" void __cdecl
_invalid_parameter_noinfo(void);

extern "C" __declspec(noreturn) void __cdecl
_invalid_parameter_noinfo_noreturn(void);

extern "C" __declspec(noreturn) void __cdecl
_invoke_watson(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);
```

## <a name="parameters"></a>Parámetros

*expression*<br/>
Una cadena que representa la expresión del parámetro de código fuente que no es válida.

*function_name*<br/>
El nombre de la función que llamó al controlador.

*file_name*<br/>
El archivo de código fuente donde se llamó al controlador.

*line_number*<br/>
El número de línea del código fuente donde se llamó al controlador.

*sector*<br/>
Sin usar.

## <a name="return-value"></a>Valor devuelto

Estas funciones no devuelven ningún valor. Las funciones **_invalid_parameter_noinfo_noreturn** y **_invoke_watson** no vuelven al llamador y, en algunos casos, **_invalid_parameter** y **_invalid_parameter_noinfo** no pueden volver al llamador.

## <a name="remarks"></a>Observaciones

Cuando se pasan parámetros no válidos a las funciones de la biblioteca en tiempo de ejecución de C, las funciones de la biblioteca llaman a un *controlador de parámetros no válidos*, una función que el programador puede especificar para llevar a cabo numerosas operaciones. Por ejemplo, puede notificar el problema al usuario, escribir en un registro, interrumpir un depurador, finalizar el programa o no hacer nada. Si el programador no especifica ninguna función, se llama a un controlador predeterminado, **_invoke_watson**.

De forma predeterminada, cuando se identifica un parámetro no válido en el código de depuración, las funciones de la biblioteca CRT llaman a la función **_invalid_parameter** mediante parámetros detallados. En código que no es de depuración, se llama a la función **_invalid_parameter_noinfo** , que llama a la función **_invalid_parameter** mediante parámetros vacíos. Si la función de biblioteca CRT que no es de depuración requiere la finalización del programa, se llama a la función **_invalid_parameter_noinfo_noreturn** , que llama a la función **_invalid_parameter** mediante parámetros vacíos, seguido de una llamada a la función **_invoke_watson** para forzar la finalización del programa.

La función **_invalid_parameter** comprueba si se ha establecido un controlador de parámetros no válidos definidos por el usuario y, si es así, lo llama. Por ejemplo, si un controlador de subproceso local definido por el usuario se ha establecido mediante una llamada a [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) en el subproceso actual, se llama a este y luego se devuelve la función. En caso contrario, si un controlador global de parámetros no válidos definido por el usuario se ha establecido mediante una llamada a [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), se llama a este y se devuelve la función. De lo contrario, se llama al controlador predeterminado **_invoke_watson** . El comportamiento predeterminado de **_invoke_watson** es finalizar el programa. Los controladores definidos por el usuario pueden finalizar o devolver. Se recomienda que los controladores definidos por el usuario finalicen el programa a menos que la recuperación sea segura.

Cuando se llama al controlador predeterminado **_invoke_watson** , si el procesador admite una operación de [__fastfail](../../intrinsics/fastfail.md) , se invoca mediante un parámetro de **FAST_FAIL_INVALID_ARG** y el proceso finaliza. De lo contrario, se produce una excepción de error rápido, que se puede detectar con un depurador adjunto. Si el proceso puede continuar, finaliza mediante una llamada a la función **TerminateProcess** de Windows mediante un estado de código de excepción de **STATUS_INVALID_CRUNTIME_PARAMETER**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Validación de parámetros](../../c-runtime-library/parameter-validation.md)<br/>
