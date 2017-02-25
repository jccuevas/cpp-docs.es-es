---
title: "Expresiones constantes de C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "expresiones constantes"
  - "expresiones constantes, sintaxis"
  - "expresiones [C++], constante"
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Expresiones constantes de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una expresión constante se evalúa en tiempo de compilación, no en tiempo de ejecución y se puede usar en cualquier lugar en el que se pueda usar una constante.  La expresión constante se debe evaluar como una constante que se encuentre en el intervalo de valores representables para ese tipo.  Los operandos de una expresión constante pueden ser constantes enteras, constantes de caracteres, constantes de punto flotante, constantes de enumeración, conversiones de tipo, expresiones `sizeof` y otras expresiones constantes.  
  
## Sintaxis  
 *constant\-expression*:  
 *conditional\-expression*  
  
 *conditional\-expression*:  
 *logical\-OR\-expression*  
  
 *logical\-OR\-expression* **?**  *expression* **:**  *conditional\-expression*  
  
 *expression*:  
 *assignment\-expression*  
  
 *expression* **,**  *assignment\-expression*  
  
 *assignment\-expression*:  
 *conditional\-expression*  
  
 *unary\-expression assignment\-operator assignment\-expression*  
  
 *assignment\-operator*: uno de  
 **\= \*\= \/\= %\= \+\= –\= \<\<\= \>\>\= &\= ^\= &#124;\=**  
  
 Los elementos no terminales para declarador de struct, enumerador, declarador directo, declarador directo\-abstracto e instrucción etiquetada contienen el elemento no terminal *constant\-expression*.  
  
 Se debe usar una expresión constante entera para especificar el tamaño de un miembro de campo de bits de una estructura, el valor de una constante de enumeración, el tamaño de una matriz o el valor de una constante **case**.  
  
 Las expresiones constantes usadas en las directivas de preprocesador están sujetas a restricciones adicionales.  Por consiguiente, se conocen como “expresiones constantes restringidas”. Una expresión constante restringida no puede contener expresiones `sizeof`, constantes de enumeración, conversiones de tipos a cualquier tipo ni constantes de tipo flotante.  Puede, no obstante, contener la expresión constante especial `defined (`*identifier*`)`.  
  
## Vea también  
 [Operandos y expresiones](../c-language/operands-and-expressions.md)