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
ms.openlocfilehash: baebf5c7b00dc069a1b0f97a9bc5ffb54f856980
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383058"
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