---
title: Operadores new y delete
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: fd170c1500e2d80879fdd89f7d825930189ae942
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367885"
---
# <a name="new-and-delete-operators"></a>Operadores new y delete

C++ admite la asignación dinámica y la desasignación de objetos mediante los operadores [new](new-operator-cpp.md) y [delete.](delete-operator-cpp.md) Estos operadores asignan memoria para los objetos de un conjunto denominado almacén libre. El **nuevo** operador llama al [operador](new-operator-cpp.md)de función especial new y el operador **delete** llama al operador de función especial [delete](delete-operator-cpp.md).

La **nueva** función de la biblioteca estándar C++ admite el comportamiento especificado en el estándar C++, que consiste en producir una excepción std::bad_alloc si se produce un error en la asignación de memoria. Si todavía desea la versión no-lanzamiento de **new**, vincule su programa con nothrownew.obj. Sin embargo, cuando se vincula con nothrownew.obj, el operador predeterminado **nuevo** en la biblioteca estándar C++ ya no funciona.

Para obtener una lista de los archivos de biblioteca que componen la biblioteca en tiempo de ejecución de C y la biblioteca estándar C++, consulte Características de la [biblioteca CRT](../c-runtime-library/crt-library-features.md).

## <a name="the-new-operator"></a><a id="new_operator"> </a> El nuevo operador

Cuando se encuentra una instrucción como la siguiente en un programa, se traduce en una llamada al operador de función **new**:

```cpp
char *pch = new char[BUFFER_SIZE];
```

Si la solicitud es para cero bytes de almacenamiento, **el operador new** devuelve un puntero a un objeto distinto (es decir, llamadas repetidas al operador **new** devuelven punteros diferentes). Si no hay memoria suficiente para la solicitud `std::bad_alloc` de asignación, el operador **new** produce una excepción o devuelve **nullptr** si ha vinculado en el operador no producente **nueva** compatibilidad.

Puede escribir una rutina que intente liberar memoria y volver a intentar la asignación; consulte [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) para obtener más información. Para obtener más información sobre el esquema de recuperación, consulte la sección Control de memoria insuficiente de este tema.

Los dos ámbitos para las **nuevas** funciones del operador se describen en la tabla siguiente.

### <a name="scope-for-operator-new-functions"></a>Alcance para las nuevas funciones del operador

|Operator|Ámbito|
|--------------|-----------|
|**::operador nuevo**|Global|
|*nombre de clase* **::operador nuevo**|Clase|

El primer argumento para **operator** `size_t` new debe ser \<de tipo (un tipo definido en stddef.h>) y el tipo de valor devuelto siempre es **void** <strong>\*</strong>.

Se llama a la nueva función del **operador** global cuando se utiliza el operador **new** para asignar objetos de tipos integrados, objetos de tipo de clase que no contienen **funciones de operador** definidas por el usuario y matrices de ningún tipo. Cuando se utiliza el operador **new** para asignar objetos de un tipo de clase donde se define un **operador new,** se llama al **operador new** de esa clase.

Un **operador nueva** función definida para una clase es una función miembro estática (que, por lo tanto, no puede ser virtual) que oculta el operador global **nueva** función para los objetos de ese tipo de clase. Considere el caso donde **new** se utiliza para asignar y fijar la memoria a un valor dado:

```cpp
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

El argumento proporcionado entre paréntesis `Blanks::operator new` a `chInit` **new** se pasa como argumento. Sin embargo, la nueva función del **operador** global está oculta, lo que hace que el código como el siguiente genere un error:

```cpp
Blanks *SomeBlanks = new Blanks;
```

El compilador admite la matriz de miembros **new** y **delete** operadores en una declaración de clase. Por ejemplo:

```cpp
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

Las pruebas para la asignación de memoria fallida se pueden hacer como se muestra aquí:

```cpp
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

Hay otra manera de controlar las solicitudes de asignación de memoria con errores. Escriba una rutina de recuperación personalizada para controlar dicho error y, a continuación, registre la función llamando a la [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) función en tiempo de ejecución.

## <a name="the-delete-operator"></a><a id="delete_operator"> </a> El operador delete

La memoria que se asigna dinámicamente mediante el **operador new** se puede liberar mediante el operador **delete.** El operador delete llama a la función delete del **operador,** que libera memoria al grupo disponible. El uso del operador **delete** también hace que se llame al destructor de clase (si existe).

Hay funciones de eliminación de **operadores** globales y de ámbito de clase. Solo se puede definir una función **de eliminación** de operador para una clase determinada; si se define, oculta la función **de eliminación** del operador global. La función **global de eliminación** de operadores siempre se llama para matrices de cualquier tipo.

La función **de eliminación** del operador global. Existen dos formularios para las funciones de **eliminación** de operador global y **de eliminación** de operador de miembro de clase:

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Solo uno de los dos formularios anteriores puede estar presente para una clase determinada. El primer formulario toma un `void *`único argumento de tipo , que contiene un puntero al objeto que se va a desasignar. La segunda forma, la desasignación de tamaño, toma dos argumentos, el primero de los cuales es un puntero al bloque de memoria que se va a desasignar y el segundo es el número de bytes que se van a desasignar. El tipo de valor devuelto de ambos formularios es **void** **(operator delete** no puede devolver un valor).

La intención del segundo formulario es acelerar la búsqueda de la categoría de tamaño correcta del objeto que se va a eliminar, que a menudo no se almacena cerca de la propia asignación y probablemente sin almacenar en caché. El segundo formulario es útil cuando se utiliza una función **de eliminación** de operador de una clase base para eliminar un objeto de una clase derivada.

La función delete del **operador** es estática; por lo tanto, no puede ser virtual. La función delete del **operador** obedece al control de acceso, como se describe en [Member-Access Control](member-access-control-cpp.md).

En el ejemplo siguiente se muestran las funciones de **eliminación** de **operadores new** y operator definidas por el usuario diseñadas para registrar asignaciones y desasignaciones de memoria:

```cpp
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

El código anterior se puede utilizar para detectar "pérdidas de memoria", es decir, la memoria que se asigna en el almacén libre pero que nunca se libera. Para realizar esta detección, los operadores **globales new** y **delete** se redefinen para contar la asignación y la desasignación de memoria.

El compilador admite la matriz de miembros **new** y **delete** operadores en una declaración de clase. Por ejemplo:

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
