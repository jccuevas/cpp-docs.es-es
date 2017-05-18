---
title: "Clasificación de bytes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.types.bytes
dev_langs:
- C++
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 78bc75930f3e7aadd2bf147b9c6565f8c0c87a84
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="byte-classification"></a>Clasificación de bytes
Cada una de estas rutinas prueba un byte especificado de un carácter multibyte para ver si cumple una condición. A menos que se especifique lo contrario, el valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional. Vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  
  
> [!NOTE]
>  Por definición, los caracteres ASCII entre 0 y 127 son un subconjunto de todos los juegos de caracteres multibyte. Por ejemplo, el juego de caracteres katakana japonés contiene caracteres ASCII y no ASCII.  
  
 Las constantes predefinidas de la siguiente tabla se definen en CTYPE.H.  
  
### <a name="multibyte-character-byte-classification-routines"></a>Rutinas de clasificación de bytes de caracteres multibyte  
  
|Rutina|Condición de prueba de byte|  
|-------------|-------------------------|  
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Byte inicial. El resultado de prueba depende del valor de la categoría `LC_CTYPE` de la configuración regional actual.|  
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum &#124;&#124; _ismbbkalnum`|  
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|`isalpha &#124;&#124; _ismbbkalnum`|  
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Igual que `_ismbbprint`, pero `_ismbbgraph` no incluye el carácter de espacio (0x20).|  
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Símbolo de texto no ASCII que no sea de puntuación. Por ejemplo, en la página de códigos 932 únicamente, `_ismbbkalnum` prueba si hay caracteres alfanuméricos katakana.|  
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 - 0xDF), página de códigos 932 únicamente.|  
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Texto no ASCII o signo de puntuación no ASCII. Por ejemplo, solo en la página de códigos 932, `_ismbbkprint` comprueba si hay caracteres o signos de puntuación katakana (intervalo: 0xA1 - 0xDF).|  
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Puntuación no ASCII. Por ejemplo, en la página de códigos 932 únicamente, `_ismbbkpunct` prueba si hay signos de puntuación katakana.|  
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Primer byte de un carácter multibyte. Por ejemplo, en la página de códigos 932 únicamente, los intervalos válidos son 0x81 - 0x9F y 0xE0 - 0xFC.|  
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint &#124;&#124; _ismbbkprint. ismbbprint` incluye el carácter de espacio (0x20).|  
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct &#124;&#124; _ismbbkpunct`|  
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Segundo byte de un carácter multibyte. Por ejemplo, en la página de códigos 932 únicamente, los intervalos válidos son 0x40 - 0x7E y 0x80 - 0xEC.|  
|[_ismbslead, _ismbslead_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Byte inicial (en contexto de cadena).|  
|[ismbstrail, _ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Byte final (en contexto de cadena).|  
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Tipo de valor devuelto del byte, en función del byte anterior.|  
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Tipo de valor devuelto del byte de la cadena.|  
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Realiza el seguimiento del estado de una conversión de caracteres multibyte.|  
  
 La macro `MB_LEN_MAX`, definida en LIMITS.H, se expande a la longitud máxima en bytes que puede tener cualquier carácter multibyte. `MB_CUR_MAX`, definida en STDLIB.H, se expande a la longitud máxima en bytes de cualquier carácter multibyte en la configuración regional actual.  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)
