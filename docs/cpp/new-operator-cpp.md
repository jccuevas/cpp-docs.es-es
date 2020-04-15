---
title: new (Operador) (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: ac89bf37b8aaaa9d77393b714a233f8a4c998139
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367872"
---
# <a name="new-operator-c"></a>new (Operador) (C++)

Asigna memoria para un objeto o matriz de objetos de *tipo-nombre* del almacén libre y devuelve un puntero distinto de cero con tipo adecuada al objeto.

> [!NOTE]
> Microsoft C++ Extensiones de componentes proporciona compatibilidad con la **nueva** palabra clave para agregar entradas de ranura vtable. Para obtener más información, consulte [new (nueva ranura en vtable)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>Sintaxis

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Observaciones

Si no se realiza correctamente, **new** devuelve cero o produce una excepción; consulte [Los operadores nuevos y eliminados](../cpp/new-and-delete-operators.md) para obtener más información. Puede cambiar este comportamiento predeterminado escribiendo una rutina de control de excepciones personalizada y llamando a la [función](../c-runtime-library/reference/set-new-handler.md) de biblioteca en tiempo de ejecución de _set_new_handler con el nombre de la función como argumento.

Para obtener información sobre cómo crear un objeto en el montón administrado, consulte [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Cuando se usa **new** para asignar memoria para un objeto de clase C++, se llama al constructor del objeto después de asignar la memoria.

Utilice el operador [delete](../cpp/delete-operator-cpp.md) para desasignar la memoria asignada con el operador **new.**

En el ejemplo siguiente se asigna y se libera una matriz bidimensional de caracteres de tamaño `dim` por 10. Al asignar una matriz multidimensional, todas las dimensiones excepto la primera deben ser expresiones constantes que se evalúen como valores positivos; la dimensión de la matriz del extremo izquierdo puede ser cualquier expresión que se evalúe como un valor positivo. Al asignar una matriz mediante el operador **new,** la primera dimensión puede ser cero: el operador **new** devuelve un puntero único.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

El *nombre-tipo* no puede contener **const**, **volatile**, declaraciones de clase o declaraciones de enumeración. Por consiguiente, la siguiente expresión no es válida:

```cpp
volatile char *vch = new volatile char[20];
```

El operador **new** no asigna tipos de referencia porque no son objetos.

El **operador new** no se puede utilizar para asignar una función, pero se puede utilizar para asignar punteros a funciones. En el ejemplo siguiente se asigna y se libera una matriz de siete punteros a funciones que devuelven enteros.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

Si usa el operador **new** sin ningún argumento adicional y compila con la opción [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md)o [/EHs,](../build/reference/eh-exception-handling-model.md) el compilador generará código para llamar a **operator delete** si el constructor produce una excepción.

La siguiente lista describe los elementos gramaticales de **new:**

*Colocación*<br/>
Proporciona una forma de pasar argumentos adicionales si sobrecarga **new**.

*nombre-tipo*<br/>
Especifica el tipo que se va a asignar; puede ser un tipo integrado o un tipo definido por el usuario. Si la especificación de tipo es compleja, puede ir entre paréntesis para forzar el orden de enlace.

*initializer*<br/>
Proporciona un valor para el objeto inicializado. No se pueden especificar inicializadores para matrices. El **operador new** creará matrices de objetos solo si la clase tiene un constructor predeterminado.

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

Si usa la nueva forma de ubicación del **operador new,** el formulario con argumentos además del tamaño de la asignación, el compilador no admite una forma de ubicación del operador **delete** si el constructor produce una excepción. Por ejemplo:

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

Se incluye un campo *de inicializador* opcional en la gramática del **operador new.** Esto permite que los nuevos objetos se inicialicen con constructores definidos por el usuario. Para obtener más información sobre cómo se realiza la inicialización, vea [Inicializadores](../cpp/initializers.md). En el ejemplo siguiente se muestra cómo utilizar una expresión de inicialización con el operador **new:**

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

En este ejemplo, `CheckingAcct` el objeto se asigna mediante el operador **new,** pero no se especifica ninguna inicialización predeterminada. Por lo tanto, se llama al constructor predeterminado para la clase, `Acct()`. El objeto `SavingsAcct` se asigna de la misma manera, salvo que se inicializa explícitamente en 34,98. Dado que 34.98 es de tipo **double**, se llama al constructor que toma un argumento de ese tipo para controlar la inicialización. Finalmente, el tipo `HowMuch` que no es de clase se inicializa en 43,0.

Si un objeto es de un tipo de clase y esa clase tiene constructores (como en el ejemplo anterior), el operador **new** solo puede inicializar el objeto si se cumple una de estas condiciones:

- Los argumentos proporcionados en el inicializador concuerdan con los de un constructor.

- La clase tiene un constructor predeterminado (un constructor al que se puede llamar sin argumentos).

No se puede realizar ninguna inicialización explícita por elemento al asignar matrices mediante el operador **new;** solo se llama al constructor predeterminado, si está presente. Consulte [Argumentos predeterminados](../cpp/default-arguments.md) para obtener más información.

Si se produce un error en la asignación de memoria **(el operador new** devuelve un valor de 0), no se realiza ninguna inicialización. Esto protege contra intentos de inicializar datos que no existen.

Como sucede con las llamadas a funciones, no se define el orden en que se evalúan las expresiones inicializadas. Además, no debe dar por hecho que estas expresiones se hayan evaluado totalmente antes de que se realice la asignación de memoria. Si se produce un error en la asignación de memoria y el **operador new** devuelve cero, es posible que algunas expresiones del inicializador no se evalúen completamente.

## <a name="lifetime-of-objects-allocated-with-new"></a>Duración de objetos asignados con new

Los objetos asignados con el **operador new** no se destruyen cuando se cierra el ámbito en el que se definen. Dado que el **operador new** devuelve un puntero a los objetos que asigna, el programa debe definir un puntero con el ámbito adecuado para tener acceso a esos objetos. Por ejemplo:

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

La *expresión de asignación* —la expresión que contiene el **operador new—** hace tres cosas:

- Busca y reserva el almacenamiento para el objeto o los objetos a asignar. Cuando se completa esta fase, se asigna la cantidad correcta de almacenamiento, pero no es todavía un objeto.

- Inicializa los objetos. Una vez completada la inicialización, hay suficiente información presente para que el almacenamiento asignado sea un objeto.

- Devuelve un puntero a los objetos de un tipo de puntero derivado de *new-type-name* o *type-name*. El programa usa este puntero para tener acceso al objeto recién asignado.

El operador **new** invoca el operador de función **new**. Para matrices de cualquier tipo y para objetos que no son de tipos de **clase**, **struct**o **union,** se llama a una función global, **::operator new**, para asignar almacenamiento. Los objetos de tipo de clase pueden definir su propia función miembro estática de **operador nueva** por clase.

Cuando el compilador encuentra el operador **new** para asignar un objeto `type`de tipo **type**, emite una llamada a **::operator new( sizeof(** `type` **) )** o, si no se define ningún operador **nuevo** definido por el usuario, **::operator new( sizeof(** `type` **) )**. Por lo tanto, el **operador new** puede asignar la cantidad correcta de memoria para el objeto.

> [!NOTE]
> El argumento a **operator** `size_t`new es de tipo . Este tipo se \<define en \<direct.h>, \<malloc.h \<>, memory.h \<>, search.h \<>, stddef.h>, stdio.h>, \<stdlib.h>, \<string.h> y \<time.h>.

Una opción en la gramática permite la especificación de *la colocación* (consulte la gramática para [el nuevo operador](../cpp/new-operator-cpp.md)). El parámetro *placement* solo se puede utilizar para implementaciones definidas por el usuario del **operador new**; permite que se pase información adicional al **operador new**. Una expresión con un `T *TObject = new ( 0x0040 ) T;` campo de `T *TObject = T::operator new( sizeof( T ), 0x0040 );` *ubicación* como se traduce a `T *TObject = ::operator new( sizeof( T ), 0x0040 );`si la clase T tiene el operador miembro new, de lo contrario a .

La intención original del campo de *ubicación* era permitir que los objetos dependientes del hardware se asignaran en direcciones especificadas por el usuario.

> [!NOTE]
> Aunque el ejemplo anterior muestra solo un argumento en el campo *de ubicación,* no hay ninguna restricción en cuanto a cuántos argumentos adicionales se pueden pasar al **operador nuevo** de esta manera.

Incluso cuando se ha definido operator **new** para un tipo de clase, el operador global se puede utilizar utilizando la forma de este ejemplo:

```cpp
T *TObject =::new TObject;
```

El operador de`::`resolución de ámbito ( ) fuerza el uso del **nuevo** operador global.

## <a name="see-also"></a>Consulte también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[nuevos y eliminar operadores](../cpp/new-and-delete-operators.md)
