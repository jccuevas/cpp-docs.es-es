---
title: __pctype_func
ms.date: 11/04/2016
apiname:
- __pctype_func
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: fc0f4b0be80534744beda1fe7595293ceb002924
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444231"
---
# <a name="pctypefunc"></a>__pctype_func

Recupera un puntero a una matriz de información de clasificación de caracteres.

## <a name="syntax"></a>Sintaxis

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>Valor devuelto

Puntero a una matriz de información de clasificación de caracteres.

## <a name="remarks"></a>Comentarios

La información de la tabla de clasificación de caracteres solo es para uso interno y sirve para diversas funciones que clasifican los caracteres de tipo `char`. Para obtener más información, consulte la sección `Remarks` de [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>Vea también

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)