---
title: EOF, WEOF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- EOF
dev_langs:
- C++
helpviewer_keywords:
- EOF function
- WEOF function
- end of file
ms.assetid: a7150563-cdae-4cdf-9798-ad509990e505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 113ae268b4f97fdd14a3ac1a7fd0397b61ef8eb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065756"
---
# <a name="eof-weof"></a>EOF, WEOF

## <a name="syntax"></a>Sintaxis

```

#include <stdio.h>
```

## <a name="remarks"></a>Comentarios

Una rutina de E/S devuelve EOF al encontrar el final del archivo (o en algunos casos, un error).

WEOF da como resultado el valor devuelto de tipo **wint_t**, que se usa para indicar el final de un flujo amplio o para informar de una condición de error.

## <a name="see-also"></a>Vea también

[putc, putwc](../c-runtime-library/reference/putc-putwc.md)<br/>
[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[fflush](../c-runtime-library/reference/fflush.md)<br/>
[fclose, _fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)<br/>
[_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)<br/>
[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)