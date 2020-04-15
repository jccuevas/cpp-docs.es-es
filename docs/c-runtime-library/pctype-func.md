---
title: __pctype_func
ms.date: 4/2/2020
api_name:
- __pctype_func
- _o___pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: 78562a29c89abe5b649444ae9223cf219488e009
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349196"
---
# <a name="__pctype_func"></a>__pctype_func

Recupera un puntero a una matriz de información de clasificación de caracteres.

## <a name="syntax"></a>Sintaxis

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>Valor devuelto

Puntero a una matriz de información de clasificación de caracteres.

## <a name="remarks"></a>Observaciones

La información de la tabla de clasificación de caracteres solo es para uso interno y sirve para diversas funciones que clasifican los caracteres de tipo `char`. Para obtener más información, consulte la sección `Remarks` de [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>Consulte también

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
