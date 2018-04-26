---
title: isgraph, iswgraph, _isgraph_l, _iswgraph_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- isgraph
- iswgraph
- _iswgraph_l
- _isgraph_l
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
- _isgraph_l
- _iswgraph_l
- _ismbcgraph_l
- Isgraph
- _istgraph_l
- _istgraph
- iswgraph
dev_langs:
- C++
helpviewer_keywords:
- isgraph function
- _istgraph_l function
- istgraph function
- _isgraph_l function
- iswgraph function
- _iswgraph_l function
- _istgraph function
- _ismbcgraph_l function
ms.assetid: 531a5f34-4302-4d0a-8a4f-b7ea150ad941
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7733a36c840805e3adfc2feea4f9db00e895a5e
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="isgraph-iswgraph-isgraphl-iswgraphl"></a>isgraph, iswgraph, _isgraph_l, _iswgraph_l

Determina si un entero representa un carácter gráfico.

## <a name="syntax"></a>Sintaxis

```C
int isgraph(
   int c
);
int iswgraph(
   wint_t c
);
int _isgraph_l(
   int c,
   _locale_t locale
);
int _iswgraph_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Entero que se va a probar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve un valor distinto de cero si *c* es una representación concreta de un carácter imprimible que no sea un espacio. **isgraph** devuelve un valor distinto de cero si *c* es un carácter imprimible que no sea un espacio. **iswgraph** devuelve un valor distinto de cero si *c* es un carácter ancho imprimible que no sea un espacio de carácter ancho. Cada una de estas rutinas devuelve 0 si *c* no satisface la condición de prueba.

Las versiones de estas funciones que tienen la **_l** sufijo usar la configuración regional que se pasa en lugar de la configuración regional actual de su comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

El comportamiento de **isgraph** y **_isgraph_l** es indefinido si *c* no es EOF o en el intervalo de 0 a 0xFF, incluidos. Cuando se usa una biblioteca de depuración CRT y *c* no es uno de estos valores, las funciones generan una aserción.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istgraph**|**isgraph**|[_ismbcgraph](ismbcgraph-functions.md)|**iswgraph**|
|**_istgraph_l**|**_isgraph_l**|[_ismbcgraph_l](ismbcgraph-functions.md)|**_iswgraph_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isgraph**|\<ctype.h>|
|**iswgraph**|\<ctype.h> o \<wchar.h>|
|**_isgraph_l**|\<ctype.h>|
|**_iswgraph_l**|\<ctype.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
