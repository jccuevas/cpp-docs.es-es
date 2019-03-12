---
title: vprintf (Funciones)
ms.date: 11/04/2016
apilocation:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- vprintf
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
ms.openlocfilehash: c45197c9008c2d0b6a0519d947ca75f55a7960fd
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747851"
---
# <a name="vprintf-functions"></a>vprintf (Funciones)

Cada una de las funciones `vprintf` toma un puntero a una lista de argumentos y, después, aplica formato a los datos determinados y los escribe en un destino concreto. Las funciones se diferencian en la validación de parámetros realizada, si las funciones adoptan cadenas de caracteres de byte único o de caracteres anchos, el destino de salida y la posibilidad de especificar el orden en que se usan los parámetros en la cadena de formato.

|||
|-|-|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|
|[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|
|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|
|[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|

## <a name="remarks"></a>Comentarios

Las funciones `vprintf` son similares a sus funciones equivalentes, como se muestra en la tabla siguiente. Sin embargo, cada función `vprintf` acepta un puntero a una lista de argumentos, mientras que cada una de las funciones equivalentes acepta una lista de argumentos.

Estas funciones aplican formato a los datos para la salida en los destinos como se indica a continuación.

|Función|Función equivalente|Destino de salida|Validación de parámetros|Compatibilidad con parámetros posicionales|
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|consola|Buscar valores Null.|No|
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|consola|Buscar valores Null.|No|
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Secuencia*|Buscar valores Null.|No|
|**vfprintf_p**|[fprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Secuencia*|Buscar valor Null y formato válido.|sí|
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Secuencia*|Buscar valor Null y formato válido.|No|
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Secuencia*|Buscar valores Null.|No|
|**vfwprintf_p**|[fwprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Secuencia*|Buscar valor Null y formato válido.|sí|
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Secuencia*|Buscar valor Null y formato válido.|No|
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Buscar valores Null.|No|
|**vprintf_p**|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Buscar valor Null y formato válido.|sí|
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Buscar valor Null y formato válido.|No|
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Buscar valores Null.|No|
|**vwprintf_p**|[wprintf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Buscar valor Null y formato válido.|sí|
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Buscar valor Null y formato válido.|No|
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|Memoria a la que apunta el *búfer*|Buscar valores Null.|No|
|**vsprintf_p**|[sprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|Memoria a la que apunta el *búfer*|Buscar valor Null y formato válido.|sí|
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Memoria a la que apunta el *búfer*|Buscar valor Null y formato válido.|No|
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|Memoria a la que apunta el *búfer*|Buscar valores Null.|No|
|**vswprintf_p**|[swprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|Memoria a la que apunta el *búfer*|Buscar valor Null y formato válido.|sí|
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Memoria a la que apunta el *búfer*|Buscar valor Null y formato válido.|No|
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|Memoria a la que apunta el *búfer*|Buscar valores Null.|No|
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|Memoria a la que apunta el *búfer*|Buscar valores Null.|No|
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|Memoria a la que apunta el *búfer*|Buscar valores Null.|No|
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|Memoria a la que apunta el *búfer*|Buscar valores Null.|No|

El argumento `argptr` es del tipo `va_list`, que se define en VARARGS.H y STDARG.H. La variable `argptr` debe inicializarse mediante **va_start,** y debe reinicializarse con llamadas posteriores a `va_arg`; `argptr` apunta después al principio de una lista de argumentos que se convierten y transmiten para la salida según las especificaciones correspondientes del argumento *format*. El *formato* tiene la misma forma y función que el argumento *format* de [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Ninguna de estas funciones invoca a `va_end`. Para obtener una descripción más completa de cada función `vprintf`, vea la descripción de su función equivalente, como se muestra en la tabla anterior.

`_vsnprintf` difiere de **vsprintf** en que escribe no más de *recuento* bytes en el *búfer*.

Las versiones de estas funciones con el infijo **w** en el nombre son versiones de caracteres anchos de las funciones correspondientes sin el infijo **w**; en cada una de estas funciones de caracteres fijos, el, *búfer* y el *formato* son cadenas de caracteres anchos. De lo contrario, cada función de caracteres anchos tiene un comportamiento idéntico a su función de SBCS equivalente.

Las versiones de estas funciones con los sufijos **_s** y **_p** son las versiones más seguras. Estas versiones validan las cadenas de formato y generarán una excepción si la cadena de formato no está bien formada (por ejemplo, si se utilizan caracteres de formato no válidos).

Las versiones de estas funciones con el sufijo **_p** proporcionan la capacidad de especificar el orden en el que se sustituyen los argumentos proporcionados en la cadena de formato. Para obtener más información, consulte [printf_p (Parámetros de posición)](../c-runtime-library/printf-p-positional-parameters.md).

En el caso de **vsprintf**, `vswprintf`, `_vsnprintf` y `_vsnwprintf`, si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

> [!IMPORTANT]
>  Asegúrese de que *format* no es una cadena definida por el usuario. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/desktop/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer). Si usa las versiones seguras de estas funciones (con los sufijos **_s** o **_p**), una cadena de formato proporcionada por el usuario podría desencadenar una excepción de parámetro no válido si dicha cadena contiene caracteres de formato no válidos.

## <a name="see-also"></a>Vea también

[E/S de secuencia](../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)
