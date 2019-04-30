---
title: _free_locale
ms.date: 11/04/2016
apiname:
- _free_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __free_locale
- free_locale
- _free_locale
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
ms.openlocfilehash: 92dc8cd711087e8e797b484d6c7e3c6c3b031b5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333045"
---
# <a name="freelocale"></a>_free_locale

Libera un objeto de configuración regional.

## <a name="syntax"></a>Sintaxis

```C
void _free_locale(
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*locale*<br/>
Objeto de configuración regional que se va a liberar.

## <a name="remarks"></a>Comentarios

El **_free_locale** función se usa para liberar el objeto de configuración regional obtenido de una llamada a **_get_current_locale** o **_create_locale**.

El nombre anterior de esta función, **__free_locale** (con dos caracteres de subrayado iniciales) ha quedado en desuso.

## <a name="requirements"></a>Requisitos

|**Rutina**|Encabezado necesario|
|---------------|---------------------|
|**_free_locale**|\<locale.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
