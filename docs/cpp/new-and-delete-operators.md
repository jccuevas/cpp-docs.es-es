---
title: nuevo y eliminar operadores | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- delete_cpp
- new
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++], dynamic allocation of objects
- nothrownew.obj
- delete keyword [C++], syntax
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a1470c544e624de4ef9fb570859dca9b282edde
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208071"
---
# <a name="new-and-delete-operators"></a>Operadores new y delete

C++ admite la asignación dinámica y la desasignación de objetos mediante el [nueva](../cpp/new-operator-cpp.md) y [eliminar](../cpp/delete-operator-cpp.md) operadores. Estos operadores asignan memoria para los objetos de un conjunto denominado almacén libre. El **nueva** operador llama a la función especial [new (operador)](../cpp/new-operator-cpp.md)y el **eliminar** operador llama a la función especial [operador delete](../cpp/delete-operator-cpp.md).  
  
 El **nuevo** función en la biblioteca estándar de C++ admite el comportamiento especificado en el estándar de C++, que se usa para producir una excepción std:: bad_alloc si se produce un error en la asignación de memoria. Si aún desea la versión no producen excepciones de **nuevo**, vincule el programa con nothrownew.obj. Sin embargo, cuando se vincula con nothrownew.obj, el valor predeterminado **operador new** en la biblioteca estándar de C++ ya no funciona.  
  
 Para obtener una lista de los archivos de biblioteca que componen la biblioteca en tiempo de ejecución de C y la biblioteca estándar de C++, vea [características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).  
  
##  <a id="new_operator"> </a> El operador new  
 Cuando se encuentra una instrucción como la siguiente en un programa, convierte en una llamada a la función **new (operador)**:  
  
```cpp  
char *pch = new char[BUFFER_SIZE];  
```  
  
Si la solicitud es para cero bytes de almacenamiento, **new (operador)** devuelve un puntero a un objeto distinto (es decir, las llamadas repetidas a **operador new** devuelven punteros diferentes). Si no hay memoria suficiente para la solicitud de asignación, **new (operador)** produce una excepción std:: bad_alloc o devuelve **nullptr** si ha vinculado en no producen excepciones **operador new** admite.  
  
Puede escribir una rutina que intente liberar memoria y vuelva a intentar la asignación; consulte [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) para obtener más información. Para obtener más detalles sobre el esquema de recuperación, consulte la sección de memoria insuficiente de control de este tema.  

  
Los dos ámbitos para **operador new** funciones se describen en la tabla siguiente.  
  
### <a name="scope-for-operator-new-functions"></a>Ámbito de funciones operator new  
  
|Operador|Ámbito|  
|--------------|-----------|  
|**:: new (operador)**|Global|  
|*nombre de la clase* **:: new (operador)**|Clase|  
  
 El primer argumento **new (operador)** debe ser de tipo `size_t` (un tipo definido en \<stddef.h >), y el tipo de valor devuelto es siempre **void** <strong>\*</strong>.  
  
 Global **new (operador)** función se llama cuando el **nueva** operador se usa para asignar objetos de tipos integrados, objetos del tipo de clase que no tienen definido por el usuario **operador new** funciones y las matrices de cualquier tipo. Cuando el **nueva** operador se usa para asignar objetos de un tipo de clase donde un **new (operador)** está definido, esa clase **new (operador)** se llama.  
  
 Un **new (operador)** función definida para una clase es una función miembro estática (que no es posible, por lo tanto, ser virtual) que oculta la información global **operador new** función para los objetos de ese tipo de clase. Considere el caso donde **nuevo** se usa para asignar y establecer la memoria con un valor determinado:  
  
```cpp  
// spec1_the_operator_new_function1.cpp  
#include <malloc.h>  
#include <memory.h>  
  
class Blanks  
{  
public:  
    Blanks(){}  
    void *operator new( size_t stAllocateBlock, char chInit );  
};  
void *Blanks::operator new( size_t stAllocateBlock, char chInit )  
{  
    void *pvTemp = malloc( stAllocateBlock );  
    if( pvTemp != 0 )  
        memset( pvTemp, chInit, stAllocateBlock );  
    return pvTemp;  
}  
// For discrete objects of type Blanks, the global operator new function  
// is hidden. Therefore, the following code allocates an object of type  
// Blanks and initializes it to 0xa5  
int main()  
{  
   Blanks *a5 = new(0xa5) Blanks;  
   return a5 != 0;  
}  
```  
  
 El argumento proporcionado entre paréntesis a **nueva** se pasa a `Blanks::operator new` como el `chInit` argumento. Sin embargo, la información global **operador new** función está oculta, haciendo que el código como el siguiente para generar un error:  
  
```cpp  
Blanks *SomeBlanks = new Blanks;  
```  
  
 En tipos de Visual C++ 5.0 y versiones anteriores, utilizaban y todas las matrices (independientemente de si eran de **clase** tipo) asignados mediante el **nueva** operador siempre utiliza global **operador new** función.  
  
 A partir de Visual C++ 5.0, el compilador admite la matriz de miembros **nueva** y **eliminar** operadores en una declaración de clase. Por ejemplo:  
  
