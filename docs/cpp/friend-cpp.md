---
title: "friend (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Friend"
  - "friend_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de confianza"
  - "friend (palabra clave) [C++]"
  - "acceso a miembros, desde funciones de confianza"
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# friend (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En algunos casos, es más cómodo conceder acceso de nivel de miembro a funciones que no son miembros de una clase o a todas las funciones de una clase independiente.  Solo el implementador de la clase puede declarar cuáles son sus funciones o clases friend.  Las funciones o clases no pueden hacerlo por sí mismas.  En una declaración de clase, use la palabra clave `friend` y el nombre de una función no miembro u otra clase para conceder acceso a los miembros privados y protegidos de la clase.  
  
## Sintaxis  
  
```  
  
        friend class-name;  
friend function-declarator;  
```  
  
## Declaraciones friend  
 Si declara una función friend que no se declaró previamente, esa función se exporta al ámbito de inclusión que no es de clase.  
  
 Las funciones declaradas en una declaración friend se tratan como si se hubieran declarado mediante la palabra clave `extern`.  \(Para obtener más información sobre `extern`, vea [Especificadores estáticos de clase de almacenamiento](http://msdn.microsoft.com/es-es/3ba9289a-a412-4a17-b319-ceb2c087df48)\).  
  
 Aunque las funciones con ámbito global se pueden declarar como friend antes que los prototipos, las funciones miembro no se pueden declarar como friend antes de que aparezca la declaración de clase completa.  En el siguiente ejemplo de código se muestra por qué esto produce un error:  
  
```  
class ForwardDeclared;   // Class name is known.  
class HasFriends  
{  
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected  
};  
```  
  
 El ejemplo anterior introduce el nombre de clase `ForwardDeclared` en el ámbito, pero la declaración completa \(específicamente, la parte que declara la función `IsAFriend`\) no se conoce.  Por consiguiente, la declaración de `friend` en la clase `HasFriends` genera un error.  
  
 Para declarar dos clases que son de tipo friend entre sí, la segunda clase completa se debe especificar como friend de la primera clase.  La razón de esta restricción se debe a que el compilador solo tiene información suficiente para declarar funciones friend individuales en el punto donde se declara la segunda clase.  
  
> [!NOTE]
>  Aunque la segunda clase completa debe ser definirse como friend en la primera clase, puede seleccionar las funciones de la primera clase que se definen como friend para la segunda clase.  
  
## funciones de confianza  
 Una función `friend` es una función que no es miembro de una clase pero tiene acceso a los miembros privados y protegidos de la clase.  Las funciones friend no se consideran miembros de clase; son funciones externas normales que tienen privilegios de acceso especiales.  No están en el ámbito de la clase y no se las llama usando los operadores de selección de miembro \(**.** y –**\>**\) a menos que sean miembros de otra clase.  Una función `friend` la declara la clase que concede el acceso.  La declaración `friend` se puede colocar en cualquier lugar de la declaración de clase.  No se ve afectada por las palabras clave de control de acceso.  
  
 En el ejemplo siguiente se muestra una clase `Point` y una función friend, `ChangePrivate`.  La función `friend` tiene acceso al miembro de datos privado del objeto `Point` que recibe como parámetro.  
  
```  
// friend_functions.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Point  
{  
    friend void ChangePrivate( Point & );  
public:  
    Point( void ) : m_i(0) {}  
    void PrintPrivate( void ){cout << m_i << endl; }  
  
private:  
    int m_i;  
};  
  
void ChangePrivate ( Point &i ) { i.m_i++; }  
  
int main()  
{  
   Point sPoint;  
   sPoint.PrintPrivate();  
   ChangePrivate(sPoint);  
   sPoint.PrintPrivate();  
// Output: 0  
           1  
}  
```  
  
## Miembros de clase como friend  
 Las funciones miembro de clase se pueden declarar como de confianza en otras clases.  Considere el ejemplo siguiente:  
  
```  
// classes_as_friends1.cpp  
// compile with: /c  
class B;  
  
class A {  
public:  
   int Func1( B& b );  
  
private:  
   int Func2( B& b );  
};  
  
class B {  
private:  
   int _b;  
  
   // A::Func1 is a friend function to class B  
   // so A::Func1 has access to all members of B  
   friend int A::Func1( B& );  
};  
  
int A::Func1( B& b ) { return b._b; }   // OK  
int A::Func2( B& b ) { return b._b; }   // C2248  
```  
  
 En el ejemplo anterior, solo se concede a la función `A::Func1( B& )` acceso de confianza a la clase `B`.  Por consiguiente, el acceso al miembro privado `_b` es correcto en `Func1` de la clase `A` pero no en `Func2`.  
  
 Una clase `friend` es una clase todas cuyas funciones miembro con funciones de confianza de una clase, es decir, cuyas funciones miembro tienen acceso a los miembros privados y protegidos de la otra clase.  Suponga que la declaración `friend` de la clase `B` hubiera sido:  
  
```  
friend class A;  
```  
  
 En ese caso, a todas las funciones miembro de la clase `A` se les habría concedido acceso de confianza a la clase `B`.  El código siguiente es un ejemplo de una clase de confianza:  
  
```  
// classes_as_friends2.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class YourClass {  
friend class YourOtherClass;  // Declare a friend class  
public:  
   YourClass() : topSecret(0){}  
   void printMember() { cout << topSecret << endl; }  
private:  
   int topSecret;  
};  
  
class YourOtherClass {  
public:  
   void change( YourClass& yc, int x ){yc.topSecret = x;}  
};  
  
int main() {  
   YourClass yc1;  
   YourOtherClass yoc1;  
   yc1.printMember();  
   yoc1.change( yc1, 5 );  
   yc1.printMember();  
}  
```  
  
 La confianza no es mutua a menos que se especifique explícitamente como tal.  En el ejemplo anterior, las funciones miembro de `YourClass` no pueden tener acceso a los miembros privados de `YourOtherClass`.  
  
 Un tipo administrado no puede tener funciones, clases o interfaces de confianza.  
  
 La confianza no se hereda, lo que significa que las clases derivadas de `YourOtherClass` no pueden tener acceso a los miembros privados de `YourClass`.  La confianza no es transitiva, por lo que las clases de confianza de `YourOtherClass` no pueden tener acceso a los miembros privados de `YourClass`.  
  
 La ilustración siguiente muestra cuatro declaraciones de clase: `Base`, `Derived`, `aFriend` y `anotherFriend`.  Solo la clase `aFriend` tiene acceso directo a los miembros privados de `Base` \(y a cualquier miembro `Base` que pueda haber heredado\).  
  
 ![Implicaciones de relaciones de confianza](../cpp/media/vc38v41.png "vc38V41")  
Implicaciones de relaciones de amistad  
  
## Definiciones friend en línea  
 Las funciones friend se pueden definir dentro de declaraciones de clase.  Estas funciones son funciones insertadas y como funciones insertadas de miembro, se comportan como si se hubieran definido inmediatamente después de haberse considerado todos los miembros de clase pero antes de cerrarse el ámbito de clase \(el final de la declaración de clase\).  
  
 Las funciones friend definidas dentro de declaraciones de clase no se consideran en el ámbito de la clase envolvente; están en el ámbito de archivo.  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)