---
title: "Expresiones primarias | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "expresiones [C++], literal"
  - "expresiones [C++], name"
  - "expresiones [C++], principal"
  - "expresiones [C++], nombres completos"
  - "expresiones primarias"
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Expresiones primarias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las expresiones primarias son los bloques de creación de expresiones más complejas.  Son literales, nombres, y nombres calificados por el operador de resolución de ámbito \(`::`\).  Una expresión primaria puede tener cualquiera de las formas siguientes:  
  
```  
  
        literal  
this  
:: name  
name   
( expression )  
```  
  
 Un *literal* es una expresión primaria constante.  Su tipo depende de la forma de su especificación.  Vea [Literales](../cpp/numeric-boolean-and-pointer-literals-cpp.md) para obtener información completa sobre la especificación de literales.  
  
 La palabra clave **this** es un puntero a un objeto de clase.  Está disponible en funciones miembro no estáticas y señala a la instancia de la clase para la que se ha invocado la función.  La palabra clave **this** no se puede utilizar fuera del cuerpo de una función miembro de clase.  
  
 El tipo del puntero **this** es `type` **\*const** \(donde `type` es el nombre de clase\) en funciones que no modifican específicamente el puntero **this**.  En el ejemplo siguiente se muestran declaraciones de funciones miembro y los tipos de **this**:  
  
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
  
 Vea [Tipo de puntero this](../misc/type-of-this-pointer.md) para obtener más información sobre la modificación del tipo del puntero **this**.  
  
 El operador de resolución de ámbito \(`::`\) seguido de un nombre constituye una expresión primaria.  Dichos nombres deben ser nombres en el ámbito global, no nombres de miembro.  El tipo de esta expresión está determinado por la declaración del nombre.  Es un valor L \(es decir, puede aparecer en el lado izquierdo de una expresión de operador de asignaciones\) si el nombre de declaración es un valor L.  El operador de resolución de ámbito permite que se haga referencia a un nombre global, incluso si ese nombre está oculto en el ámbito actual.  Vea [Ámbito](../cpp/scope-visual-cpp.md) para obtener un ejemplo de cómo se utiliza el operador de resolución de ámbito.  
  
 Una expresión delimitada entre paréntesis es una expresión primaria cuyos tipo y valor son idénticos a los de la expresión no incluida entre paréntesis.  Es un valor L si la expresión no incluida entre paréntesis es un l\-valor.  
  
 En el contexto de la sintaxis de expresión primaria proporcionada más arriba, *name* no significa nada en la sintaxis descrita para [Nombres](http://msdn.microsoft.com/es-es/1c49cc24-08d5-4884-b170-ba8ed42d80db), aunque cuando se utiliza el operador de resolución de ámbito delante del nombre, no se permiten tipos de nombres que solo pueden aparecer en una clase.  Esto incluye nombres de función de conversión definida por el usuario y nombres de destructor.  
  
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
  
 Los ejemplos siguientes se consideran nombres \(*name*\) todos ellos, y por consiguiente expresiones primarias, en diversas formas:  
  
```  
MyClass // a identifier  
MyClass::f // a qualified name  
operator = // an operator function name  
operator char* // a conversion operator function name  
~MyClass // a destructor name  
A::B   // a qualified name  
A<int> // a template id  
```  
  
## Vea también  
 [Tipos de expresiones](../cpp/types-of-expressions.md)