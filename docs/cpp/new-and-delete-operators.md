---
title: Operadores new y delete
ms.date: 11/19/2019
f1_keywords:
- delete_cpp
- new
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: c64b15f1e1e63b1e743743883429ffd11007de0a
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246445"
---
# <a name="new-and-delete-operators"></a>Operadores new y delete

C++admite la asignación y desasignación dinámica de objetos mediante los operadores [New](new-operator-cpp.md) y [Delete](delete-operator-cpp.md) . Estos operadores asignan memoria para los objetos de un conjunto denominado almacén libre. El operador **New** llama a la función especial [Operator New](new-operator-cpp.md)y el operador **Delete** llama a la función especial [operator delete](delete-operator-cpp.md).

La **nueva** función de la C++ biblioteca estándar admite el comportamiento especificado en el C++ estándar, que consiste en iniciar una excepción STD:: bad_alloc si se produce un error en la asignación de memoria. Si todavía desea la versión de no lanzamiento de **nueva**, vincule el programa con nothrownew. obj. Sin embargo, al vincular con nothrownew. obj, el **operador predeterminado New** en C++ la biblioteca estándar ya no funciona.

Para obtener una lista de los archivos de biblioteca que componen la biblioteca en C++ tiempo de ejecución de C y la biblioteca estándar, vea características de la [biblioteca CRT](../c-runtime-library/crt-library-features.md).

##  <a id="new_operator"></a> Operador New

Cuando se encuentra una instrucción como la siguiente en un programa, se convierte en una llamada al operador de función **New**:

```cpp
char *pch = new char[BUFFER_SIZE];
```

Si la solicitud es para cero bytes de almacenamiento, **Operator New** devuelve un puntero a un objeto distinto (es decir, las llamadas repetidas a **Operator New** devuelven punteros diferentes). Si no hay memoria suficiente para la solicitud de asignación, el **operador New** inicia una excepción `std::bad_alloc`, o devuelve **nullptr** si se ha vinculado en la **nueva** compatibilidad con el operador de no generación.

Puede escribir una rutina que intente liberar memoria y reintentar la asignación. consulte [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) para obtener más información. Para obtener más detalles sobre el esquema de recuperación, consulte la sección controlar la memoria insuficiente de este tema.

Los dos ámbitos de las funciones **New de operador** se describen en la tabla siguiente.

### <a name="scope-for-operator-new-functions"></a>Ámbito de las funciones New de operador

|Operador|Ámbito|
|--------------|-----------|
|**:: Operator New**|Global|
|*Class-Name* **:: Operator New**|Clase|

El primer argumento de **Operator New** debe ser de tipo `size_t` (un tipo definido en \<stddef. h >) y el tipo de valor devuelto siempre es **void** <strong>\*</strong>.

Se llama a la función global **New (operador** ) cuando se usa el operador **New** para asignar objetos de tipos integrados, objetos de tipo de clase que no contienen funciones **New de operadores** definidos por el usuario y matrices de cualquier tipo. Cuando el operador **New** se usa para asignar objetos de un tipo de clase en el que se define un **operador New** , se llama al **operador New** de esa clase.

Una función **Operator New** definida para una clase es una función miembro estática (que no puede, por tanto, ser virtual) que oculta la función global **Operator New** para los objetos de ese tipo de clase. Considere el caso en el que se usa **New** para asignar y establecer la memoria en un valor determinado:

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

El argumento proporcionado entre paréntesis a **New** se pasa a `Blanks::operator new` como el argumento `chInit`. Sin embargo, se oculta la función global **New (operador** ), que hace que el código como el siguiente genere un error:

```cpp
Blanks *SomeBlanks = new Blanks;
```

El compilador admite operadores **New** y **Delete** de matriz de miembros en una declaración de clase. Por ejemplo:

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

Las pruebas de asignación de memoria con errores se pueden realizar como se muestra aquí:

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

Hay otra manera de controlar las solicitudes de asignación de memoria con error. Escriba una rutina de recuperación personalizada para controlar este tipo de error y, a continuación, registre la función mediante una llamada a la función de tiempo de ejecución [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) .

##  <a id="delete_operator"></a> El operador Delete

La memoria que se asigna dinámicamente mediante el operador **New** se puede liberar mediante el operador **Delete** . El operador Delete llama a la función **operator delete** , que libera la memoria de nuevo en el Grupo disponible. El uso del operador **Delete** también hace que se llame al destructor de clase (si hay alguno).

Hay funciones de **eliminación de operadores** globales y de ámbito de clase. Solo se puede definir una función de **eliminación de operador** para una clase determinada; Si se define, oculta la función de **eliminación de operador** global. Siempre se llama a la función global **operator delete** para matrices de cualquier tipo.

La función de **eliminación de operador** global. Existen dos formas para las funciones de eliminación y de **operador** de **miembro de clase** globales:

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Solo una de las dos formas anteriores puede estar presente para una clase determinada. La primera forma toma un solo argumento de tipo `void *`, que contiene un puntero al objeto que se va a desasignar. La segunda forma, la desasignación de tamaño, toma dos argumentos, el primero es un puntero al bloque de memoria que se va a desasignar y el segundo es el número de bytes que se van a desasignar. El tipo de valor devuelto de ambos formularios es **void** (el**operador Delete** no puede devolver un valor).

La intención del segundo formulario es acelerar la búsqueda de la categoría de tamaño correcto del objeto que se va a eliminar, que a menudo no se almacena cerca de la propia asignación y es probable que no esté almacenada en caché. La segunda forma es útil cuando se usa una función de **eliminación de operador** de una clase base para eliminar un objeto de una clase derivada.

La función **operator delete** es estática; por lo tanto, no puede ser virtual. La función **operator delete** obedece el control de acceso, tal y como se describe en [member-access control](member-access-control-cpp.md).

En el ejemplo siguiente se muestran las funciones **de operador y** **eliminación** definidas por el usuario, diseñadas para registrar asignaciones y desasignaciones de memoria:

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

El código anterior se puede utilizar para detectar "pérdidas de memoria", es decir, la memoria que se asigna en el almacén libre pero que nunca se libera. Para realizar esta detección, se han redefinido los operadores globales **New** y **Delete** para contar la asignación y desasignación de memoria.

El compilador admite operadores **New** y **Delete** de matriz de miembros en una declaración de clase. Por ejemplo:

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
