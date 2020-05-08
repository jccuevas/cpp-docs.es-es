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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: 67447823b0322e647784cdbe0f3f7228e1c5fb34
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919245"
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

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>Consulta también

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
