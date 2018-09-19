---
title: Evaluación de tokens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d5c79ac043b2131df7a876f2de63922c45c9ead
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035284"
---
# <a name="evaluation-of-tokens"></a>Evaluación de tokens

Cuando el compilador interpreta tokens, incluye todos los caracteres posibles en un único token antes de pasar al token siguiente. Debido a este comportamiento, el compilador no puede interpretar los tokens tal como se pretende cuando no están correctamente separados por espacio en blanco. Observe la siguiente expresión:

```
i+++j
```

En este ejemplo, el compilador crea primero el operador más largo posible (`++`) de los tres signos más y, después, procesa el signo más restante como operador de suma (`+`). Así, la expresión se interpreta como `(i++) + (j)`, no `(i) + (++j)`. En este caso y otros similares, utilice el espacio en blanco y paréntesis para evitar la ambigüedad y garantizar la evaluación adecuada de la expresión.

**Específicos de Microsoft**

El compilador de C trata un carácter CTRL+Z como un indicador de fin de archivo. Omite cualquier texto después de CTRL+Z.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Tokens de C](../c-language/c-tokens.md)