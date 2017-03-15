---
title: "Sobrecargar operadores unarios | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operadores de incremento, sobrecargados"
  - "operadores [C++], unarios"
  - "más (operador)"
  - "sobrecarga de operador de desreferenciación de puntero"
  - "operadores unarios redefinibles"
  - "operadores unarios"
  - "operadores unarios, minus"
  - "operadores unarios, plus"
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Sobrecargar operadores unarios
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los operadores unarios que se pueden sobrecargar son los siguientes:  
  
1.  `!` \([operador NOT lógico](../cpp/logical-negation-operator-exclpt.md)\)  
  
2.  `&` \([dirección de](../cpp/address-of-operator-amp.md)\)  
  
3.  `~` \([complemento a uno](../cpp/one-s-complement-operator-tilde.md)\)  
  
4.  `*` \([desreferencia de puntero](../cpp/indirection-operator-star.md)\)  
  
5.  `+` \([unario más](../cpp/additive-operators-plus-and.md)\)  
  
6.  `-` \([negación unaria](../cpp/additive-operators-plus-and.md)\)  
  
7.  `++` \([incremento](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)\)  
  
8.  `--` \([decremento](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)\)  
  
9. operadores de conversión  
  
 Los operadores de incremento y decremento de postfijo \(`++` y **––**\) se tratan por separado en [Incremento y decremento](../cpp/increment-and-decrement-operator-overloading-cpp.md).  
  
 Los operadores de conversión también se describen en un tema independiente; consulte [Conversiones](../cpp/user-defined-type-conversions-cpp.md).  
  
 Las reglas siguientes son ciertas para todos los demás operadores unarios.  Para declarar una función de operador unario como miembro no estático, debe declararla de la forma siguiente:  
  
 `ret-type operator` `op` `()`  
  
 donde `ret-type` es el tipo de valor devuelto y `op` es uno de los operadores enumerados en la tabla anterior.  
  
 Para declarar una función de operador unario como función global, debe declararla de la forma siguiente:  
  
 `ret-type operator` `op` \(`arg` \)  
  
 donde `ret-type` y `op` son tal y como se describen para las funciones de operador de miembro y `arg` es un argumento de tipo de clase en el que se va a operar.  
  
> [!NOTE]
>  No hay restricciones en los tipos de valor devuelto de los operadores unarios.  Por ejemplo, tiene sentido que el operador NOT lógico \(`!`\) devuelva un valor entero, pero esto no siempre sucede así.  
  
## Vea también  
 [Sobrecarga de operadores](../cpp/operator-overloading.md)