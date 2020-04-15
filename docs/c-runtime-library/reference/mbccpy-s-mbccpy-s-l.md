---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 4/2/2020
api_name:
- _mbccpy_s
- _mbccpy_s_l
- _o__mbccpy_s
- _o__mbccpy_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
ms.openlocfilehash: 08df395c6978c84b3f53ed0b07ce988afd0249f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341233"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s, _mbccpy_s_l

Copia un carácter multibyte de una cadena en otra. Estas versiones de [_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md) incluyen mejoras de seguridad, tal como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _mbccpy_s(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src
);
errno_t _mbccpy_s_l(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src,
   locale_t locale
);
template <size_t size>
errno_t _mbccpy_s(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbccpy_s_l(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*dest*<br/>
Destino de la copia.

*buffSizeInBytes*<br/>
Tamaño del búfer de destino.

*pCopied*<br/>
Se rellena con el número de bytes copiados (1 o 2 si la operación se ejecuta correctamente). Pase **NULL** si no le importa el número.

*src*<br/>
Carácter multibyte que se va a copiar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Si *src* o *dest* es **NULL**, o si se copiarían más de **bytes buffSizeinBytes** en *dest*, se invoca el controlador de parámetros no válidos, como se describe en [Validación](../../c-runtime-library/parameter-validation.md)de parámetros . Si la ejecución puede continuar, las funciones devuelven **EINVAL** y **errno** se establece en **EINVAL**.

## <a name="remarks"></a>Observaciones

La función **_mbccpy_s** copia un carácter multibyte de *src* a *dest*. Si *src* no apunta al byte principal de un carácter multibyte según lo determinado por una llamada implícita a [_ismbblead](ismbblead-ismbblead-l.md), se copia el único byte al que apunta *src.* Si *src* apunta a un byte de cliente potencial pero el siguiente byte es 0 y, por lo tanto, no es válido, 0 se copia en *dest*, **errno** se establece en **EILSEQ**y la función devuelve **EILSEQ**.

**_mbccpy_s** no anexa un terminador nulo; sin embargo, si *src* apunta a un carácter nulo, ese null se copia en *dest* (esto es sólo una copia normal de un solo byte).

El valor de *pCopied* se rellena con el número de bytes copiados. Los valores posibles son 1 y 2 si la operación es correcta. Si se pasa **NULL,** se omite este parámetro.

|*src*|copiado a *dest*|*pCopied*|Valor devuelto|
|-----------|----------------------|---------------|------------------|
|byte no inicial|byte no inicial|1|0|
|0|0|1|0|
|byte inicial seguido por un valor distinto de 0|byte inicial seguido por un valor distinto de 0|2|0|
|byte inicial seguido por 0|0|1|**EILSEQ**|

Observe que la segunda fila simplemente es un caso especial de la primera. Tenga en cuenta también que la tabla asume *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s** utiliza la configuración regional actual para cualquier comportamiento dependiente de la configuración regional. **_mbccpy_s_l** es idéntica a **_mbccpy_s** excepto que **_mbccpy_s_l** utiliza la configuración regional pasada para cualquier comportamiento dependiente de la configuración regional.

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|Se asigna a una macro o una función insertada.|**_mbccpy_s**|Se asigna a una macro o una función insertada.|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
