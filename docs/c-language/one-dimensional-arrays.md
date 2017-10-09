---
title: Matrices unidimensionales | Microsoft Docs
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
- brackets [ ]
- brackets [ ], arrays
- one-dimensional arrays
- arrays [C++], one-dimensional
- square brackets [ ]
- square brackets [ ], arrays
- subscript expressions
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: ea3d4c2461579fcafc4f9ff7ba5071572229c640
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="one-dimensional-arrays"></a>Matrices unidimensionales
Una expresión de postfijo seguida de una expresión entre corchetes (**[ ]**) es una representación de subíndice de un elemento de un objeto de matriz. Una expresión de subíndice representa el valor en la dirección, es decir, posiciones de *expression* más allá de *postfix-expression* cuando se expresa como  
  
```  
  
postfix-expression  
[  
expression  
]  
  
```  
  
 Normalmente, el valor representado por *postfix-expression* es un valor de puntero, tal como un identificador de matriz y *expression* es un valor entero. Sin embargo, todo lo que se necesita desde el punto de vista sintáctico es que una de las expresiones sea de tipo puntero y que la otra sea de tipo entero. Así pues, el valor entero podría estar en la posición de *postfix-expression* y el valor de puntero podría estar en los corchetes de la posición de *expression* o subíndice. Por ejemplo, este código es válido:  
  
```  
// one_dimensional_arrays.c  
int sum, *ptr, a[10];  
int main() {  
   ptr = a;  
   sum = 4[ptr];  
}  
```  
  
 Las expresiones suscritas se utilizan normalmente para hacer referencia a elementos de matriz, pero se puede aplicar un subíndice a cualquier puntero. Sea cual sea el orden de los valores, *expression* se debe incluir entre corchetes (**[ ]**).  
  
 La expresión de subíndice se evalúa sumando el valor entero al valor del puntero y, después, aplicando el operador de direccionamiento indirecto (**\***) al resultado. (Vea [Direccionamiento indirecto y dirección de operadores](../c-language/indirection-and-address-of-operators.md) para ver una descripción del operador de direccionamiento indirecto). De hecho, en una matriz unidimensional, las cuatro expresiones siguientes son equivalentes, suponiendo que `a` es un puntero y `b` es un entero:  
  
```  
a[b]  
*(a + b)  
*(b + a)  
b[a]  
```  
  
 Según las reglas de conversión para el operador de suma (dadas en [Operadores aditivos](../c-language/c-additive-operators.md)), el valor entero se convierte en un desplazamiento de dirección multiplicándolo por la longitud del tipo direccionado por el puntero.  
  
 Por ejemplo, suponga que el identificador `line` hace referencia a una matriz de valores `int`. El procedimiento siguiente se utiliza para evaluar la expresión de subíndice `line[ i ]`:  
  
1.  El valor entero `i` se multiplica por el número de bytes definido como la longitud de un elemento `int`. El valor convertido de `i` representa las posiciones `i` `int`.  
  
2.  Este valor convertido se suma al valor del puntero original (`line`) para producir una dirección que está desplazada a las posiciones `i` `int` respecto a `line`.  
  
3.  El operador de direccionamiento indirecto se aplica a la nueva dirección. El resultado es el valor del elemento de matriz en esa posición (de manera intuitiva, `line [ i ]`).  
  
 La expresión de subíndice `line[0]` representa el valor del primer elemento de la línea, ya que el desplazamiento respecto a la dirección representada por `line` es 0. De igual forma, una expresión tal como `line[5]` hace referencia al elemento desplazado cinco posiciones respecto a la línea o al sexto elemento de la matriz.  
  
## <a name="see-also"></a>Vea también  
 [Operador de subíndice:](../cpp/subscript-operator.md)
