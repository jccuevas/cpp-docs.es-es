---
title: nuevos operadores y delete | Documentos de Microsoft
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
ms.openlocfilehash: a7f411d05491294421202ae6d8a1b7cbbb4e1d47
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423961"
---
# <a name="new-and-delete-operators"></a>Operadores new y delete

C++ admite la asignación dinámica de asignación y desasignación de objetos mediante el [nueva](../cpp/new-operator-cpp.md) y [eliminar](../cpp/delete-operator-cpp.md) operadores. Estos operadores asignan memoria para los objetos de un conjunto denominado almacén libre. El `new` operador llama a la función especial [new (operador)](../cpp/new-operator-cpp.md)y el `delete` operador llama a la función especial [operador delete](../cpp/delete-operator-cpp.md).  
  
 El `new` función de la biblioteca estándar de C++ admite el comportamiento especificado en el estándar de C++, que consiste en producir una excepción std:: bad_alloc si se produce un error en la asignación de memoria. Si aún desea la versión no producen excepciones de `new`, vincule el programa con nothrownew.obj. Sin embargo, cuando se vincula con nothrownew.obj, el valor predeterminado `operator new` en la biblioteca estándar de C++ deja de funcionar.  
  
 Para obtener una lista de los archivos de biblioteca que componen la biblioteca en tiempo de ejecución de C y la biblioteca estándar de C++, vea [características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).  
  
##  <a id="new_operator"> </a> El operador new  
 Cuando una instrucción como la siguiente se encuentra en un programa, se convierte a una llamada a la función `operator new`:  
  
```cpp  
char *pch = new char[BUFFER_SIZE];  
```  
  
Si la solicitud es de cero bytes de almacenamiento, **new (operador)** devuelve un puntero a un objeto (es decir, las llamadas repetidas a **new (operador)** devuelven punteros diferentes). Si no hay memoria suficiente para la solicitud de asignación, **new (operador)** produce una excepción std:: bad_alloc o devuelve **nullptr** si ha vinculado en no producen excepciones `operator new` admite.  
  
Puede escribir una rutina que intenta liberar memoria y vuelva a intentar la asignación; vea [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) para obtener más información. Para obtener más detalles sobre el esquema de recuperación, vea la sección de memoria insuficiente de control de este tema.  

  
Los dos ámbitos para las funciones `operator new` se describen en la tabla siguiente.  
  
### <a name="scope-for-operator-new-functions"></a>Ámbito de funciones operator new  
  
|Operador|Ámbito|  
|--------------|-----------|  
|**:: new (operador)**|Global|  
|*nombre de la clase* **:: new (operador)**|Clase|  
  
 El primer argumento **new (operador)** debe ser de tipo **size_t** (un tipo definido en \<stddef.h >), y el tipo de valor devuelto es siempre **void \***  .  
  
 Global **new (operador)** función se llama cuando el **nueva** operador se usa para asignar objetos de los tipos integrados, objetos de tipo de clase que no contienen definidos por el usuario **new (operador)** funciones y matrices de cualquier tipo. Cuando el **nueva** operador se usa para asignar objetos de un tipo de clase donde un **new (operador)** se define, esa clase **new (operador)** se llama.  
  
 Un **new (operador)** función definida para una clase es una función miembro estática (que no es posible, por lo tanto, ser virtual) que oculta la información global de **new (operador)** función para los objetos de ese tipo de clase. Considere el caso donde **nueva** se utiliza para asignar y establecer la memoria en un valor determinado:  
  
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
  
 El argumento proporcionado entre paréntesis a **nueva** se pasa a `Blanks::operator new` como el `chInit` argumento. Sin embargo, la información global de **new (operador)** función está oculta, haciendo que el código como el siguiente para generar un error:  
  
```cpp  
Blanks *SomeBlanks = new Blanks;  
```  
  
 En tipos de Visual C++ 5.0 y versiones anteriores, no es de clase y todas las matrices (independientemente de si eran de **clase** tipo) asignados mediante el **nueva** operador siempre usa la información global **new (operador)** (función).  
  
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
 Memoria que se asigna dinámicamente mediante la **nueva** operador se puede liberar con la **eliminar** operador. El operador delete llama el **operador delete** función, lo que libera memoria para el grupo disponible. Mediante el **eliminar** operador también hace que el destructor de clase (si hay alguno) que se llame a.  
  
 Hay globales y de ámbito de clase **operador delete** funciones. Solo un **operador delete** función se puede definir para una clase dada; si se define, oculta la información global de **operador delete** función. Global **operador delete** siempre se llama la función de las matrices de cualquier tipo.  
  
 Global **operador delete** función. Hay dos formas para global **operador delete** y miembros de clase **operador delete** funciones:  
  
```cpp  
void operator delete( void * );  
void operator delete( void *, size_t );  
```  
  
 Solo una de las dos formas anteriores puede estar presente para una clase determinada. La primera forma toma un solo argumento de tipo **void \*** , que contiene un puntero al objeto que se va a desasignar. El segundo formulario: desasignación de tamaño: toma dos argumentos, el primero de los cuales es un puntero al bloque de memoria para cancelar la asignación y el segundo de los cuales es el número de bytes que se va a desasignar. Es el tipo de valor devuelto de ambas formas `void` (**operador delete** no puede devolver un valor).  
  
 El propósito de la segunda forma es acelerar la búsqueda de la categoría de tamaño correcto del objeto que se puede eliminar, que a menudo no se almacenan unos junto a la asignación de sí mismo y probablemente sin almacenar en caché; la segunda forma es especialmente útil cuando un **operador delete** función de una clase base se utiliza para eliminar un objeto de una clase derivada.  
  
 El **operador delete** función es estática; por lo tanto, no puede ser virtual. El `operator delete` función obedece el control de acceso, como se describe en [Control de acceso a miembros](../cpp/member-access-control-cpp.md).  
  
 En el ejemplo siguiente se muestra definido por el usuario **new (operador)** y **operador delete** funciones diseñadas para registrar asignaciones y desasignaciones de memoria:  
  
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
  
 El código anterior se puede utilizar para detectar "pérdidas de memoria", es decir, la memoria que se asigna en el almacén libre pero que nunca se libera. Para realizar esta detección, la información global de **nueva** y **eliminar** se volvió a definir operadores para determinar la asignación y desasignación de memoria.  
  
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

