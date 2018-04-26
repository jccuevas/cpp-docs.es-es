---
title: wctype | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- wctype
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
apitype: DLLExport
f1_keywords:
- wctype
dev_langs:
- C++
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbad04d3c56015ddea10a058ae8b262d7f94d40f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

Si el **LC_CTYPE** categoría de la configuración regional actual no define una regla de clasificación cuyo nombre coincide con la cadena de propiedad *propiedad*, la función devuelve cero. De lo contrario, devuelve un valor distinto de cero adecuado como segundo argumento de una llamada subsiguiente a [towctrans](towctrans.md).

## <a name="remarks"></a>Comentarios

La función determina una regla de clasificación para códigos de caracteres anchos. Los siguientes pares de llamadas tienen el mismo comportamiento en todas las configuraciones regionales (aunque una implementación puede definir reglas de clasificación adicionales incluso en la configuración regional "C"):

|Función|Igual que|
|--------------|-------------|
|iswalnum(c)|iswctype (c, wctype ("alnum"))|
|iswalpha(c)|iswctype (c, wctype ("alfa"))|
|iswcntrl(c)|iswctype (c, wctype ("CTRL"))|
|iswdigit(c)|iswctype (c, wctype ("dígitos"))|
|iswgraph(c)|iswctype (c, wctype ("gráfico"))|
|iswlower(c)|iswctype (c, wctype ("menor"))|
|iswprint(c)|iswctype (c, wctype ("print"))|
|iswpunct(c)|iswctype (c, wctype ("puntuación"))|
|iswspace(c)|iswctype (c, wctype ("espacio"))|
|iswupper(c)|iswctype (c, wctype ("superior"))|
|iswxdigit(c)|iswctype (c, wctype ("xdigit"))|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
