---
title: _mbccpy, _mbccpy_l
ms.date: 4/2/2020
api_name:
- _mbccpy
- _mbccpy_l
- _o__mbccpy
- _o__mbccpy_l
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
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
helpviewer_keywords:
- _tccpy function
- _tccpy_l function
- tccpy_l function
- tccpy function
- mbccpy function
- _mbccpy_l function
- _mbccpy function
- mbccpy_l function
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
ms.openlocfilehash: 45f93e370e11cf38fc17da3557b21c636fcbc623
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341262"
---
# <a name="_mbccpy-_mbccpy_l"></a>_mbccpy, _mbccpy_l

Copia un carácter multibyte de una cadena en otra. Hay disponibles versiones más seguras de estas funciones; vea [_mbccpy_s, _mbccpy_s_l](mbccpy-s-mbccpy-s-l.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
void _mbccpy(
   unsigned char *dest,
   const unsigned char *src
);
void _mbccpy_l(
   unsigned char *dest,
   const unsigned char *src,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*dest*<br/>
Destino de la copia.

*src*<br/>
Carácter multibyte que se va a copiar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="remarks"></a>Observaciones

La función **_mbccpy** copia un carácter multibyte de *src* a *dest*.

Esta función valida sus parámetros. Si se pasa **_mbccpy** un puntero nulo para *dest* o *src*, se invoca el controlador de parámetros no válidos, como se describe en [validación](../../c-runtime-library/parameter-validation.md)de parámetros . Si la ejecución puede continuar, **errno** se establece **en EINVAL**.

**_mbccpy** utiliza la configuración regional actual para cualquier comportamiento dependiente de la configuración regional. **_mbccpy_l** es idéntica a **_mbccpy** excepto que **_mbccpy_l** utiliza la configuración regional pasada para cualquier comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

**Nota de seguridad** Use una cadena terminada en un valor nulo. El tamaño de la cadena terminada en un valor nulo no debe ser mayor que el del búfer de destino. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer). Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy**|Se asigna a una macro o una función insertada|**_mbccpy**|Se asigna a una macro o una función insertada|
|**_tccpy_l**|N/D|**_mbccpy_l**|N/D|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbccpy**|\<mbctype.h>|
|**_mbccpy_l**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
