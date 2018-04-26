---
title: mbsrtowcs_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- mbsrtowcs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsrtowcs_s
dev_langs:
- C++
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc125521b7db7537ecbbf3fe3c42ec6b8b8e1ada
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s

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
El número máximo de caracteres anchos para almacenar en la *wcstr* búfer, sin incluir el carácter nulo de terminación o [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Un puntero a un **mbstate_t** objeto de estado de conversión. Si este valor es un puntero nulo, se utiliza un objeto de estado de la conversión interno estático. Dado que el fax interno **mbstate_t** objeto no es seguro para subprocesos, se recomienda pasar siempre su propio *mbstate* parámetro.

## <a name="return-value"></a>Valor devuelto

Cero si la conversión es correcta, o un código de error en caso de error.

|Condición de error|Valor devuelto y **errno**|
|---------------------|------------------------------|
|*wcstr* es un puntero nulo y *sizeInWords* > 0|**EINVAL**|
|*mbstr* es un puntero nulo|**EINVAL**|
|La cadena señalada indirectamente por *mbstr* contiene una secuencia multibyte que no es válida para la configuración regional actual.|**EILSEQ**|
|El búfer de destino es demasiado pequeño para contener la cadena convertida (a menos que *recuento* es **_TRUNCATE**; para obtener más información, vea la sección Comentarios)|**ERANGE**|

Si solo se produce una de estas condiciones, se invoca la excepción de parámetro no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve un código de error y establece **errno** como se indica en la tabla.

## <a name="remarks"></a>Comentarios

El **mbsrtowcs_s** función convierte una cadena de caracteres multibyte indirectamente señalada por *mbstr* en caracteres anchos almacenados en el búfer señalado por *wcstr*, utilizando el estado de conversión contenido en *mbstate*. La conversión continuará para cada carácter hasta que se cumpla alguna de estas condiciones:

- Se encuentra un carácter multibyte nulo

- Se encuentra un carácter multibyte no válido

- El número de caracteres anchos almacenados en el *wcstr* almacenar en búfer es igual a *recuento*.

La cadena de destino *wcstr* siempre está terminada en null, incluso si se produce un error, a menos que *wcstr* es un puntero nulo.

Si *recuento* es el valor especial [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s** convierte tanto de la cadena como quepan en el búfer de destino, dejando espacio para un valor null terminador.

Si **mbsrtowcs_s** convierte correctamente la cadena de origen, coloca el tamaño en caracteres anchos de la cadena convertida y el terminador nulo en  *&#42;pReturnValue*, suministrado  *pReturnValue* no es un puntero nulo. Esto ocurre incluso si la *wcstr* argumento es un puntero nulo y le permite determinar el tamaño de búfer necesario. Tenga en cuenta que si *wcstr* es un puntero nulo, *recuento* se omite.

Si *wcstr* no es un puntero nulo, el objeto de puntero señalado por *mbstr* se le asigna un puntero null si la conversión se detuvo porque se alcanzó un carácter nulo de terminación. De lo contrario, se le asigna la dirección inmediatamente posterior al último carácter multibyte convertido, de haberlo. Esto permite que una llamada de función subsiguiente reinicie la conversión en el punto en que se detuvo esta llamada.

Si *mbstate* es un puntero nulo, la biblioteca interna **mbstate_t** se usa el objeto estático de estado de conversión. Dado que este objeto estático interno no es seguro para subprocesos, se recomienda pasar siempre su propio *mbstate* valor.

Si **mbsrtowcs_s** encuentra un carácter multibyte que no es válido en la configuración regional actual, pone -1  *&#42;pReturnValue*, Establece el búfer de destino *wcstr* en una cadena vacía, establece **errno** a **EILSEQ**y devuelve **EILSEQ**.

Si las secuencias señaladas por *mbstr* y *wcstr* se superponen, el comportamiento de **mbsrtowcs_s** no está definido. **mbsrtowcs_s** se ve afectado por la categoría LC_TYPE de la configuración regional actual.

> [!IMPORTANT]
> Asegúrese de que *wcstr* y *mbstr* no se superponen y que *recuento* refleja correctamente el número de caracteres multibyte a convertir.

El **mbsrtowcs_s** función difiere de [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md) por su capacidad de reinicio. El estado de la conversión se almacena en *mbstate* para llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación debe utilizar **mbsrlen** en lugar de **mbslen**, si una llamada subsiguiente a **mbsrtowcs_s** se utiliza en lugar de **mbstowcs_s**.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla. Las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Excepciones

El **mbsrtowcs_s** función es segura para subprocesos si ninguna función en el proceso actual llama **setlocale** siempre y cuando se ejecute esta función y la *mbstate* argumento es no es un puntero nulo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
