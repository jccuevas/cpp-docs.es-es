---
title: Interpretación de secuencias de caracteres de varios bytes
ms.date: 10/22/2019
f1_keywords:
- c.character.multibyte
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
ms.openlocfilehash: 7431f0c63df60414af192ea38103318c775c430d
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811077"
---
# <a name="interpretation-of-multibyte-character-sequences"></a>Interpretación de secuencias de caracteres de varios bytes

La mayoría de las rutinas de caracteres multibyte de la biblioteca en tiempo de ejecución de Microsoft reconocen secuencias de caracteres multibyte relativas a una página de códigos multibyte. El valor de salida se ve afectado por la configuración de la categoría **LC_CTYPE** de la configuración regional. Para obtener más información, vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Las versiones de estas funciones sin el sufijo **_L** usan la configuración regional actual para este comportamiento dependiente de la configuración regional. Las versiones con el sufijo **_L** son idénticas, salvo que usan el parámetro locale en lugar de la configuración regional actual.

## <a name="locale-dependent-multibyte-routines"></a>Rutinas multibyte dependientes de la configuración regional

|Rutina|Usar|
|-------------|---------|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Valida y devuelve el número de bytes del carácter multibyte|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|En el caso de las cadenas de caracteres multibyte: valida cada carácter de la cadena; devuelve la longitud de la cadena. En el caso de las cadenas de caracteres anchos: devuelve la longitud de cadena.|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Convierte la secuencia de caracteres multibyte en la secuencia correspondiente de caracteres anchos|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Convierte el carácter multibyte en el carácter ancho correspondiente|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Convierte la secuencia de caracteres anchos en la secuencia correspondiente de caracteres multibyte|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Convierte el carácter ancho en el carácter multibyte correspondiente|

## <a name="locale-independent-multibyte-routines"></a>Rutinas multibyte independientes de la configuración regional

|Rutina|Usar|
|-------------|---------|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Convierte el carácter UTF-8 multibyte en un carácter UTF-16 o UTF-32 equivalente.|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Convertir el carácter UTF-16 o UTF-32 en un carácter multibyte de UTF-8 equivalente|

## <a name="see-also"></a>Vea también

[Internacionalización](../c-runtime-library/internationalization.md)\
[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)
