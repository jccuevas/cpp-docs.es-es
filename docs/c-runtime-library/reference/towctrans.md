---
title: towctrans
ms.date: 11/04/2016
apiname:
- towctrans
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- towctrans
helpviewer_keywords:
- towctrans function
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
ms.openlocfilehash: b814c65d2f5d0bb18b19d97a539d79dd6df8a1c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269168"
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

El carácter *c*, después **towctrans** utiliza la regla de transformación de *categoría*.

## <a name="remarks"></a>Comentarios

El valor de *categoría* debe haber sido devuelto por una llamada anterior correcta a [wctrans](wctrans.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**towctrans**|\<wctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte **wctrans** para obtener un ejemplo que usa **towctrans**.

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
