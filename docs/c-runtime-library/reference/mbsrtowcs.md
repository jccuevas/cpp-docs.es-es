---
title: mbsrtowcs
ms.date: 4/2/2020
api_name:
- mbsrtowcs
- _o_mbsrtowcs
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: fc9310a95165944b7f516c1f8c48d8d4d1e56117
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915478"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Convierte una cadena de caracteres multibyte en la configuración regional actual en una cadena de caracteres anchos correspondiente, con la capacidad de reinicio en medio de un carácter multibyte. Hay disponible una versión más segura de esta función; vea [mbsrtowcs_s](mbsrtowcs-s.md).

## <a name="syntax"></a>Sintaxis

```C
size_t mbsrtowcs(
   wchar_t *wcstr,
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t mbsrtowcs(
   wchar_t (&wcstr)[size],
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parámetros

*wcstr*<br/>
Dirección para almacenar la cadena de caracteres anchos convertida.

*mbstr*<br/>
Puntero indirecto a la ubicación de la cadena de caracteres multibyte a convertir.

*count*<br/>
Número máximo de caracteres (no bytes) que se van a convertir y almacenar en *wcstr*.

*mbstate*<br/>
Puntero a un objeto de estado de la conversión **mbstate_t** . Si este valor es un puntero nulo, se utiliza un objeto de estado de la conversión interno estático. Dado que el objeto de **mbstate_t** interno no es seguro para subprocesos, se recomienda pasar siempre su propio parámetro *mbstate* .

## <a name="return-value"></a>Valor devuelto

Devuelve el número de caracteres convertidos correctamente, sin incluir el carácter nulo de terminación, de haberlo. Devuelve (size_t) (-1) si se produce un error y establece **errno** en EILSEQ.

## <a name="remarks"></a>Observaciones

La función **mbsrtowcs** convierte una cadena de caracteres multibyte indirectamente señalada por *mbstr*, en caracteres anchos almacenados en el búfer al que apunta *wcstr*, utilizando el estado de conversión contenido en *mbstate*. La conversión continúa para cada carácter hasta que se encuentra un carácter multibyte nulo de terminación, se encuentra una secuencia multibyte que no se corresponde con un carácter válido en la configuración regional actual o hasta que se han convertido los caracteres de *recuento* . Si **mbsrtowcs** detecta el carácter nulo multibyte (' \ 0 ') antes o cuando se produce el *recuento* , lo convierte en un carácter nulo de terminación de 16 bits y se detiene.

Por lo tanto, la cadena de caracteres anchos en *wcstr* está terminada en NULL solo si **mbsrtowcs** encuentra un carácter nulo multibyte durante la conversión. Si las secuencias señaladas por *mbstr* y *wcstr* se superponen, el comportamiento de **mbsrtowcs** es indefinido. **mbsrtowcs** se ve afectado por la categoría LC_TYPE de la configuración regional actual.

La función **mbsrtowcs** difiere de [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) por su reinicio. El estado de la conversión se almacena en *mbstate* para las llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación debe usar **mbsrlen** en lugar de **mbslen**, si se utiliza una llamada subsiguiente a **mbsrtowcs** en lugar de **mbstowcs**.

Si *wcstr* no es un puntero nulo, al objeto de puntero al que apunta *mbstr* se le asigna un puntero nulo si la conversión se detuvo porque se alcanzó un carácter nulo de terminación. De lo contrario, se le asigna la dirección inmediatamente posterior al último carácter multibyte convertido, de haberlo. Esto permite que una llamada de función subsiguiente reinicie la conversión en el punto en que se detuvo esta llamada.

Si el argumento *wcstr* es un puntero nulo, se omite el argumento *Count* y **mbsrtowcs** devuelve el tamaño necesario en caracteres anchos para la cadena de destino. Si *mbstate* es un puntero nulo, la función usa un objeto de estado de conversión **mbstate_t** interno estático no seguro para subprocesos. Si la secuencia de caracteres *mbstr* no tiene una representación de caracteres multibyte correspondiente, se devuelve-1 y **errno** se establece en **EILSEQ**.

Si el puntero NULL de *mbstr* ISA, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve-1.

En C++, esta función tiene una sobrecarga de plantilla que invoca una contrapartida más nueva y segura de la función. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="exceptions"></a>Excepciones

La función **mbsrtowcs** es segura para subprocesos siempre y cuando ninguna función del subproceso actual llame a **setlocale** mientras se esté ejecutando esta función y el argumento *mbstate* no sea un puntero nulo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Consulta también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
