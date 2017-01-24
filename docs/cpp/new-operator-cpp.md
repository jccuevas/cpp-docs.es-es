---
title: "new (Operador) (C++) | Microsoft Docs"
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
  - "new (palabra clave) [C++]"
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# new (Operador) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asigna memoria para un objeto o una matriz de objetos de *type\-name* del almacén disponible y devuelve un puntero con un tipo adecuado distinto de cero al objeto.  
  
> [!NOTE]
>  Las extensiones de componentes de Microsoft C\+\+ proporcionan compatibilidad para que la palabra clave `new` agregue entradas de ranura de vtable.  Para obtener más información, vea [new \(nueva ranura en vtable\)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
## Sintaxis  
  
```  
[::] new [placement] new-type-name [new-initializer]  
[::] new [placement] ( type-name ) [new-initializer]  
```  
  
## Comentarios  
 Si esta operación no se realiza correctamente, **new** devuelve cero o produce una excepción; vea [Los operadores new y delete](../cpp/new-and-delete-operators.md) para obtener más información.  Puede cambiar este comportamiento predeterminado escribiendo una rutina de control de excepciones personalizada y llamando a la función de biblioteca en tiempo de ejecución [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md) con el nombre de función como su argumento.  
  
 Para obtener información sobre cómo crear un objeto en el montón administrado, vea [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
 Cuando **new** se utiliza para asignar memoria para un objeto de clase de C\+\+, se llama al constructor del objeto después de que se asigna la memoria.  
  
 Utilice el operador [delete](../cpp/delete-operator-cpp.md) para desasignar la memoria asignada con el operador **new**.  
  
 En el ejemplo siguiente se asigna y se libera una matriz bidimensional de caracteres de tamaño `dim` por 10.  Al asignar una matriz multidimensional, todas las dimensiones excepto la primera deben ser expresiones constantes que se evalúen como valores positivos; la dimensión de la matriz del extremo izquierdo puede ser cualquier expresión que se evalúe como un valor positivo.  Al asignar una matriz mediante el operador **new**, la primera dimensión puede ser cero; el operador **new** devuelve un puntero único.  
  
```  
char (*pchar)[10] = new char[dim][10];  
delete [] pchar;  
```  
  
 El elemento *type\-name* no puede contener **const**, `volatile`, declaraciones de clase ni declaraciones de enumeración.  Por consiguiente, la siguiente expresión no es válida:  
  
```  
volatile char *vch = new volatile char[20];  
```  
  
 El operador **new** no asigna tipos de referencia porque no son objetos.  
  
 El operador **new** no se puede utilizar para asignar una función, pero sí para asignar punteros a funciones.  En el ejemplo siguiente se asigna y se libera una matriz de siete punteros a funciones que devuelven enteros.  
  
```  
int (**p) () = new (int (*[7]) ());  
delete *p;  
```  
  
 Si usa el operador **new** sin ningún argumento adicional y compila con la opción [\/GX](../build/reference/gx-enable-exception-handling.md), [\/EHa](../build/reference/eh-exception-handling-model.md) o [\/EHs](../build/reference/eh-exception-handling-model.md), el compilador generará código para llamar al operador **delete** si el constructor produce una excepción.  
  
 En la lista siguiente se describen los elementos de la gramática de **new**:  
  
 *placement*  
 Proporciona una manera de pasar argumentos adicionales si se sobrecarga **new**.  
  
 *type\-name*  
 Especifica el tipo que se va a asignar; puede ser un tipo integrado o un tipo definido por el usuario.  Si la especificación de tipo es compleja, puede ir entre paréntesis para forzar el orden de enlace.  
  
 *initializer*  
 Proporciona un valor para el objeto inicializado.  No se pueden especificar inicializadores para matrices.  El operador **new** creará las matrices de objetos únicamente si la clase tiene un constructor predeterminado.  
  
## Ejemplo  
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
  
## Ejemplo  
 Si utiliza el nuevo formato de ubicación del operador **new**, el formato con argumentos además del tamaño de asignación, el compilador no admite un formato de ubicación del operador **delete** si el constructor produce una excepción.  Por ejemplo:  
  
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
  
## Inicializar objetos asignados con new  
 Un campo *initializer* opcional se incluye en la gramática del operador **new**.  Esto permite que los nuevos objetos se inicialicen con constructores definidos por el usuario.  Para obtener más información sobre cómo se realiza la inicialización, vea [Inicializadores](../cpp/initializers.md).  En el ejemplo siguiente se muestra la forma de utilizar una expresión de inicialización con el operador **new**:  
  
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
  
 En este ejemplo, el objeto `CheckingAcct` se asigna utilizando el operador **new**, pero no se especifica ninguna inicialización predeterminada.  Por lo tanto, se llama al constructor predeterminado para la clase, `Acct()`.  El objeto `SavingsAcct` se asigna de la misma manera, salvo que se inicializa explícitamente en 34,98.  Dado que 34,98 es de tipo **double**, se llama al constructor que toma un argumento de ese tipo para controlar la inicialización.  Finalmente, el tipo `HowMuch` que no es de clase se inicializa en 43,0.  
  
 Si un objeto es de un tipo de clase y esa clase tiene constructores \(como en el ejemplo anterior\), el objeto se puede inicializar mediante el operador **new** solo si se cumple una de estas condiciones:  
  
-   Los argumentos proporcionados en el inicializador concuerdan con los de un constructor.  
  
-   La clase tiene un constructor predeterminado \(un constructor al que se puede llamar sin argumentos\).  
  
 El control de acceso y el control de ambigüedad se realizan en `operator new` y en los constructores de acuerdo con las reglas estipuladas en [Ambigüedad](http://msdn.microsoft.com/es-es/0b399cab-40a7-4e79-9278-05f40139a0e1) y en [Inicialización mediante el uso de funciones miembro especiales](http://msdn.microsoft.com/es-es/82223d73-64cb-4923-b678-78f9568ff3ca).  
  
 No puede realizarse ninguna inicialización explícita por elemento al asignar matrices mediante el operador **new**; solo se llama al constructor predeterminado, si existe.  Vea [Argumentos predeterminados](../cpp/default-arguments.md) para obtener más información.  
  
 Si se produce un error en la asignación de memoria \(`operator new` devuelve un valor de 0\), no se realiza ninguna inicialización.  Esto protege contra intentos de inicializar datos que no existen.  
  
 Como sucede con las llamadas a funciones, no se define el orden en que se evalúan las expresiones inicializadas.  Además, no debe dar por hecho que estas expresiones se hayan evaluado totalmente antes de que se realice la asignación de memoria.  Si se produce un error en la asignación de memoria y el operador **new** devuelve cero, es posible que algunas expresiones del inicializador no se hayan evaluado totalmente.  
  
## Duración de objetos asignados con new  
 Los objetos asignados con el operador **new** no se destruyen cuando se sale del ámbito en el que se definen.  Como el operador **new** devuelve un puntero a los objetos que asigna, el programa debe definir un puntero con el ámbito adecuado para tener acceso a esos objetos.  Por ejemplo:  
  
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
  
## Cómo funciona new  
 La expresión de asignación *allocation\-expression* –la expresión que contiene el operador **new**– hace tres cosas:  
  
-   Busca y reserva el almacenamiento para el objeto o los objetos a asignar.  Cuando se completa esta fase, se asigna la cantidad correcta de almacenamiento, pero no es todavía un objeto.  
  
-   Inicializa los objetos.  Una vez completada la inicialización, hay suficiente información presente para que el almacenamiento asignado sea un objeto.  
  
-   Devuelve un puntero a los objetos de un tipo de puntero derivado de *new\-type\-name* o *type\-name*.  El programa usa este puntero para tener acceso al objeto recién asignado.  
  
 El operador **new** invoca la función `operator new`.  Para las matrices de cualquier tipo y para objetos que no son de tipo **class**, `struct` o **union**, se llama a una función global, **::operator new**, para asignar almacenamiento.  Los objetos de tipo de clase pueden definir su propia función de miembro estática `operator new` clase por clase.  
  
 Cuando el compilador se encuentra con el operador **new** que asigna un objeto de tipo `type`, emite una llamada a `type`**::operator new\( sizeof\(** `type` **\) \)** o, si no hay ningún `operator new` definido por el usuario, **::operator new\( sizeof\(** `type` **\) \)**.  Por consiguiente, el operador **new** puede asignar la cantidad de memoria correcta para el objeto.  
  
> [!NOTE]
>  El argumento para `operator new` es de tipo **size\_t**.  Este tipo se define en DIRECT.H, MALLOC.H, MEMORY.H, SEARCH.H, STDDEF.H, STDIO.H, STDLIB.H, STRING.H, y TIME.H.  
  
 Una opción de la gramática permite la especificación de *placement* \(vea la gramática para [new \(Operador\)](../cpp/new-operator-cpp.md)\).  El parámetro *placement* solo se puede utilizar para las implementaciones definidas por el usuario de `operator new`; permite pasar información adicional a `operator new`.  Una expresión con un campo *placement* tal como `T *TObject = new ( 0x0040 ) T;` se convierte en `T *TObject = T::operator new( sizeof( T ), 0x0040 );` si la clase T tiene el operator new de miembro; si no, se convierte en `T *TObject = ::operator new( sizeof( T ), 0x0040 );`.  
  
 La intención original del campo *placement* es permitir que los objetos dependientes de hardware se asignen a direcciones especificadas por el usuario.  
  
> [!NOTE]
>  Aunque en el ejemplo anterior solo se muestra un argumento en el campo *placement*, no hay ninguna restricción sobre cuántos argumentos adicionales se pueden pasar a `operator new` de esta forma.  
  
 Aunque se haya definido `operator new` para un tipo de clase, el operador global se puede usar con la forma de este ejemplo:  
  
```  
T *TObject =::new TObject;  
```  
  
 El operador de resolución de ámbito \(`::`\) fuerza el uso del operador global **new**.  
  
## Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [operador new \(Función\)](../misc/operator-new-function.md)