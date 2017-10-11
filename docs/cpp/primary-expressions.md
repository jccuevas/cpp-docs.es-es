---
title: Expresiones primarias | Documentos de Microsoft
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
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 2ba603c19a88849c15c9402e21d2acf39bb9f54d
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="primary-expressions"></a>Expresiones primarias
Las expresiones primarias son los bloques de creación de expresiones más complejas. Son literales, nombres, y nombres calificados por el operador de resolución de ámbito (`::`).  Una expresión primaria puede tener cualquiera de las formas siguientes:  
  
```  
  
      literal  
      this  
:: namename( expression )  
```  
  
 A *literal* es una expresión primaria constante. Su tipo depende de la forma de su especificación. Vea [literales](../cpp/numeric-boolean-and-pointer-literals-cpp.md) para obtener información completa acerca de cómo especificar literales.  
  
 El **esto** palabra clave es un puntero a un objeto de clase. Está disponible en funciones miembro no estáticas y señala a la instancia de la clase para la que se ha invocado la función. El **esto** palabra clave no se puede usar fuera del cuerpo de una función miembro de clase.  
  
 El tipo de la **esto** puntero es `type` ** \*const** (donde `type` es el nombre de clase) dentro de las funciones no modifican específicamente el **esta** puntero. En el ejemplo siguiente se muestra el miembro declaraciones de función y los tipos de **esto**:  
  
```  
// expre_Primary_Expressions.cpp  
// compile with: /LD  
class Example  
{  
public:  
    void Func();          //  * const this  
    void Func() const;    //  const * const this  
    void Func() volatile; //  volatile * const this  
};  
```  
  
 Vea [this (puntero)](this-pointer.md) para obtener más información acerca de cómo modificar el tipo de la **esto** puntero.  
  
 El operador de resolución de ámbito (`::`) seguido de un nombre constituye una expresión primaria.  Dichos nombres deben ser nombres en el ámbito global, no nombres de miembro.  El tipo de esta expresión está determinado por la declaración del nombre. Es un valor L (es decir, puede aparecer en el lado izquierdo de una expresión de operador de asignaciones) si el nombre de declaración es un valor L. El operador de resolución de ámbito permite que se haga referencia a un nombre global, incluso si ese nombre está oculto en el ámbito actual. Vea [ámbito](../cpp/scope-visual-cpp.md) para obtener un ejemplo de cómo usar el operador de resolución de ámbito.  
  
 Una expresión delimitada entre paréntesis es una expresión primaria cuyos tipo y valor son idénticos a los de la expresión no incluida entre paréntesis. Es un valor L si la expresión no incluida entre paréntesis es un l-valor.  
  
 En el contexto de la sintaxis de expresión primaria indicada anteriormente, *nombre* significa cualquier cosa en la sintaxis descrita para [nombres](http://msdn.microsoft.com/en-us/1c49cc24-08d5-4884-b170-ba8ed42d80db), aunque cuando mediante el operador de resolución de ámbito antes del nombre, tipos de nombres que sólo puede ocurrir en una clase no se permiten.  Esto incluye nombres de función de conversión definida por el usuario y nombres de destructor.  
  
 Entre los ejemplos de expresiones primarias se incluyen:  
  
```  
100 // literal  
'c' // literal  
this // in a member function, a pointer to the class instance  
::func // a global function  
::operator + // a global operator function  
::A::B // a global qualified name  
( i + 1 ) // a parenthesized expression  
```  
  
 Los ejemplos siguientes se consideran *nombres*y por consiguiente expresiones primarias, en diversas formas:  
  
```  
MyClass // a identifier  
MyClass::f // a qualified name  
operator = // an operator function name  
operator char* // a conversion operator function name  
~MyClass // a destructor name  
A::B   // a qualified name  
A<int> // a template id  
```  
  
## <a name="see-also"></a>Vea también  
 [Tipos de expresiones](../cpp/types-of-expressions.md)
