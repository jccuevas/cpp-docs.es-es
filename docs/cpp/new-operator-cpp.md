---
title: Operador new (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cc2131ad3c74477aa8972ca4e6e75bf845c954e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057306"
---
# <a name="new-operator-c"></a>new (Operador) (C++)

Asigna memoria para un objeto o una matriz de objetos de *nombre de tipo* del almacén disponible y devuelve un puntero con tipo adecuado distinto de cero al objeto.

> [!NOTE]
>  Extensiones de componentes de Microsoft C++ proporciona compatibilidad para la **nuevo** palabra clave para agregar entradas de ranura de vtable. Para obtener más información, consulte [new (nueva ranura en vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>Sintaxis

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Comentarios

Si no lo consigue, **nueva** devuelve cero o produce una excepción; vea [el nuevo y eliminar operadores](../cpp/new-and-delete-operators.md) para obtener más información. Puede cambiar este comportamiento predeterminado escribiendo una rutina de control de excepciones personalizada y llamando a la [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) función de biblioteca en tiempo de ejecución con el nombre de función como su argumento.

Para obtener información sobre cómo crear un objeto en el montón administrado, consulte [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md).

Cuando **nuevo** es usa para asignar memoria para un objeto de clase de C++, el constructor del objeto se llama después de que se asigna la memoria.

Use la [eliminar](../cpp/delete-operator-cpp.md) operador para desasignar la memoria asignada con el **nuevo** operador.

En el ejemplo siguiente se asigna y se libera una matriz bidimensional de caracteres de tamaño `dim` por 10. Al asignar una matriz multidimensional, todas las dimensiones excepto la primera deben ser expresiones constantes que se evalúen como valores positivos; la dimensión de la matriz del extremo izquierdo puede ser cualquier expresión que se evalúe como un valor positivo. Al asignar una matriz mediante la **nueva** operador, la primera dimensión puede ser cero, el **nuevo** operador devuelve un puntero único.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

El *nombre de tipo* no puede contener **const**, **volátil**, declaraciones de clase ni declaraciones de enumeración. Por consiguiente, la siguiente expresión no es válida:

```cpp
volatile char *vch = new volatile char[20];
```

El **nuevo** operador no asigna los tipos de referencia porque no son objetos.

El **nuevo** operador no se puede usar para asignar una función, pero se puede usar para asignar punteros a funciones. En el ejemplo siguiente se asigna y se libera una matriz de siete punteros a funciones que devuelven enteros.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

Si usa el operador **nueva** sin ningún argumento adicional y compilar con la [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md), o [/EHs](../build/reference/eh-exception-handling-model.md) opción, el compilador creará generar código para llamar al operador **eliminar** si el constructor produce una excepción.

En la lista siguiente se describe los elementos de gramática de **nuevo**:

*selección de ubicación*<br/>
Proporciona una manera de pasar argumentos adicionales si sobrecarga **nuevo**.

*nombre de tipo*<br/>
Especifica el tipo que se va a asignar; puede ser un tipo integrado o un tipo definido por el usuario. Si la especificación de tipo es compleja, puede ir entre paréntesis para forzar el orden de enlace.

*initializer*<br/>
Proporciona un valor para el objeto inicializado. No se pueden especificar inicializadores para matrices. El **nuevo** operador creará las matrices de objetos solo si la clase tiene un constructor predeterminado.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se asigna una matriz de caracteres y un objeto de clase `CName` y después se liberan.

```cpp
// expre_new_Operator.cpp
// compile with: /EHsc
#include <string.h>

class CName {
public:
   enum {
      sizeOfBuffer = 256
   };

   char m_szFirst[sizeOfBuffer];
   char m_szLast[sizeOfBuffer];

public:
   void SetName(char* pszFirst, char* pszLast) {
     strcpy_s(m_szFirst, sizeOfBuffer, pszFirst);
     strcpy_s(m_szLast, sizeOfBuffer, pszLast);
   }

};

int main() {
   // Allocate memory for the array
   char* pCharArray = new char[CName::sizeOfBuffer];
   strcpy_s(pCharArray, CName::sizeOfBuffer, "Array of characters");

   // Deallocate memory for the array
   delete [] pCharArray;
   pCharArray = NULL;

   // Allocate memory for the object
   CName* pName = new CName;
   pName->SetName("Firstname", "Lastname");

   // Deallocate memory for the object
   delete pName;
   pName = NULL;
}
```

## <a name="example"></a>Ejemplo

Si usa el formato de la nueva ubicación de la **nueva** operador, el formato con argumentos además del tamaño de la asignación, el compilador no admite un formato de ubicación de la **eliminar** operador si el constructor produce una excepción. Por ejemplo:

```cpp
// expre_new_Operator2.cpp
// C2660 expected
class A {
public:
   A(int) { throw "Fail!"; }
};
void F(void) {
   try {
      // heap memory pointed to by pa1 will be deallocated
      // by calling ::operator delete(void*).
      A* pa1 = new A(10);
   } catch (...) {
   }
   try {
      // This will call ::operator new(size_t, char*, int).
      // When A::A(int) does a throw, we should call
      // ::operator delete(void*, char*, int) to deallocate
      // the memory pointed to by pa2.  Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.

      A* pa2 = new(__FILE__, __LINE__) A(20);
   } catch (...) {
   }
}

int main() {
   A a;
}
```

## <a name="initializing-object-allocated-with-new"></a>Inicializar objetos asignados con new

Opcional *inicializador* campo se incluye en la gramática de la **nuevo** operador. Esto permite que los nuevos objetos se inicialicen con constructores definidos por el usuario. Para obtener más información acerca de cómo se realiza la inicialización, vea [inicializadores](../cpp/initializers.md). El ejemplo siguiente muestra cómo usar una expresión de inicialización con el **nuevo** operador:

```cpp
// expre_Initializing_Objects_Allocated_with_new.cpp
class Acct
{
public:
    // Define default constructor and a constructor that accepts
    //  an initial balance.
    Acct() { balance = 0.0; }
    Acct( double init_balance ) { balance = init_balance; }
private:
    double balance;
};

int main()
{
    Acct *CheckingAcct = new Acct;
    Acct *SavingsAcct = new Acct ( 34.98 );
    double *HowMuch = new double ( 43.0 );
    // ...
}
```

En este ejemplo, el objeto `CheckingAcct` se asigna mediante el **nuevo** se especifica el operador, pero ninguna inicialización predeterminada. Por lo tanto, se llama al constructor predeterminado para la clase, `Acct()`. El objeto `SavingsAcct` se asigna de la misma manera, salvo que se inicializa explícitamente en 34,98. Dado que 34,98 es de tipo **doble**, se llama al constructor que toma un argumento de ese tipo para controlar la inicialización. Finalmente, el tipo `HowMuch` que no es de clase se inicializa en 43,0.

Si un objeto es de un tipo de clase y esa clase tiene constructores (como se muestra en el ejemplo anterior), se puede inicializar el objeto por el **nuevo** operador solo si se cumple una de estas condiciones:

- Los argumentos proporcionados en el inicializador concuerdan con los de un constructor.

- La clase tiene un constructor predeterminado (un constructor al que se puede llamar sin argumentos).

No se puede realizar ninguna inicialización explícita por elemento al asignar matrices mediante la **nuevo** operador; solo el constructor predeterminado, si está presente, se llama. Consulte [argumentos predeterminados](../cpp/default-arguments.md) para obtener más información.

Si se produce un error en la asignación de memoria (**operador new** devuelve un valor de 0), se realiza ninguna inicialización. Esto protege contra intentos de inicializar datos que no existen.

Como sucede con las llamadas a funciones, no se define el orden en que se evalúan las expresiones inicializadas. Además, no debe dar por hecho que estas expresiones se hayan evaluado totalmente antes de que se realice la asignación de memoria. Si se produce un error en la asignación de memoria y el **nuevo** operador devuelve cero, algunas expresiones en el inicializador no se pueden evaluar por completo.

## <a name="lifetime-of-objects-allocated-with-new"></a>Duración de objetos asignados con new

Objetos asignados con el **nuevo** operador no se destruyen cuando se sale del ámbito en el que se definen. Dado que el **nuevo** operador devuelve un puntero a los objetos que asigna, el programa debe definir un puntero con el ámbito adecuado para tener acceso a esos objetos. Por ejemplo:

```cpp
// expre_Lifetime_of_Objects_Allocated_with_new.cpp
// C2541 expected
int main()
{
    // Use new operator to allocate an array of 20 characters.
    char *AnArray = new char[20];

    for( int i = 0; i < 20; ++i )
    {
        // On the first iteration of the loop, allocate
        //  another array of 20 characters.
        if( i == 0 )
        {
            char *AnotherArray = new char[20];
        }
    }

    delete [] AnotherArray; // Error: pointer out of scope.
    delete [] AnArray;      // OK: pointer still in scope.
}
```

Una vez que el puntero `AnotherArray` sale del ámbito en el ejemplo, el objeto ya no se puede eliminar.

## <a name="how-new-works"></a>Cómo funciona new

El *expresión de asignación* : la expresión que contiene el **nuevo** operador: hace tres cosas:

- Busca y reserva el almacenamiento para el objeto o los objetos a asignar. Cuando se completa esta fase, se asigna la cantidad correcta de almacenamiento, pero no es todavía un objeto.

- Inicializa los objetos. Una vez completada la inicialización, hay suficiente información presente para que el almacenamiento asignado sea un objeto.

- Devuelve un puntero a los objetos de un tipo de puntero derivado de *nuevo nombre de tipo* o *nombre de tipo*. El programa usa este puntero para tener acceso al objeto recién asignado.

El **nueva** operador invoca la función **new (operador)**. Para las matrices de cualquier tipo y para los objetos que no son de **clase**, **struct**, o **unión** tipos, una función global, **:: new (operador)**, es se llama para asignar el almacenamiento. Objetos de tipo de clase pueden definir sus propios **operador new** función miembro estática por clase.

Cuando el compilador encuentra la **nueva** operador para asignar un objeto de tipo **tipo**, emite una llamada a `type` **:: operador new (sizeof (** `type` **))** o, si no definido por el usuario **new (operador)** está definido, **:: operador new (sizeof (** `type` **))**. Por lo tanto, el **nuevo** operador puede asignar la cantidad de memoria correcta para el objeto.

> [!NOTE]
>  El argumento **new (operador)** es de tipo `size_t`. Este tipo se define en \<direct.h >, \<malloc.h >, \<memory.h >, \<search.h >, \<stddef.h >, \<stdio.h >, \<stdlib.h >, \<string.h >, y \<time.h >.

Una opción en la gramática permite la especificación de *colocación* (vea la gramática para [nuevo operador](../cpp/new-operator-cpp.md)). El *colocación* parámetro puede usarse solo para las implementaciones definidas por el usuario de **new (operador)**; permite que la información adicional que se pasarán al **new (operador)**. Una expresión con un *colocación* campo como `T *TObject = new ( 0x0040 ) T;` se traduce a `T *TObject = T::operator new( sizeof( T ), 0x0040 );` si la clase T tiene el operador de miembro nueva, en caso contrario, para `T *TObject = ::operator new( sizeof( T ), 0x0040 );`.

La intención original de la *colocación* campo era permitir que los objetos dependientes de hardware se asignen a las direcciones especificadas por el usuario.

> [!NOTE]
>  Aunque en el ejemplo anterior muestra un único argumento en el *colocación* campo, no hay ninguna restricción sobre cuántos argumentos adicionales se pueden pasar a **new (operador)** de este modo.

Incluso cuando **operador new** se ha definido para un tipo de clase, puede utilizarse el operador global mediante el uso de la forma de este ejemplo:

```cpp
T *TObject =::new TObject;
```

El operador de resolución de ámbito (`::`) fuerza el uso de la información global **nuevo** operador.

## <a name="see-also"></a>Vea también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[nuevo y eliminar operadores](../cpp/new-and-delete-operators.md)