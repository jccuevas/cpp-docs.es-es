---
title: "Evaluaci&#243;n de tokens | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tokens, evaluar"
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Evaluaci&#243;n de tokens
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando el compilador interpreta tokens, incluye todos los caracteres posibles en un único token antes de pasar al token siguiente.  Debido a este comportamiento, el compilador no puede interpretar los tokens tal como se pretende cuando no están correctamente separados por espacio en blanco.  Observe la siguiente expresión:  
  
```  
i+++j  
```  
  
 En este ejemplo, el compilador crea primero el operador más largo posible \(`++`\) de los tres signos más y, después, procesa el signo más restante como operador de suma \(`+`\).  Así, la expresión se interpreta como `(i++) + (j)`, no `(i) + (++j)`.  En este caso y otros similares, utilice el espacio en blanco y paréntesis para evitar la ambigüedad y garantizar la evaluación adecuada de la expresión.  
  
 **Específicos de Microsoft**  
  
 El compilador de C trata un carácter CTRL\+Z como un indicador de fin de archivo.  Omite cualquier texto después de CTRL\+Z.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Tokens de C](../c-language/c-tokens.md)