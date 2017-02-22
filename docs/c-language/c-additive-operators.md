---
title: "Operadores de adici&#243;n de C | Microsoft Docs"
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
  - "+ (operador), operadores de adición"
  - "operadores de adición"
  - "operadores aritméticos [C++], operadores de adición"
  - "operadores [C], suma"
  - "conversiones aritméticas habituales"
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Operadores de adici&#243;n de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los operadores aditivos realizan la suma \(**\+**\) y la resta \(**–**\).  
  
## Sintaxis  
 *additive\-expression*:  
 *multiplicative\-expression*  
  
 *additive\-expression*  **\+**  *multiplicative\-expression*  
  
 *additive\-expression*  **–**  *multiplicative\-expression*  
  
> [!NOTE]
>  Aunque la sintaxis de *additive\-expression* incluye la *multiplicative\-expression*, no implica que se necesiten expresiones que utilicen la multiplicación.  Vea la sintaxis de *multiplicative\-expression*, *cast\-expression* y *unary\-expression* en el [Resumen de la sintaxis del lenguaje C](../c-language/c-language-syntax-summary.md).  
  
 Los operandos pueden ser valores enteros o de punto flotante.  Algunas operaciones aditivas también se pueden realizar sobre valores de puntero, como se explica en la descripción de cada operador.  
  
 Los operadores aditivos realizan las conversiones aritméticas habituales sobre operandos enteros y de punto flotante.  El tipo del resultado es el tipo de los operandos después de la conversión.  Como las conversiones realizadas por los operadores aditivos no proporcionan condiciones de desbordamiento o subdesbordamiento, la información puede perderse si el resultado de una operación aditiva no se puede representar en el tipo de los operandos después de la conversión.  
  
## Vea también  
 [Operadores de adición: \+ y \-](../cpp/additive-operators-plus-and.md)