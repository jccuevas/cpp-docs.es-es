---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 11/04/2016
api_name:
- _mbccpy_s
- _mbccpy_s_l
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
ms.openlocfilehash: 26fad83c5b7847e0050fe490cad30e0643aefd74
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952632"
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
Se rellena con el número de bytes copiados (1 o 2 si la operación se ejecuta correctamente). Pase **null** si no le importa el número.

*src*<br/>
Carácter multibyte que se va a copiar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Si *src* o *dest* es **null**, o si se copian más de **buffSizeinBytes** bytes en *dest*, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven **EINVAL** y **errno** se establece en **EINVAL**.

## <a name="remarks"></a>Comentarios

La función **_mbccpy_s** copia un carácter multibyte de *src* a *dest*. Si *src* no apunta al byte inicial de un carácter multibyte según lo determinado por una llamada implícita a [_ismbblead](ismbblead-ismbblead-l.md), se copia el byte único al *que apunta.* Si *src* apunta a un byte inicial pero el siguiente byte es 0 y, por tanto, es no válido, se copia 0 en *dest*, **errno** se establece en **EILSEQ**y la función devuelve **EILSEQ**.

**_mbccpy_s** no anexa un terminador nulo; sin embargo, si *src* apunta a un carácter nulo, ese valor NULL se copia en *dest* (esto es simplemente una copia normal de un solo byte).

El valor de *pCopied* se rellena con el número de bytes copiados. Los valores posibles son 1 y 2 si la operación es correcta. Si se pasa **null** , se omite este parámetro.

|*src*|copiado en el *destino*|*pCopied*|Valor devuelto|
|-----------|----------------------|---------------|------------------|
|byte no inicial|byte no inicial|1|0|
|0|0|1|0|
|byte inicial seguido por un valor distinto de 0|byte inicial seguido por un valor distinto de 0|2|0|
|byte inicial seguido por 0|0|1|**EILSEQ**|

Observe que la segunda fila simplemente es un caso especial de la primera. Tenga en cuenta también que la tabla presupone *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s** usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional. **_mbccpy_s_l** es idéntico a **_mbccpy_s** , salvo que **_mbccpy_s_l** usa la configuración regional que se pasa para cualquier comportamiento dependiente de la configuración regional.

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulte [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|Se asigna a una macro o una función insertada.|**_mbccpy_s**|Se asigna a una macro o una función insertada.|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
