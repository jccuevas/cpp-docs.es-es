---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
apiname:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b0fecd7eefe9ac6a7a479fb12475b2b1c769cf4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405476"
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

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

*expresión* una cadena que representa la expresión de parámetro de código de origen que no es válida.

*nombre_función* el nombre de la función que llama el controlador.

*file_name* el archivo de código fuente donde se llama al controlador.

*line_number* el número de línea en el código fuente donde se llama al controlador.

*reservada* no utilizado.

## <a name="return-value"></a>Valor devuelto

Estas funciones no devuelven ningún valor. El **_invalid_parameter_noinfo_noreturn** y **_invoke_watson** funciones no vuelven al llamador y en algunos casos, **_invalid_parameter** y **_invalid_parameter_noinfo** no puede devolver al llamador.

## <a name="remarks"></a>Comentarios

Cuando se pasan parámetros no válidos a las funciones de la biblioteca en tiempo de ejecución de C, las funciones de la biblioteca llaman a un *controlador de parámetros no válidos*, una función que el programador puede especificar para llevar a cabo numerosas operaciones. Por ejemplo, puede notificar el problema al usuario, escribir en un registro, interrumpir un depurador, finalizar el programa o no hacer nada. Si no se especifica ninguna función por el programador, un controlador predeterminado, **_invoke_watson**, se llama.

De forma predeterminada, cuando se identifica un parámetro no válido en el código de depuración, funciones de la biblioteca CRT llamar a la función **_invalid_parameter** mediante parámetros detallados. En el código no son de depuración, el **_invalid_parameter_noinfo** se llama a función que llama el **_invalid_parameter** función con parámetros vacías. Si la función de biblioteca de CRT de depuración no requiere la finalización del programa, el **_invalid_parameter_noinfo_noreturn** se llama a función que llama el **_invalid_parameter** función vacía los parámetros, seguidos por una llamada a la **_invoke_watson** función para forzar la finalización del programa.

El **_invalid_parameter** función comprueba si se estableció un controlador de parámetros no válidos definidos por el usuario y, si es así, lo llama. Por ejemplo, si un controlador de subproceso local definido por el usuario se ha establecido mediante una llamada a [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) en el subproceso actual, se llama a este y luego se devuelve la función. En caso contrario, si un controlador global de parámetros no válidos definido por el usuario se ha establecido mediante una llamada a [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), se llama a este y se devuelve la función. En caso contrario, el controlador predeterminado **_invoke_watson** se llama. El comportamiento predeterminado de **_invoke_watson** consiste en Finalizar el programa. Los controladores definidos por el usuario pueden finalizar o devolver. Se recomienda que los controladores definidos por el usuario finalicen el programa a menos que la recuperación sea segura.

Cuando el controlador predeterminado **_invoke_watson** se llama, si el procesador admite un [__fastfail](../../intrinsics/fastfail.md) operación, se invoca con un parámetro de **FAST_FAIL_INVALID_ARG** y finaliza el proceso. De lo contrario, se produce una excepción de error rápido, que se puede detectar con un depurador adjunto. Si el proceso puede continuar, se termina por una llamada a las ventanas **TerminateProcess** funcionar con un estado del código de excepción **STATUS_INVALID_CRUNTIME_PARAMETER**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Validación de parámetros](../../c-runtime-library/parameter-validation.md)<br/>
