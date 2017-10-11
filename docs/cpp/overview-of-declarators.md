---
title: "Información general sobre los declaradores | Documentos de Microsoft"
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
- declarators, about declarators
ms.assetid: 0f2e2312-80bd-4154-8345-718bd9ed2173
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 4a8f795a23f4e93f02d5d6b5ce98d60555a432d6
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="overview-of-declarators"></a>Información general sobre los declaradores
Los declaradores son los componentes de una declaración que especifican nombres de objetos o funciones. Los declaradores también especifican si el objeto con nombre es o no un objeto, puntero, referencia o matriz.  Aunque los declaradores no especifican el tipo base, modifican la información de tipo del tipo básico para especificar tipos derivados, como punteros, referencias y matrices.  Cuando se aplica a las funciones, el declarador funciona con el especificador de tipo para especificar completamente que el tipo de valor devuelto de una función es un objeto, puntero o referencia. (Especificadores, que se describen en [declaraciones y definiciones](declarations-and-definitions-cpp.md), transmiten propiedades tales como la clase de tipo y el almacenamiento. Modificadores, se describen en esta sección y en [modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md), modifican los declaradores.) En la ilustración siguiente se muestra una declaración completa de `MyFunction` y se llama a los componentes de la declaración.  
  
 ![Modificadores, especificadores y declaradores](../cpp/media/vc38qy1.gif "vc38QY1")  
Especificadores, modificadores y declaradores  
  
 **Específicos de Microsoft**  
  
 La mayoría de las palabras clave extendidas de Microsoft se pueden utilizar como modificadores para formar tipos derivados; no son especificadores ni declaradores. (Consulte [modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).)  
  
 **FIN de Específicos de Microsoft**  
  
 Los declaradores aparecen en la sintaxis de declaración después de una lista opcional de especificadores. Estos especificadores se describen en [declaraciones.](declarations-and-definitions-cpp.md) Una declaración puede contener varios declaradores, pero cada declarador declara un solo nombre.  
  
 En la declaración de ejemplo siguiente se muestra cómo se combinan especificadores y declaradores para formar una declaración completa:  
  
```  
const char *pch, ch;  
```  
  
 En la declaración anterior, las palabras clave **const** y `char` forman parte de la lista de especificadores. Se muestran dos declaradores: `*pch` y `ch`.  Una declaración que declara varias entidades está formada por un especificador de tipo seguido de una lista separada por comas de declaradores, finalizada con un punto y coma.  
  
 **Declaradores de objetos simples**  
  
 El declarador de un objeto simple, como int o double, es simplemente su nombre, con paréntesis opcionales.  
  
 `int i; // declarator is i`  
  
 `int (i); // declarator is (i)`  
  
 **Declaradores de punteros, referencias y matrices**  
  
 Los operadores de puntero que se insertan delante del nombre hacen que el objeto sea un puntero o referencia.  El ** \* ** operador declara el nombre como puntero; el ** & ** operador declara como referencia.  
  
```  
int *i; // declarator is *i  
int **i; // declarator is **i;  
int &i = x; // declaratory is &i  
```  
  
 Al anexar `const` o `volatile`, se proporcionan al puntero estas propiedades especiales.  El uso de estos especificadores en un declarador (frente al especificador de tipo) modifica las propiedades del puntero, no el objeto al que se señala:  
  
```  
char *const cpc; // const pointer to char   
const char *pcc; // pointer to const char   
const char *const cpcc; // const pointer to const char  
```  
  
 Puede encontrar más información en [punteros const y volatile](../cpp/const-and-volatile-pointers.md).  
  
 Un puntero a un miembro de una clase o struct se declara con el especificador de nombre anidado adecuado:  
  
```  
int X::* pIntMember;   
int ::X::* pIntMember; // the initial :: specifies X is in global scope  
char Outer::Inner::* pIntMember; // pointer to char in a nested class  
```  
  
 Los corchetes que rodean una expresión constante opcional después del nombre hacen que el objeto sea una matriz.  Los corchetes posteriores declaran dimensiones adicionales de la matriz.  
  
```  
int i[5]; // array with five elements of type int numbered from 0 to 4  
int i[]; // array of unknown size  
char *s[4]; // array of pointers to char  
int i[2][2]; // two dimensional array  
```  
  
 **Declaradores de funciones**  
  
 Se usan paréntesis alrededor de la lista de argumentos, detrás del nombre, para declarar una función.  A continuación, se declara una función del tipo de valor devuelto `int` y tres argumentos de tipo `int`.  
  
```  
int f(int a, int b, int c);  
```  
  
 Los punteros y referencias a funciones se declaran mediante la anteposición del puntero u operador de referencia al nombre de función, como se muestra a continuación.  Se requieren paréntesis, normalmente opcionales, para distinguir un puntero a una función de una función que devuelve un puntero:  
  
