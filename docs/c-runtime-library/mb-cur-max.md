---
title: MB_CUR_MAX
ms.date: 10/18/2017
f1_keywords:
- MB_CUR_MAX
helpviewer_keywords:
- MB_CUR_MAX constant
ms.assetid: fab22609-c14d-4c19-991c-bd09ff30e604
ms.openlocfilehash: 8f89d06f11d5da14389c849814e06b56586b3c69
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746453"
---
# <a name="mbcurmax"></a>MB_CUR_MAX

Macro que indica el número máximo de bytes en un carácter multibyte para la configuración regional actual.

## <a name="syntax"></a>Sintaxis

```
#include <stdlib.h>
```

## <a name="remarks"></a>Comentarios

Contexto: funciones de conversión de caracteres multibyte y anchos de ANSI

El valor de `MB_CUR_MAX` es el número máximo de bytes en un carácter multibyte para la configuración local actual.

## <a name="see-also"></a>Vea también

[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)<br/>
[&#95;&#95;&#95;mb_cur_max_func, &#95;&#95;&#95;mb_cur_max_l_func, &#95;&#95;p&#95;&#95;&#95;mb_cur_max, &#95;&#95;mb_cur_max](../c-runtime-library/mb-cur-max-func-mb-cur-max-l-func-p-mb-cur-max-mb-cur-max.md)<br/>
[Tipos estándar](../c-runtime-library/standard-types.md)<br/>
[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)<br/>
[Constantes de tipo de datos](../c-runtime-library/data-type-constants.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
