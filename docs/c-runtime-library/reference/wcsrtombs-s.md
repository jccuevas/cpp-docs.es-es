---
title: wcsrtombs_s
ms.date: 11/04/2016
apiname:
- wcsrtombs_s
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
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: bd965271a65fa91b427c7af7bbd4173b129e1d8c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188576"
---
# <a name="wcsrtombss"></a>wcsrtombs_s

Convierte una cadena de caracteres anchos en su representación de cadena de caracteres multibyte. Versión de [wcsrtombs](wcsrtombs.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parámetros

*pReturnValue*<br/>
El tamaño en bytes de la cadena convertida, incluido el terminador nulo.

*mbstr*<br/>
Dirección de un búfer para la cadena de caracteres multibyte convertida resultante.

*sizeInBytes*<br/>
El tamaño en bytes de la *mbstr* búfer.

*wcstr*<br/>
Apunta a la cadena de caracteres anchos que se va a convertir.

*count*<br/>
El número máximo de bytes que se almacenará en el *mbstr* búfer, o [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Un puntero a un **mbstate_t** objeto de estado de conversión.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

|Condición de error|Valor devuelto y **errno**|
|---------------------|------------------------------|
|*mbstr* es **NULL** y *sizeInBytes* > 0|**EINVAL**|
|*wcstr* es **NULL**|**EINVAL**|
|El búfer de destino es demasiado pequeño para contener la cadena convertida (a menos que *recuento* es **_TRUNCATE**; vea Comentarios más abajo)|**ERANGE**|

Si se produce alguna de estas condiciones, se invoca la excepción de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve un código de error y establece **errno** como se indica en la tabla.

## <a name="remarks"></a>Comentarios

El **wcsrtombs_s** función convierte una cadena de caracteres anchos que apunta *wcstr* en caracteres multibyte almacenados en el búfer señalado por *mbstr*, mediante el estado de conversión contenido en *mbstate*. La conversión continuará para cada carácter hasta que se cumpla alguna de estas condiciones:

- Se encuentre un carácter ancho nulo

- Se encuentre un carácter ancho que no se pueda convertir

- El número de bytes almacenados en el *mbstr* búfer equals *recuento*.

La cadena de destino siempre termina en nulo (aun en caso de error).

Si *recuento* es el valor especial [_TRUNCATE](../../c-runtime-library/truncate.md), a continuación, **wcsrtombs_s** convierte tanto de la cadena como cabe en el búfer de destino, dejando espacio para un valor null terminador.

Si **wcsrtombs_s** convierte correctamente la cadena de origen, pone el tamaño en bytes de la cadena convertida, incluido el terminador nulo, en  *&#42;pReturnValue* (proporcionado  *pReturnValue* no **NULL**). Esto ocurre incluso si la *mbstr* argumento es **NULL** y proporciona una manera de determinar el tamaño de búfer necesario. Observe que si *mbstr* es **NULL**, *recuento* se omite.

Si **wcsrtombs_s** encuentra un carácter ancho que no se puede convertir en un carácter multibyte, pone -1  *\*pReturnValue*, Establece el búfer de destino en una cadena vacía, establece **errno** a **EILSEQ**y devuelve **EILSEQ**.

Si las secuencias señaladas por *wcstr* y *mbstr* se superponen, el comportamiento de **wcsrtombs_s** es indefinido. **wcsrtombs_s** se ve afectado por la categoría LC_TYPE de la configuración regional actual.

> [!IMPORTANT]
> Asegúrese de que *wcstr* y *mbstr* no se superponen y que *recuento* refleja correctamente el número de caracteres anchos a convertir.

El **wcsrtombs_s** función difiere de [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) por su capacidad de reinicio. El estado de conversión se almacena en *mbstate* en las llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación usaría **wcsrlen** lugar **wcslen**, si una llamada subsiguiente a **wcsrtombs_s** se usaron en lugar de **wcstombs_s**.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Excepciones

El **wcsrtombs_s** función es segura para subprocesos siempre y cuando ninguna función en el subproceso actual llame a **setlocale** mientras se está ejecutando esta función y el *mbstate* es null.

## <a name="example"></a>Ejemplo

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

void main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
