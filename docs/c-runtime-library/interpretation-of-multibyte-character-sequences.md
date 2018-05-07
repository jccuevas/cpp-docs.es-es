---
title: Interpretación de secuencias de caracteres de varios bytes | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- c.character.multibyte
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1363d5fd28f7a8c3cbf01c24db028bad38185364
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="interpretation-of-multibyte-character-sequences"></a>Interpretación de secuencias de caracteres de varios bytes

La mayoría de las rutinas de caracteres multibyte de la biblioteca en tiempo de ejecución de Microsoft reconocen secuencias de caracteres multibyte relativas a una página de códigos multibyte. El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa.

## <a name="locale-dependent-multibyte-routines"></a>Rutinas multibyte dependientes de la configuración regional

|Rutina|Usar|
|-------------|---------|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Valida y devuelve el número de bytes del carácter multibyte|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|En el caso de las cadenas de caracteres multibyte: valida cada carácter de la cadena; devuelve la longitud de la cadena. En el caso de las cadenas de caracteres anchos: devuelve la longitud de cadena.|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Convierte la secuencia de caracteres multibyte en la secuencia correspondiente de caracteres anchos|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Convierte el carácter multibyte en el carácter ancho correspondiente|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Convierte la secuencia de caracteres anchos en la secuencia correspondiente de caracteres multibyte|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Convierte el carácter ancho en el carácter multibyte correspondiente|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Convierte el carácter multibyte en un carácter UTF-16 o UTF-32 equivalente|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Convierte el carácter UTF-16 o UTF-32 en un carácter multibyte equivalente|

## <a name="see-also"></a>Vea también

[Internacionalización](../c-runtime-library/internationalization.md)<br/>
 [Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
