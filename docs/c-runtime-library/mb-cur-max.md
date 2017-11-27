---
title: MB_CUR_MAX | Microsoft Docs
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MB_CUR_MAX
dev_langs: C++
helpviewer_keywords: MB_CUR_MAX constant
ms.assetid: fab22609-c14d-4c19-991c-bd09ff30e604
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3d82463f9041e4c121fc1988f396b2a1854ff338
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="mbcurmax"></a>MB_CUR_MAX

Macro que indica el número máximo de bytes en un carácter multibyte para la configuración regional actual.

## <a name="syntax"></a>Sintaxis

`#include <stdlib.h>`

## <a name="remarks"></a>Comentarios

Contexto: funciones de conversión de caracteres multibyte y anchos de ANSI

El valor de `MB_CUR_MAX` es el número máximo de bytes en un carácter multibyte para la configuración local actual.

## <a name="see-also"></a>Vea también

[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
[&#95;&#95;&#95;mb_cur_max_func, &#95;&#95;&#95;mb_cur_max_l_func, &#95;&#95;p&#95;&#95;&#95;mb_cur_max, &#95;&#95;mb_cur_max](../c-runtime-library/mb-cur-max-func-mb-cur-max-l-func-p-mb-cur-max-mb-cur-max.md)   
[Tipos estándar](../c-runtime-library/standard-types.md)   
[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)   
[Constantes de tipo de datos](../c-runtime-library/data-type-constants.md)   
[Constantes globales](../c-runtime-library/global-constants.md)