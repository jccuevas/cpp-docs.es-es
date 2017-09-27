---
title: Operador new (C++) | Documentos de Microsoft
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
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a7386d45f5188e7217ebfd4c235c0763bfd70044
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="new-operator-c"></a>new (Operador) (C++)
Asigna memoria para un objeto o una matriz de objetos de *nombre-tipo* del almacén disponible y devuelve un puntero con tipo adecuado distinto de cero para el objeto.  
  
> [!NOTE]
>  Las extensiones de componentes de Microsoft C++ proporcionan compatibilidad para que la palabra clave `new` agregue entradas de ranura de vtable. Para obtener más información, vea [new (nueva ranura en vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[::] new [placement] new-type-name [new-initializer]  
[::] new [placement] ( type-name ) [new-initializer]  
```  
  
## <a name="remarks"></a>Comentarios  
 Si no lo consigue, **nueva** devuelve cero o produce una excepción; vea [el nuevo y eliminar operadores](../cpp/new-and-delete-operators.md) para obtener más información. Puede cambiar este comportamiento predeterminado escribiendo una rutina de control de excepciones personalizada y llamando a la [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) función de biblioteca en tiempo de ejecución con el nombre de función como su argumento.  
  
 Para obtener información sobre cómo crear un objeto en el montón administrado, consulte [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
 Cuando **nueva** es usa para asignar memoria para un objeto de clase de C++, el constructor del objeto se llama después de haber asignado la memoria.  
  
 Use la [eliminar](../cpp/delete-operator-cpp.md) operador que se va a desasignar la memoria asignada con el **nueva** operador.  
  
 En el ejemplo siguiente se asigna y se libera una matriz bidimensional de caracteres de tamaño `dim` por 10. Al asignar una matriz multidimensional, todas las dimensiones excepto la primera deben ser expresiones constantes que se evalúen como valores positivos; la dimensión de la matriz del extremo izquierdo puede ser cualquier expresión que se evalúe como un valor positivo. Al asignar una matriz mediante la **nueva** (operador), la primera dimensión puede ser cero: el **nueva** operador devuelve un puntero único.  
  
```  
char (*pchar)[10] = new char[dim][10];  
delete [] pchar;  
```  
  
 El *nombre-tipo* no puede contener **const**, `volatile`, declaraciones de clase ni declaraciones de enumeración. Por consiguiente, la siguiente expresión no es válida:  
  
```  
volatile char *vch = new volatile char[20];  
```  
  
 El **nueva** operador no asignar tipos de referencia porque no son objetos.  
  
 El **nueva** operador no se puede usar para asignar una función, pero se puede utilizar para asignar punteros a funciones. En el ejemplo siguiente se asigna y se libera una matriz de siete punteros a funciones que devuelven enteros.  
  
```  
int (**p) () = new (int (*[7]) ());  
delete *p;  
```  
  
 Si utiliza el operador **nueva** sin ningún argumento adicional y compila con la [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md), o [/EHs](../build/reference/eh-exception-handling-model.md) opción, el compilador realizará generar código para llamar al operador **eliminar** si el constructor produce una excepción.  
  
 En la lista siguiente se describe los elementos de la gramática de **nueva**:  
  
 *selección de ubicación*  
 Proporciona una manera de pasar argumentos adicionales si se sobrecarga **nueva**.  
  
 *nombre de tipo*  
 Especifica el tipo que se va a asignar; puede ser un tipo integrado o un tipo definido por el usuario. Si la especificación de tipo es compleja, puede ir entre paréntesis para forzar el orden de enlace.  
  
 *initializer*  
 Proporciona un valor para el objeto inicializado. No se pueden especificar inicializadores para matrices. El **nueva** operador creará las matrices de objetos únicamente si la clase tiene un constructor predeterminado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se asigna una matriz de caracteres y un objeto de clase `CName` y después se liberan.  
  
```  
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
 Si usa el nuevo formato de ubicación de la **nueva** (operador), el formato con argumentos además del tamaño de la asignación, el compilador no admite un formato de ubicación de la **eliminar** operador si el constructor produce una excepción. Por ejemplo:  
  
```  
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
 Opcional *inicializador* campo se incluye en la gramática de la **nueva** operador. Esto permite que los nuevos objetos se inicialicen con constructores definidos por el usuario. Para obtener más información acerca de cómo se realiza la inicialización, vea [inicializadores](../cpp/initializers.md). En el ejemplo siguiente se muestra cómo utilizar una expresión de inicialización con el **nueva** operador:  
  
```  
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
  
 En este ejemplo, el objeto `CheckingAcct` se asigna mediante el **nueva** se especifica el operador, pero ninguna inicialización predeterminada. Por lo tanto, se llama al constructor predeterminado para la clase, `Acct()`. El objeto `SavingsAcct` se asigna de la misma manera, salvo que se inicializa explícitamente en 34,98. Dado que 34,98 es de tipo **doble**, se llama al constructor que toma un argumento de ese tipo para controlar la inicialización. Finalmente, el tipo `HowMuch` que no es de clase se inicializa en 43,0.  
  
 Si un objeto es de un tipo de clase y esa clase tiene constructores (como en el ejemplo anterior), se puede inicializar el objeto de la **nueva** operador solo si se cumple una de estas condiciones:  
  
-   Los argumentos proporcionados en el inicializador concuerdan con los de un constructor.  
  
-   La clase tiene un constructor predeterminado (un constructor al que se puede llamar sin argumentos).  
  
 No puede realizarse ninguna inicialización explícita por elemento al asignar matrices mediante la **nueva** operador; sólo el constructor predeterminado, si está presente, se llama. Vea [argumentos predeterminados](../cpp/default-arguments.md) para obtener más información.  
  
 Si se produce un error en la asignación de memoria (`operator new` devuelve un valor de 0), no se realiza ninguna inicialización. Esto protege contra intentos de inicializar datos que no existen.  
  
 Como sucede con las llamadas a funciones, no se define el orden en que se evalúan las expresiones inicializadas. Además, no debe dar por hecho que estas expresiones se hayan evaluado totalmente antes de que se realice la asignación de memoria. Si se produce un error en la asignación de memoria y la **nueva** operador devuelve cero, algunas expresiones en el inicializador no se hayan evaluado.  
  
## <a name="lifetime-of-objects-allocated-with-new"></a>Duración de objetos asignados con new  
 Objetos asignados con el **nueva** operador no se destruyen cuando se sale del ámbito en el que se definen. Dado que la **nueva** operador devuelve un puntero a los objetos que asigna, el programa debe definir un puntero con el ámbito adecuado para tener acceso a esos objetos. Por ejemplo:  
  
```  
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
 El *expresión de asignación* : la expresión que contiene el **nueva** operador: hace tres cosas:  
  
-   Busca y reserva el almacenamiento para el objeto o los objetos a asignar. Cuando se completa esta fase, se asigna la cantidad correcta de almacenamiento, pero no es todavía un objeto.  
  
-   Inicializa los objetos. Una vez completada la inicialización, hay suficiente información presente para que el almacenamiento asignado sea un objeto.  
  
-   Devuelve un puntero a los objetos de un tipo de puntero derivado de *nuevo nombre de tipo* o *nombre de tipo*. El programa usa este puntero para tener acceso al objeto recién asignado.  
  
 El **nueva** operador invoca la función `operator new`. Para las matrices de cualquier tipo y para los objetos que no son de **clase**, `struct`, o **union** tipos, una función global, **:: new (operador)**, se llama para asignar el almacenamiento. Los objetos de tipo de clase pueden definir su propia función de miembro estática `operator new` clase por clase.  
  
 Cuando el compilador encuentra la **nueva** operador que se va a asignar un objeto de tipo `type`, emite una llamada a `type` **:: operador new (sizeof (** `type` **)) ** o, si no definido por el usuario `operator new` se define, **:: operador new (sizeof (** `type` **))**. Por lo tanto, la **nueva** operador puede asignar la cantidad correcta de memoria para el objeto.  
  
> [!NOTE]
>  El argumento `operator new` es de tipo **size_t**. Este tipo se define en DIRECT.H, MALLOC.H, MEMORY.H, SEARCH.H, STDDEF.H, STDIO.H, STDLIB.H, STRING.H, y TIME.H.  
  
 Una opción en la gramática permite la especificación de *colocación* (vea la gramática de [operador new](../cpp/new-operator-cpp.md)). El *colocación* parámetro se puede utilizar solo para implementaciones definidas por el usuario de `operator new`; permite que la información adicional que se pasan a `operator new`. Una expresión con un *colocación* campo como `T *TObject = new ( 0x0040 ) T;` se traduce a `T *TObject = T::operator new( sizeof( T ), 0x0040 );` si la clase T tiene el operador de miembro nueva, en caso contrario para `T *TObject = ::operator new( sizeof( T ), 0x0040 );`.  
  
 La intención original de la *colocación* campo es permitir que los objetos dependientes de hardware se asignen a direcciones especificadas por el usuario.  
  
> [!NOTE]
>  Aunque el ejemplo anterior muestra un único argumento en el *colocación* campo, no hay ninguna restricción sobre cuántos argumentos adicionales se pueden pasar a `operator new` este modo.  
  
 Aunque se haya definido `operator new` para un tipo de clase, el operador global se puede usar con la forma de este ejemplo:  
  
```  
T *TObject =::new TObject;  
```  
  
 El operador de resolución de ámbito (`::`) fuerza el uso de la información global **nueva** operador.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [nueva y eliminar operadores](../cpp/new-and-delete-operators.md)
