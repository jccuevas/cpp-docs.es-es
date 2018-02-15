---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 258d3e3aa9f005c76b5e4f2b3739ee588cde3f0a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
Estas funciones se usan en la biblioteca en tiempo de ejecución de C para controlar los parámetros no válidos que se han pasado a las funciones de la biblioteca CRT. El código también puede usar estas funciones para admitir el control predeterminado o personalizable de los parámetros no válidos.

## <a name="syntax"></a>Sintaxis
```
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

## <a name="return-value"></a>Valor devuelto
Estas funciones no devuelven ningún valor. Las funciones `_invalid_parameter_noinfo_noreturn` y `_invoke_watson` no vuelven al llamador y, en algunos casos, `_invalid_parameter` y `_invalid_parameter_noinfo` podrían no volver al llamador.

## <a name="parameters"></a>Parámetros
`expression`  
Una cadena que representa la expresión del parámetro de código fuente que no es válida.

`function_name`  
El nombre de la función que llamó al controlador.

`file_name`  
El archivo de código fuente donde se llamó al controlador.

`line_number`  
El número de línea del código fuente donde se llamó al controlador.

`reserved`  
Sin usar.

## <a name="remarks"></a>Comentarios
Cuando se pasan parámetros no válidos a las funciones de la biblioteca en tiempo de ejecución de C, las funciones de la biblioteca llaman a un *controlador de parámetros no válidos*, una función que el programador puede especificar para llevar a cabo numerosas operaciones. Por ejemplo, puede notificar el problema al usuario, escribir en un registro, interrumpir un depurador, finalizar el programa o no hacer nada. Si el programador no especifica ninguna función, se llama a un controlador predeterminado, `_invoke_watson`.

De forma predeterminada, cuando se identifica un parámetro no válido en el código de depuración, las funciones de la biblioteca CRT llaman a la función `_invalid_parameter` mediante parámetros detallados. En el código de no depuración, se llama a la función `_invalid_parameter_noinfo`, que a su vez llama a la función `_invalid_parameter` con parámetros vacíos. Si la función de biblioteca CRT de no depuración no requiere la finalización del programa, se llama a la función `_invalid_parameter_noinfo_noreturn`, que a su vez llama a la función `_invalid_parameter` con parámetros vacíos, seguido de una llamada a la función `_invoke_watson` para forzar la finalización del programa.

La función `_invalid_parameter` comprueba si se estableció un controlador de parámetro no válido definido por el usuario y, si es así, lo llama. Por ejemplo, si un controlador de subproceso local definido por el usuario se ha establecido mediante una llamada a [set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) en el subproceso actual, se llama a este y luego se devuelve la función. En caso contrario, si un controlador global de parámetros no válidos definido por el usuario se ha establecido mediante una llamada a [set_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), se llama a este y se devuelve la función. De lo contrario, se llama al controlador predeterminado `_invoke_watson`. El comportamiento predeterminado de `_invoke_watson` consiste en finalizar el programa. Los controladores definidos por el usuario pueden finalizar o devolver. Se recomienda que los controladores definidos por el usuario finalicen el programa a menos que la recuperación sea segura. 

Cuando se llama al controlador predeterminado `_invoke_watson`, si el procesador admite una operación [__fastfail](../../intrinsics/fastfail.md), se invoca con un parámetro de `FAST_FAIL_INVALID_ARG` y se finaliza el proceso. De lo contrario, se produce una excepción de error rápido, que se puede detectar con un depurador adjunto. Si el proceso puede continuar, finaliza mediante una llamada a la función `TerminateProcess` de Windows con el estado de código de excepción `STATUS_INVALID_CRUNTIME_PARAMETER`. 

## <a name="requirements"></a>Requisitos  
|Función|Encabezado necesario|  
|--------------|------------------|  
|`_invalid_parameter`, `_invalid_parameter_noinfo`, `_invalid_parameter_noinfo_noreturn`, `_invoke_watson`|\<corecrt.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)  
 [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)  
 [Validación de parámetros](../../c-runtime-library/parameter-validation.md)
