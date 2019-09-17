---
title: _ismbb (Rutinas)
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbb
- ismbb
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
ms.openlocfilehash: 374c78ca222f9c63f6b37f26d4cf3a00f48f845e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944526"
---
# <a name="_ismbb-routines"></a>_ismbb (Rutinas)

Prueba si el valor entero `c` dado cumple una determinada condición, utilizando la configuración regional actual o una categoría de estado de conversión LC_CTYPE especificada.

|||
|-|-|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|
|[_ismbbblank, _ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|

## <a name="remarks"></a>Comentarios

Todas las rutinas de la familia de `_ismbb` prueban si el valor entero `c` dado cumple una determinada condición. El resultado de la prueba depende de la página de códigos multibyte que esté en vigor. De forma predeterminada, la página de códigos multibyte se establece en la página de códigos ANSI obtenida del sistema operativo cuando se inicia el programa. Puede usar [_getmbcp](../c-runtime-library/reference/getmbcp.md) para consultar qué página de códigos multibyte está en vigor, o [_setmbcp](../c-runtime-library/reference/setmbcp.md) para cambiarla.

El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional. Para obtener más información, vea [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones que tienen el sufijo **_l** son idénticas, salvo que usan el parámetro de configuración regional que se pasa.

Las rutinas de la familia de `_ismbb` prueban el entero `c` dado como se indica a continuación.

|Rutina|Condición de prueba de byte|
|-------------|-------------------------|
|[_ismbbalnum](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbalpha](reference/ismbbalpha-ismbbalpha-l.md)|`isalpha` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|
|[_ismbbgraph](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Igual que `_ismbbprint`, pero `_ismbbgraph` no incluye el carácter de espacio (0x20).|
|[_ismbbkalnum](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Símbolo de texto no ASCII que no sea de puntuación. Por ejemplo, en la página de códigos 932 únicamente, `_ismbbkalnum` prueba si hay caracteres alfanuméricos katakana.|
|[_ismbbkana](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 - 0xDF). Específico de la página de códigos 932.|
|[_ismbbkprint](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Texto no ASCII o signo de puntuación no ASCII. Por ejemplo, solo en la página de códigos 932, `_ismbbkprint` comprueba si hay caracteres alfanuméricos o signos de puntuación katakana (intervalo: 0xA1 - 0xDF).|
|[_ismbbkpunct](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Puntuación no ASCII. Por ejemplo, en la página de códigos 932 únicamente, `_ismbbkpunct` prueba si hay signos de puntuación katakana.|
|[_ismbblead](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Primer byte de un carácter multibyte. Por ejemplo, en la página de códigos 932 únicamente, los intervalos válidos son 0x81 - 0x9F y 0xE0 - 0xFC.|
|[_ismbbprint](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint** incluye el carácter de espacio (0x20).|
|[_ismbbpunct](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|
|[_ismbbtrail](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Segundo byte de un carácter multibyte. Por ejemplo, en la página de códigos 932 únicamente, los intervalos válidos son 0x40 - 0x7E y 0x80 - 0xEC.|

En la tabla siguiente se muestran los valores ORed que conforman las condiciones de prueba para estas rutinas. Las constantes de manifiesto `_BLANK`, `_DIGIT`, `_LOWER`, `_PUNCT`y `_UPPER` se definen en Ctype.h.

|Rutina|_BLANK|_DIGIT|LOWER|_PUNCT|UPPER|No<br /><br /> ASCII<br /><br /> texto|No<br /><br /> ASCII<br /><br /> punct|
|-------------|-------------|-------------|-----------|-------------|-----------|------------------------------|-------------------------------|
|`_ismbbalnum`|—|x|x|—|x|x|—|
|`_ismbbalpha`|—|—|x|—|x|x|—|
|`_ismbbblank`|x|—|—|—|—|—|—|
|`_ismbbgraph`|—|x|x|x|x|x|x|
|`_ismbbkalnum`|—|—|—|—|—|x|—|
|`_ismbbkprint`|—|—|—|—|—|x|x|
|`_ismbbkpunct`|—|—|—|—|—|—|x|
|`_ismbbprint`|x|x|x|x|x|x|x|
|`_ismbbpunct`|—|—|—|x|—|—|x|

Las rutinas de `_ismbb` se implementan como funciones y como macros. Para obtener más información sobre cómo elegir una implementación, vea [Recomendaciones para elegir entre funciones y macros](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="see-also"></a>Vea también

[Clasificación de bytes](../c-runtime-library/byte-classification.md)<br/>
[is, isw (rutinas)](../c-runtime-library/is-isw-routines.md)<br/>
[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)<br/>
[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)
