---
title: _mbccpy, _mbccpy_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbccpy
- _mbccpy_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d79ab8362eaa911b7a4aa936d6351aa29f610fa8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="mbccpy-mbccpyl"></a>_mbccpy, _mbccpy_l

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

*dest* destino de copia.

*src* carácter Multibyte que se va a copiar.

*configuración regional* configuración regional que se use.

## <a name="remarks"></a>Comentarios

El **_mbccpy** función copia un carácter multibyte de *src* a *dest*.

Esta función valida sus parámetros. Si **_mbccpy** se pasa un puntero nulo para *dest* o *src*, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL**.

**_mbccpy** usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional. **_mbccpy_l** es idéntico a **_mbccpy** salvo que **_mbccpy_l** usa la configuración regional que se pasa para todo comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

**Nota de seguridad** Use una cadena terminada en nulo. El tamaño de la cadena terminada en un valor nulo no debe ser mayor que el del búfer de destino. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer). Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada.

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

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
