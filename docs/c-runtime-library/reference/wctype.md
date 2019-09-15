---
title: wctype
ms.date: 11/04/2016
api_name:
- wctype
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
ms.openlocfilehash: f77082bbcc5f3cd9d82fb40993c3ac678e7e7ba2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957801"
---
# <a name="wctype"></a>wctype

Determina una regla de clasificación para códigos de caracteres anchos.

## <a name="syntax"></a>Sintaxis

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>Parámetros

*propiedad*<br/>
Cadena de propiedad.

## <a name="return-value"></a>Valor devuelto

Si la categoría **LC_CTYPE** de la configuración regional actual no define una regla de clasificación cuyo nombre coincida con la *propiedad*de cadena de propiedad, la función devuelve cero. De lo contrario, devuelve un valor distinto de cero adecuado como segundo argumento de una llamada subsiguiente a [towctrans](towctrans.md).

## <a name="remarks"></a>Comentarios

La función determina una regla de clasificación para códigos de caracteres anchos. Los siguientes pares de llamadas tienen el mismo comportamiento en todas las configuraciones regionales (aunque una implementación puede definir reglas de clasificación adicionales incluso en la configuración regional "C"):

|Función|Igual que|
|--------------|-------------|
|iswalnum(c)|iswctype(c, wctype( "alnum" ) )|
|iswalpha (c)|iswctype(c, wctype( "alpha" ) )|
|iswcntrl (c)|iswctype(c, wctype( "cntrl" ) )|
|iswdigit (c)|iswctype(c, wctype( "digit" ) )|
|iswgraph (c)|iswctype (c, wctype ("Grafo"))|
|iswlower (c)|iswctype (c, wctype ("Lower"))|
|iswprint (c)|iswctype (c, wctype ("Print"))|
|iswpunct (c)|iswctype (c, wctype ("punct"))|
|iswspace (c)|iswctype (c, wctype ("Space"))|
|iswupper (c)|iswctype (c, wctype ("Upper"))|
|iswxdigit(c)|iswctype(c, wctype( "xdigit" ) )|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
