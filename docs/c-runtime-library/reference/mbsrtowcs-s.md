---
title: mbsrtowcs_s
ms.date: 4/2/2020
api_name:
- mbsrtowcs_s
- _o_mbsrtowcs_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: 62ae534e8080b74ada49cca005811a049055cb65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338899"
---
# <a name="mbsrtowcs_s"></a>mbsrtowcs_s

Convierte una cadena de caracteres multibyte en la configuración regional actual en su representación de cadena de caracteres anchos. Versión de [mbsrtowcs](mbsrtowcs.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t * wcstr,
   size_t sizeInWords,
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
);
template <size_t size>
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t (&wcstr)[size],
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
); // C++ only
```

### <a name="parameters"></a>Parámetros

*pReturnValue*<br/>
El número de caracteres convertidos.

*wcstr*<br/>
Dirección de búfer para almacenar la cadena de caracteres anchos convertida.

*sizeInWords*<br/>
El tamaño de *wcstr* en palabras (caracteres anchos).

*mbstr*<br/>
Puntero indirecto a la ubicación de la cadena de caracteres multibyte a convertir.

*count*<br/>
El número máximo de caracteres anchos que se almacenarán en el búfer *wcstr,* sin incluir el valor nulo de terminación o [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Puntero a un objeto de estado de conversión **mbstate_t.** Si este valor es un puntero nulo, se utiliza un objeto de estado de la conversión interno estático. Dado que el objeto **mbstate_t** interno no es seguro para subprocesos, se recomienda que siempre pase su propio parámetro *mbstate.*

## <a name="return-value"></a>Valor devuelto

Cero si la conversión es correcta, o un código de error en caso de error.

|Condición de error|Valor devuelto y **errno**|
|---------------------|------------------------------|
|*wcstr* es un puntero nulo y *sizeInWords* > 0|**EINVAL**|
|*mbstr* es un puntero nulo|**EINVAL**|
|La cadena a la que apunta indirectamente *mbstr* contiene una secuencia multibyte que no es válida para la configuración regional actual.|**EILSEQ**|
|El búfer de destino es demasiado pequeño para contener la cadena convertida (a menos que *count* sea **_TRUNCATE**; para obtener más información, consulte Comentarios)|**ERANGE**|

Si solo se produce una de estas condiciones, se invoca la excepción de parámetro no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve un código de error y establece **errno** como se indica en la tabla.

## <a name="remarks"></a>Observaciones

La función **mbsrtowcs_s** convierte una cadena de caracteres multibyte señalados indirectamente por *mbstr en caracteres anchos almacenados* en el búfer al que apunta *wcstr*, mediante el estado de conversión contenido en *mbstate*. La conversión continuará para cada carácter hasta que se cumpla alguna de estas condiciones:

- Se encuentra un carácter multibyte nulo

- Se encuentra un carácter multibyte no válido

- El número de caracteres anchos almacenados en el búfer *wcstr* es igual *a count*.

La cadena de destino *wcstr* siempre termina en null, incluso en el caso de un error, a menos que *wcstr* sea un puntero nulo.

Si *count* es el valor especial [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s** convierte la mayor parte de la cadena que caben en el búfer de destino, sin dejar espacio para un terminador nulo.

Si **mbsrtowcs_s** convierte correctamente la cadena de origen, coloca el tamaño en caracteres anchos de la cadena convertida y el terminador nulo en *&#42;pReturnValue*, siempre *que pReturnValue* no sea un puntero nulo. Esto ocurre incluso si el argumento *wcstr* es un puntero nulo y le permite determinar el tamaño de búfer necesario. Tenga en cuenta que si *wcstr* es un puntero nulo, se omite *count.*

Si *wcstr* no es un puntero nulo, al objeto de puntero al que apunta *mbstr* se le asigna un puntero nulo si se detiene la conversión porque se alcanzó un carácter nulo de terminación. De lo contrario, se le asigna la dirección inmediatamente posterior al último carácter multibyte convertido, de haberlo. Esto permite que una llamada de función subsiguiente reinicie la conversión en el punto en que se detuvo esta llamada.

Si *mbstate* es un puntero nulo, se utiliza el objeto estático de estado de conversión **de mbstate_t** interno de la biblioteca. Dado que este objeto estático interno no es seguro para subprocesos, se recomienda pasar su propio valor *mbstate.*

Si **mbsrtowcs_s** encuentra un carácter multibyte que no es válido en la configuración regional actual, coloca -1 en *&#42;pReturnValue*, establece el búfer de destino *wcstr* en una cadena vacía, establece **errno** en **EILSEQ**y devuelve **EILSEQ**.

Si las secuencias señaladas por *mbstr* y *wcstr* se superponen, el comportamiento de **mbsrtowcs_s** es indefinido. **mbsrtowcs_s** se ve afectada por la categoría LC_TYPE de la configuración regional actual.

> [!IMPORTANT]
> Asegúrese de que *wcstr* y *mbstr* no se superpongan y que *el recuento* refleje correctamente el número de caracteres multibyte que se convertirán.

La función **mbsrtowcs_s** difiere de [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md) por su capacidad de reinicio. El estado de conversión se almacena en *mbstate* para las llamadas posteriores a la misma u otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación debe usar **mbsrlen** en lugar de **mbslen**, si se utiliza una llamada posterior a **mbsrtowcs_s** en lugar de **mbstowcs_s**.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla. Las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="exceptions"></a>Excepciones

La función **mbsrtowcs_s** es segura para varios subprocesos si ninguna función del subproceso actual llama a **setlocale** siempre que esta función se esté ejecutando y el argumento *mbstate* no sea un puntero nulo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>Consulte también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
