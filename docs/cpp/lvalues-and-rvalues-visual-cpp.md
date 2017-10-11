---
title: "Categorías de valor: Lvalues y Rvalues (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a3d230d3374a7be5aa57d965a451235d40cbee12
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="lvalues-and-rvalues-visual-c"></a>Lvalues y Rvalues (Visual C++)
Cada expresión de C++ tiene un tipo y pertenece a un *categoría valor*. Las categorías de valor son la base para las reglas que los compiladores deben seguir al crear, copiar y mover los objetos temporales durante la evaluación de expresión. 

 El estándar C ++ 17 define las categorías de valor de expresión como se indica a continuación:

- A *glvalue* es una expresión cuya evaluación determina la identidad de un objeto, un campo de bits o una función. 
- A *prvalue* es una expresión cuya evaluación Inicializa un objeto o un campo de bits, o calcula el valor del operando de un operador, tal y como especifica el contexto de donde aparece. 
- Un *xvalue* es un glvalue que denota un objeto o un campo de bits cuyos recursos se pueden reutilizar (normalmente porque está cerca del final de su duración). [Ejemplo: determinados tipos de expresiones que incluyen referencias a valor r (8.3.2) producen xvalues, por ejemplo, una llamada a una función cuyo tipo de valor devuelto es una referencia rvalue o una conversión a un tipo de referencia rvalue. ] 
- Un *valor l* es un glvalue que no sea un xvalue. 
- Un *rvalue* es un prvalue o un xvalue. 

El siguiente diagrama muestra las relaciones entre las categorías:

 ![Categorías de valor de expresión de C++](media/value_categories.png "categorías de valor de expresión de C++")  
 
 Un valor l tiene una dirección que puede tener acceso su programa. Nombres de variable, incluidos algunos ejemplos de expresiones de valor l `const` variables, elementos de matriz, función llamadas que devuelven una referencia lvalue, campos de bits, uniones y los miembros de clase. 
 
 Una expresión de prvalue no tiene ninguna dirección que sea accesible para el programa. Ejemplos de expresiones de prvalue incluyen literales, llamadas a funciones que devuelven un tipo sin referencia y los objetos temporales que se crean durante la evaluación de expresión pero accesible únicamente por el compilador. 

 Una expresión de xvalue no tiene ninguna dirección, pero puede usarse para inicializar una referencia rvalue, que proporciona acceso a la expresión. Algunos ejemplos son llamadas a funciones que devuelven una referencia rvalue y el subíndice de matriz, miembro y puntero a expresiones de miembro en la matriz o el objeto es una referencia rvalue. 
 
 En el ejemplo siguiente se muestran varios usos correctos e incorrectos de valores L y valores R:  
  
```  
// lvalues_and_rvalues2.cpp  
int main()  
{  
   int i, j, *p;  
  
   // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.  
   i = 7;  
  
   // Incorrect usage: The left operand must be an lvalue (C2106).  `j * 4` is a prvalue.
   7 = i; // C2106  
   j * 4 = 7; // C2106  
  
   // Correct usage: the dereferenced pointer is an lvalue.  
   *p = i;   
  
   const int ci = 7;  
   // Incorrect usage: the variable is a non-modifiable lvalue (C3892).  
   ci = 9; // C3892  
  
   // Correct usage: the conditional operator returns an lvalue.  
   ((i < 3) ? i : j) = 7;  
}  
```  
  
> [!NOTE]
>  En los ejemplos de este tema se muestra el uso correcto e incorrecto cuando los operadores no están sobrecargados. Si sobrecarga operadores, puede convertir una expresión tal como `j * 4` en un valor L.  

  
 Los términos *valor l* y *rvalue* a menudo se usan cuando se hace referencia a las referencias de objeto. Para obtener más información acerca de las referencias, vea [declarador de referencia de valor l: &](../cpp/lvalue-reference-declarator-amp.md) y [declarador de referencia Rvalue: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos](../cpp/basic-concepts-cpp.md)   
 [Declarador de referencia lvalue: &](../cpp/lvalue-reference-declarator-amp.md)   
 [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md)