```cpp  
// spec1_the_operator_new_function2.cpp  
class MyClass  
{  
public:  
   void * operator new[] (size_t)  
   {  
      return 0;  
   }  
   void   operator delete[] (void*)  
   {  
   }  
};  
  
int main()   
{  
   MyClass *pMyClass = new MyClass[5];  
   delete [] pMyClass;  
}  
```  
  
### <a name="handling-insufficient-memory"></a>Controlar la memoria insuficiente  
 La prueba de error de asignación de memoria se puede realizar con código como el siguiente:  
  
```cpp  
// insufficient_memory_conditions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
#define BIG_NUMBER 100000000  
int main() {  
   int *pI = new int[BIG_NUMBER];  
   if( pI == 0x0 ) {  
      cout << "Insufficient memory" << endl;  
      return -1;  
   }  
}  
```  
  
 Hay otras maneras de controlar las solicitudes de asignación de memoria con errores: escribir una rutina de recuperación personalizada para controlar el error, a continuación, registre la función mediante una llamada a la [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) función en tiempo de ejecución.  
  
##  <a id="delete_operator"> </a> El operador delete  
 Memoria que se asigna dinámicamente mediante el **nueva** operador se puede liberar con la **eliminar** operador. El operador delete llama a la **operador delete** función, lo que libera memoria para el grupo disponible. Mediante el **eliminar** operador también hace que el destructor de clase (si hay alguno) que se llame.  
  
 Hay globales y de ámbito de clase **operador delete** funciones. Solo un **operador delete** función se puede definir para una clase dada; si se define, oculta la información global **operador delete** función. Global **operador delete** siempre se llama a las matrices de cualquier tipo de función.  
  
 Global **operador delete** función. Hay dos formas para global **operador delete** y miembro de clase **operador delete** funciones:  
  
```cpp  
void operator delete( void * );  
void operator delete( void *, size_t );  
```  
  
 Solo una de las dos formas anteriores puede estar presente para una clase determinada. El primer formulario toma un único argumento de tipo `void *`, que contiene un puntero para el objeto que se va a desasignar. La segunda forma, desasignación de tamaño: toma dos argumentos, el primero de ellos es un puntero al bloque de memoria para desasignar y el segundo de los cuales es el número de bytes que se desasigne. Es el tipo de valor devuelto de ambas formas **void** (**operador delete** no puede devolver un valor).  
  
 La intención de la segunda forma es aumentar la velocidad de búsqueda de la categoría de tamaño correcto del objeto que se va a eliminar, que a menudo no se almacena junto a la asignación de sí mismo y probablemente no almacenado en caché; la segunda forma es especialmente útil cuando un **operador delete** función de una clase base se usa para eliminar un objeto de una clase derivada.  
  
 El **operador delete** función es estática; por lo tanto, no puede ser virtual. El **operador delete** función obedece el control de acceso, como se describe en [Control de acceso de miembro](../cpp/member-access-control-cpp.md).  
  
 El ejemplo siguiente se muestra definido por el usuario **new (operador)** y **operador delete** funciones diseñadas para registrar asignaciones y desasignaciones de memoria:  
  
```cpp  
// spec1_the_operator_delete_function1.cpp  
// compile with: /EHsc  
// arguments: 3  
#include <iostream>  
using namespace std;  
  
int fLogMemory = 0;      // Perform logging (0=no; nonzero=yes)?  
int cBlocksAllocated = 0;  // Count of blocks allocated.  
  
// User-defined operator new.  
void *operator new( size_t stAllocateBlock ) {  
   static int fInOpNew = 0;   // Guard flag.  
  
   if ( fLogMemory && !fInOpNew ) {  
      fInOpNew = 1;  
      clog << "Memory block " << ++cBlocksAllocated  
          << " allocated for " << stAllocateBlock  
          << " bytes\n";  
      fInOpNew = 0;  
   }  
   return malloc( stAllocateBlock );  
}  
  
// User-defined operator delete.  
void operator delete( void *pvMem ) {  
   static int fInOpDelete = 0;   // Guard flag.  
   if ( fLogMemory && !fInOpDelete ) {  
      fInOpDelete = 1;  
      clog << "Memory block " << cBlocksAllocated--  
          << " deallocated\n";  
      fInOpDelete = 0;  
   }  
  
   free( pvMem );  
}  
  
int main( int argc, char *argv[] ) {  
   fLogMemory = 1;   // Turn logging on  
   if( argc > 1 )  
      for( int i = 0; i < atoi( argv[1] ); ++i ) {  
         char *pMem = new char[10];  
         delete[] pMem;  
      }  
   fLogMemory = 0;  // Turn logging off.  
   return cBlocksAllocated;  
}  
```  
  
 El código anterior se puede utilizar para detectar "pérdidas de memoria", es decir, la memoria que se asigna en el almacén libre pero que nunca se libera. Para realizar esta detección, global **nueva** y **eliminar** se vuelven a definir operadores para la asignación y desasignación de memoria.  
  
 A partir de Visual C++ 5.0, el compilador admite la matriz de miembros **nueva** y **eliminar** operadores en una declaración de clase. Por ejemplo:  
  
```cpp  
// spec1_the_operator_delete_function2.cpp  
// compile with: /c  
class X  {  
public:  
   void * operator new[] (size_t) {  
      return 0;  
   }  
   void operator delete[] (void*) {}  
};  
  
void f() {  
   X *pX = new X[5];  
   delete [] pX;  
}  
```  