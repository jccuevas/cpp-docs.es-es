---
title: "Evaluación de tokens | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 72ed41d37222046f6dfa594aedaa30a0bb38756b
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

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
