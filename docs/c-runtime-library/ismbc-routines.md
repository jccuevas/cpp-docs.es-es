---
title: _ismbc (Rutinas)
ms.date: 11/04/2016
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: dd187be93b5df0160686fe765f65c25e14800b75
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748689"
---
# <a name="ismbc-routines"></a>_ismbc (Rutinas)

Cada rutina de **_ismbc** prueba si un carácter multibyte `c` dado cumple una condición determinada.

|||
|-|-|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|
|[_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|

## <a name="remarks"></a>Comentarios

El resultado de la prueba de cada rutina de **_ismbc** depende de la página de códigos multibyte en vigor. Las páginas de códigos multibyte tienen caracteres alfabéticos de un solo byte. De forma predeterminada, la página de códigos multibyte se establece en la página de códigos ANSI predeterminada del sistema obtenida del sistema operativo cuando se inicia el programa. Puede ver o cambiar la página de códigos multibyte en vigor con [_getmbcp](../c-runtime-library/reference/getmbcp.md) o [_setmbcp](../c-runtime-library/reference/setmbcp.md), respectivamente.

El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa.

|Rutina|Condición de prueba|Ejemplo de la página de códigos 932|
|-------------|--------------------|---------------------------|
|[_ismbcalnum, _ismbcalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumérico|Devuelve un valor distinto de cero únicamente si `c` es una representación de un solo byte de una letra inglesa ASCII: Vea los ejemplos de `_ismbcdigit` y `_ismbcalpha`.|
|[_ismbcalpha, _ismbcalpha_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfabético|Devuelve un valor distinto de cero únicamente si `c` es una representación de un solo byte de una letra inglesa ASCII: vea los ejemplos de `_ismbcupper` y `_ismbclower`; o una letra katakana: 0xA6<=`c`<=0xDF.|
|[_ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Dígito|Devuelve un valor distinto de cero únicamente si `c` es una representación de un solo byte de un dígito ASCII: 0x30<=`c`<=0x39.|
|[_ismbcgraph, _ismbcgraph_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Gráfico|Devuelve un valor distinto de cero si y solo si `c` es una representación de un solo byte de cualquier carácter imprimible ASCII o katakana excepto un espacio en blanco ( ). Vea los ejemplos de `_ismbcdigit`, `_ismbcalpha` y `_ismbcpunct`.|
|[_ismbclegal, _ismbclegal_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Carácter multibyte válido|Devuelve un valor distinto de cero si y solo si el primer byte de `c` está dentro de los intervalos 0x81 - 0x9F o 0xE0 - 0xFC, y el segundo byte está dentro de los intervalos 0x40 - 0x7E o 0x80 - FC.|
|[_ismbclower, _ismbclower_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Alfabético en minúscula|Devuelve un valor distinto de cero únicamente si `c` es una representación de un solo byte de una letra inglesa minúscula ASCII: 0x61<=`c`<=0x7A.|
|[_ismbcprint, _ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Carácter imprimible|Devuelve un valor distinto de cero únicamente si `c` es una representación de un solo byte de cualquier carácter imprimible ASCII o katakana, incluso un espacio en blanco ( ): vea los ejemplos de `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha` y `_ismbcpunct`.|
|[_ismbcpunct, _ismbcpunct_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Puntuación|Devuelve un valor distinto de cero si y solo si `c` es una representación de un solo byte de cualquier carácter de puntuación ASCII o katakana.|
|[_ismbcblank, _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|Espacio o tabulación horizontal|Devuelve cero si y solo si `c` es una representación de un solo byte de un carácter de espacio o un carácter de tabulación horizontal: `c`=0x20 o `c`=0x09.|
|[_ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Whitespace|Devuelve un valor distinto de cero si y solo si `c` es un carácter de espacio en blanco: `c`=0x20 o 0x09<=`c`<=0x0D.|
|[_ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Símbolo multibyte|Devuelve un valor distinto de cero si y solo si 0x8141<=`c`<=0x81AC.|
|[_ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Alfabético en mayúscula|Devuelve un valor distinto de cero únicamente si `c` es una representación de un solo byte de una letra inglesa mayúscula ASCII: 0x41<=`c`<=0x5A.|

**Información específica de la página de códigos 932**

Las rutinas siguientes son específicas de la página de códigos 932.

|Rutina|Condición de prueba (solo página de códigos 932)|
|-------------|-------------------------------------------|
|[_ismbchira, _ismbchira_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Hiragana de doble byte: 0x829F<=`c`<=0x82F1.|
|[_ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Katakana de doble byte: 0x8340<=`c`<=0x8396.|
|[_ismbcl0, _ismbcl0_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS no Kanji: 0x8140<=`c`<=0x889E.|
|[_ismbcl1, _ismbcl1_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS de nivel 1: 0x889F<=`c`<=0x9872.|
|[_ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS de nivel 2: 0x989F<=`c`<=0xEA9E.|

`_ismbcl0`, `_ismbcl1` y `_ismbcl2` comprueban que el valor `c` especificado coincide con las condiciones de prueba descritas en la tabla anterior, pero no comprueben que `c` es un carácter multibyte válido. Si el byte inferior está en los intervalos 0x00 - 0x3F, 0x7F, o 0xFD - 0xFF, estas funciones devuelven un valor distinto de cero, lo que indica que el carácter cumple la condición de prueba. Use [_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) para comprobar si el carácter multibyte está definido.

**Información específica de la página de códigos de fin 932**

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../c-runtime-library/character-classification.md)<br/>
[is, isw (rutinas)](../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb (rutinas)](../c-runtime-library/ismbb-routines.md)