```  
int (*pf)(int); // pointer to function returning int  
int *f(int i); // function returning pointer to int  
int (&pf)(int); // reference to function   
```  
  
 Los punteros a funciones miembro se distinguen por los especificadores de nombre anidados:  
  
```  
int (X::* pmf)(); // pointer to member function of X returning int  
int* (X::* pmf)(); // pointer to member function returning pointer to int  
```  
  
 Vea también [punteros a miembros](../cpp/pointers-to-members.md).  
  
 **Funciones y objetos en la misma declaración**  
  
 Las funciones y objetos se pueden declarar en la misma declaración, como se indica a continuación:  
  
```  
int i, *j, f(int k);  // int, pointer to int, function returning int  
```  
  
 La sintaxis puede ser confusa en algunas circunstancias.  La siguiente declaración  
  
```  
int* i, f(int k);  // pointer to int, function returning int (not int*)  
```  
  
 puede parecer la declaración de un puntero `int` y una función que devuelve `int*`, pero no lo es.  Esto se debe a que * es parte del declarador de `i`, no parte del declarador de `f`.  
  
 **Simplificación de la sintaxis de declarador con typedef**  
  
 Sin embargo, existe una técnica mejor, que consiste en utilizar `typedef` o una combinación de paréntesis y la palabra clave `typedef`. Considere, por ejemplo, una matriz de punteros a funciones:  
  
```  
//  Function returning type int that takes one   
//   argument of type char *.  
typedef int (*PIFN)( char * );  
//  Declare an array of 7 pointers to functions   
//   returning int and taking one argument of type   
//   char *.  
PIFN pifnDispatchArray[7];  
```  
  
 La declaración equivalente se puede escribir sin la declaración de `typedef`, pero es tan complicado que las posibilidades de error superan cualquier ventaja:  
  
```  
int ( *pifnDispatchArray[7] )( char * );  
```  
  
 Para obtener más información sobre typedef, vea [alias y definiciones de tipo](aliases-and-typedefs-cpp.md).  
  
 Los punteros, referencias y matrices de un solo tipo base se pueden combinar en una sola declaración (separados por comas), como  
  
```  
int a, *b, c[5], **d, &e=a;  
```  
  
 **Sintaxis de declarador más compleja**  
  
-   Los declaradores de punteros, referencias, matrices y funciones se pueden combinar para especificar objetos tales como matrices de punteros a funciones, punteros a matrices, etc.  
  
-   La gramática recursiva siguiente describe la sintaxis completa de un declarador de puntero.  
  
-   `declarator` se define como:  
  
```  
1. identifier   
2. qualified-name   
3. declarator ( argument-list ) [cv-qualfiers] [exception-spec]  
4. declarator [ [ constant-expression ] ]   
  
5. pointer-operatordeclarator   
6. ( declarator )  
```  
  
-   y *operador de puntero* es uno de:  
  
```  
  
      * [cv-qualifiers]  
& [cv-qualifiers]  
::nested-name-specifier * [cv-qualfiers]  
```  
  
 Dado que un declarador puede contener declaradores, es posible construir los tipos derivados más complejos, como matrices de punteros, funciones que devuelven matrices de punteros a función, mediante las reglas anteriores.  Para formar cada paso de la construcción, comience con el identificador que representa el tipo de datos base y aplique la regla de sintaxis anterior con la expresión anterior como `declarator`.  El orden de aplicación de las reglas de sintaxis debe ser el inverso de como se indica la expresión en inglés.  Si se aplica el *operador de puntero* regla de sintaxis en una expresión de matriz o función, utilice paréntesis si desea un puntero a la matriz o función, como se muestra en la última fila en la tabla siguiente.  
  
 En el ejemplo siguiente, se muestra la construcción de “puntero a matriz de 10 punteros a int”.  
  
|Expresión verbal|Declarador|Regla de sintaxis aplicada|  
|-----------------------|----------------|-------------------------|  
||`i`|1|  
|puntero(s) a|`*i`|5|  
|matriz de 10|`(*i)[10]`|4|  
|puntero a|`*((*i)[10])`|6 y después 5|  
  
 Cuando se utilizan varios modificadores de puntero, referencia, matriz o función, los declaradores pueden resultar bastante complicados.  El tema [interpretar declaradores más complejos](../c-language/interpreting-more-complex-declarators.md) describe cómo leer la sintaxis de declarador más compleja.  El tema es aplicable a C y C++, aunque en C++, en cualquier lugar del * se usa para indicar un puntero, un nombre calificado tal como MyClass::\* puede utilizarse para especificar un puntero a un miembro de una clase.
