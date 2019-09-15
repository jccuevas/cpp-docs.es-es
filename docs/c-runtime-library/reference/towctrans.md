---
title: towctrans
ms.date: 11/04/2016
api_name:
- towctrans
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- towctrans
helpviewer_keywords:
- towctrans function
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
ms.openlocfilehash: d63fc343647cd0f949f282e2a64d4a0636e62bd7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957422"
---
# <a name="towctrans"></a>towctrans

Transforma un carácter.

## <a name="syntax"></a>Sintaxis

```C
wint_t towctrans(
   wint_t c,
   wctrans_t category
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Carácter que quiere transformar.

*category*<br/>
Identificador que contiene el valor devuelto de [wctrans](wctrans.md).

## <a name="return-value"></a>Valor devuelto

El carácter *c*, después de que **towctrans** usó la regla de transformación en la *categoría*.

## <a name="remarks"></a>Comentarios

El valor de *Category* debe haber sido devuelto por una llamada correcta anterior a [wctrans](wctrans.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**towctrans**|\<wctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea **wctrans** para obtener un ejemplo que usa **towctrans**.

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
