---
title: _free_locale
ms.date: 4/2/2020
api_name:
- _free_locale
- _o__free_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 8dbc424c00464966605cce5c44118b88eb5335d3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920437"
---
# <a name="_free_locale"></a>_free_locale

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

## <a name="remarks"></a>Observaciones

La función **_free_locale** se usa para liberar el objeto de configuración regional Obtenido de una llamada a **_get_current_locale** o **_create_locale**.

El nombre anterior de esta función, **__free_locale** (con dos subrayados iniciales) ha quedado en desuso.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|**Habitualmente**|Encabezado necesario|
|---------------|---------------------|
|**_free_locale**|\<locale.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
