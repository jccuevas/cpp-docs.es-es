---
title: friend (C++)
ms.date: 07/15/2019
f1_keywords:
- friend_cpp
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
ms.openlocfilehash: 20116674feffaa5b4bbddf707dd3a4d0c1d9ad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364443"
---
# <a name="friend-c"></a>friend (C++)

En algunas circunstancias, es más conveniente conceder acceso de nivel de miembro a funciones que no son miembros de una clase o a todos los miembros de una clase independiente. Solo el implementador de la clase puede declarar cuáles son sus funciones o clases friend. Las funciones o clases no pueden hacerlo por sí mismas. En una definición de clase, use la palabra clave **friend** y el nombre de una función que no sea miembro u otra clase para concederle acceso a los miembros privados y protegidos de la clase. En una definición de plantilla, un parámetro de tipo se puede declarar como amigo.

## <a name="syntax"></a>Sintaxis

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>Declaraciones friend

Si declara una función friend que no se declaró previamente, esa función se exporta al ámbito de inclusión que no es de clase.

Las funciones declaradas en una declaración friend se tratan como si se hubieran declarado mediante la palabra clave **extern.** Para obtener más información, consulte [extern](extern-cpp.md).

Aunque las funciones con ámbito global se pueden declarar como friend antes que los prototipos, las funciones miembro no se pueden declarar como friend antes de que aparezca la declaración de clase completa. En el siguiente ejemplo de código se muestra por qué esto produce un error:

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

El ejemplo anterior introduce el nombre de clase `ForwardDeclared` en el ámbito, pero la declaración completa (específicamente, la parte que declara la función `IsAFriend`) no se conoce. Por lo **friend** tanto, `HasFriends` la declaración friend en la clase genera un error.

A partir de C++11, hay dos formas de declaraciones de amigos para una clase:

```cpp
friend class F;
friend F;
```

El primer formulario introduce una nueva clase F si no se encontró ninguna clase existente con ese nombre en el espacio de nombres más interno. **C++11**: El segundo formulario no introduce una nueva clase; se puede utilizar cuando la clase ya se ha declarado y debe utilizarse al declarar un parámetro de tipo de plantilla o una typedef como amigo.

Se `class friend F` utiliza cuando el tipo al que se hace referencia aún no se ha declarado:

```cpp
namespace NS
{
    class M
    {
        class friend F;  // Introduces F but doesn't define it
    };
}
```

```cpp
namespace NS
{
    class M
    {
        friend F; // error C2433: 'NS::F': 'friend' not permitted on data declarations
    };
}
```

En el ejemplo `friend F` siguiente, `F` hace referencia a la clase que se declara fuera del ámbito de NS.

```cpp
class F {};
namespace NS
{
    class M
    {
        friend F;  // OK
    };
}
```

Se `friend F` utiliza para declarar un parámetro de plantilla como amigo:

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

Se `friend F` utiliza para declarar una typedef como amigo:

```cpp
class Foo {};
typedef Foo F;

class G
{
    friend F; // OK
    friend class F // Error C2371 -- redefinition
};
```

Para declarar dos clases que son de tipo friend entre sí, la segunda clase completa se debe especificar como friend de la primera clase. La razón de esta restricción se debe a que el compilador solo tiene información suficiente para declarar funciones friend individuales en el punto donde se declara la segunda clase.

> [!NOTE]
> Aunque la segunda clase completa debe ser definirse como friend en la primera clase, puede seleccionar las funciones de la primera clase que se definen como friend para la segunda clase.

## <a name="friend-functions"></a>funciones de confianza

Una función **friend** es una función que no es miembro de una clase pero tiene acceso a los miembros privados y protegidos de la clase. Las funciones friend no se consideran miembros de clase; son funciones externas normales que tienen privilegios de acceso especiales. Los amigos no están en el ámbito de la clase y no se les llama mediante los operadores de selección de miembros (**.** y**>**- ) a menos que sean miembros de otra clase. La clase que concede acceso declara una función **friend.** La declaración **friend** se puede colocar en cualquier lugar de la declaración de clase. No se ve afectada por las palabras clave de control de acceso.

En el ejemplo siguiente se muestra una clase `Point` y una función friend, `ChangePrivate`. La función **friend** tiene acceso al `Point` miembro de datos privados del objeto que recibe como parámetro.

```cpp
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

## <a name="class-members-as-friends"></a>Miembros de clase como friend

Las funciones miembro de clase se pueden declarar como de confianza en otras clases. Considere el ejemplo siguiente:

```cpp
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

En el ejemplo anterior, solo se concede a la función `A::Func1( B& )` acceso de confianza a la clase `B`. Por lo tanto, `_b` el acceso `Func1` al `A` miembro `Func2`privado es correcto en la clase, pero no en .

Una clase `friend` es una clase todas cuyas funciones miembro con funciones de confianza de una clase, es decir, cuyas funciones miembro tienen acceso a los miembros privados y protegidos de la otra clase. Suponga que la declaración `friend` de la clase `B` hubiera sido:

```cpp
friend class A;
```

En ese caso, a todas las funciones miembro de la clase `A` se les habría concedido acceso de confianza a la clase `B`. El código siguiente es un ejemplo de una clase de confianza:

```cpp
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

La confianza no es mutua a menos que se especifique explícitamente como tal. En el ejemplo anterior, las funciones miembro de `YourClass` no pueden tener acceso a los miembros privados de `YourOtherClass`.

Un tipo administrado (en C+/CLI) no puede tener funciones de amistad, clases de amistad o interfaces de amistad.

La confianza no se hereda, lo que significa que las clases derivadas de `YourOtherClass` no pueden tener acceso a los miembros privados de `YourClass`. La confianza no es transitiva, por lo que las clases de confianza de `YourOtherClass` no pueden tener acceso a los miembros privados de `YourClass`.

La ilustración siguiente muestra cuatro declaraciones de clase: `Base`, `Derived`, `aFriend` y `anotherFriend`. Solo la clase `aFriend` tiene acceso directo a los miembros privados de `Base` (y a cualquier miembro `Base` que pueda haber heredado).

![Implicaciones de relaciones de confianza](../cpp/media/vc38v41.gif "Implicaciones de relaciones de confianza") <br/>
Implicaciones de relaciones de confianza

## <a name="inline-friend-definitions"></a>Definiciones friend en línea

Las funciones Friend se pueden definir (dado un cuerpo de función) dentro de las declaraciones de clase. Estas funciones son funciones insertadas y como funciones insertadas de miembro, se comportan como si se hubieran definido inmediatamente después de haberse considerado todos los miembros de clase pero antes de cerrarse el ámbito de clase (el final de la declaración de clase). Las funciones Friend que se definen dentro de las declaraciones de clase están en el ámbito de la clase envolvente.

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)
