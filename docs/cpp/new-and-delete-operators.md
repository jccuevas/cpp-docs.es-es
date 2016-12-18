---
title: "Operadores new y delete | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "delete_cpp"
  - "new_cpp"
  - "new"
  - "delete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delete (palabra clave) [C++], sintaxis"
  - "new (palabra clave) [C++], asignación dinámica de objetos"
  - "nothrownew.obj"
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores new y delete
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ admite la asignación dinámica y la desasignación de objetos mediante los operadores [new](../cpp/new-operator-cpp.md) y [delete](../cpp/delete-operator-cpp.md).  Estos operadores asignan memoria para los objetos de un conjunto denominado almacén libre.  El operador `new` llama a la función especial [operador new](../misc/operator-new-function.md) y el operador `delete` llama a la función especial [operador delete](../misc/operator-delete-function.md).  
  
 En [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] .NET 2002, la función `new` de la biblioteca estándar de C\+\+ admitirá el comportamiento especificado en el estándar de C\+\+, que consiste en iniciar una excepción std::bad\_alloc si la asignación de memoria produce un error.  
  
 La función `new` de la biblioteca en tiempo de ejecución de C también iniciará una excepción std::bad\_alloc si la asignación de memoria produce un error.  
  
 Si aún desea usar la versión de `new` que no produce excepciones para la biblioteca en tiempo de ejecución de C, vincule el programa con nothrownew.obj.  Sin embargo, cuando se vincula con nothrownew.obj, el operador `new` de la biblioteca estándar de C\+\+ ya no funcionará.  
  
 Para obtener una lista de los archivos de biblioteca que componen la biblioteca de tiempo de ejecución de C y la biblioteca estándar de C\+\+, vea [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).  
  
## Operador new  
 Cuando una instrucción como la siguiente se encuentra en un programa, se convierte a una llamada a la función `operator new`:  
  
```  
char *pch = new char[BUFFER_SIZE];  
```  
  
 Si la solicitud es de cero bytes de almacenamiento, **new \(operador\)** devuelve un puntero a otro objeto \(es decir, las llamadas repetidas a **new \(operador\)** devuelven punteros diferentes\).  Si no hay memoria suficiente para la solicitud de asignación, **new \(operador\)** devuelve **NULL** o inicia una excepción \(vea [Operadores new y delete](../cpp/new-and-delete-operators.md) para obtener más información\).  
  
 Puede escribir una rutina que intente liberar memoria y reintente la asignación; vea [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md) para obtener más información.  Para obtener más detalles sobre el esquema de recuperación, vea el tema siguiente, [Controlar condiciones de memoria insuficiente](../misc/handling-insufficient-memory-conditions.md).  
  
 Los dos ámbitos para las funciones `operator new` se describen en la tabla siguiente.  
  
### Ámbito de funciones operator new  
  
|Operador|Ámbito|  
|--------------|------------|  
|**::operator new**|Global|  
|*class\-name* **::operator new**|Clase|  
  
 El primer argumento de **new \(operador\)**debe ser de tipo **size\_t** \(un tipo definido en STDDEF.H\), y el tipo de valor devuelto es siempre **void \***.  
  
 Se llama a la función global **new \(operador\)**cuando el operador **new** se usa para asignar objetos de tipos integrados, objetos de tipo de clase que no contienen funciones **new \(operador\)** definidas por el usuario y matrices de cualquier tipo.  Cuando el operador **new** se usa para asignar objetos de un tipo de clase donde se define **new \(operador\)**, se llama a la función **new \(operador\)** de esa clase.  
  
 Una función **new \(operador\)** definida para una clase es una función miembro estática \(que no puede, por consiguiente, ser virtual\) que oculta la función global **new \(operador\)** para los objetos de ese tipo de clase.  Considere que se usa **new** para asignar y establecer la memoria en un valor determinado:  
  
```  
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
  
 El argumento proporcionado entre paréntesis a **new** se pasa a `Blanks::operator new` como argumento `chInit`.  Sin embargo, se oculta la función global **new \(operador\)**, haciendo que el código como el siguiente genere un error:  
  
```  
Blanks *SomeBlanks = new Blanks;  
```  
  
 En Visual C\+\+ 5.0 y versiones anteriores, los tipos que no eran de clase y todas las matrices \(independientemente de si eran de tipo **class**\) asignados mediante el operador **new** usaban siempre la función global **new \(operador\)**.  
  
 A partir de Visual C\+\+ 5.0, el compilador admite los operadores **new** y **delete** de matriz de miembros en una declaración de clase.  Por ejemplo:  
  
```  
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
  
### Controlar la memoria insuficiente  
 La prueba de error de asignación de memoria se puede realizar con código como el siguiente:  
  
```  
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
  
 Hay otras maneras de controlar los errores de solicitud de asignación de memoria: escriba una rutina de recuperación personalizada para controlar el error, después registre la función mediante una llamada a la función en tiempo de ejecución [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md).  
  
## Operador delete  
 La memoria que se asigna dinámicamente mediante el operador **new** se puede liberar con el operador **delete**.  El operador delete llama a la función **delete \(operador\)**, que libera memoria para que la use el grupo disponible.  El uso del operador **delete** también inicia una llamada al destructor de clase \(si hay alguno\).  
  
 Hay funciones **delete \(operador\)** globales y de ámbito de clase.  Solo se puede definir una función **delete \(operador\)** para una clase dada; si se define, oculta la función **delete \(operador\)** global.  La función **delete \(operador\)** global siempre se llama para las matrices de cualquier tipo.  
  
 La función **delete \(operador\)** global, si se declara, toma un único argumento de tipo **void \***, que contiene un puntero al objeto que se va a desasignar.  El tipo de valor devuelto es `void` \(**delete \(operador\)** no puede devolver un valor\).  Hay dos formas para las funciones **delete \(operador\)** de miembro de clase:  
  
```  
void operator delete( void * );  
void operator delete( void *, size_t );  
```  
  
 Solo una de las dos formas anteriores puede estar presente para una clase dada.  La primera forma funciona según el funcionamiento descrito para `operator delete`global.  La segunda forma toma dos argumentos: el primero es un puntero al bloque de memoria que se va a desasignar y el segundo es el número de bytes que se van a desasignar.  La segunda forma resulta especialmente útil cuando se usa una función **delete \(operador\)** de una clase base para eliminar un objeto de una clase derivada.  
  
 La función **delete \(operador\)** es estática; por consiguiente, no puede ser virtual.  La función `operator delete` obedece al control de acceso, tal como se describe en [Control de acceso a miembros](../cpp/member-access-control-cpp.md).  
  
 En el ejemplo siguiente se muestran las funciones definidas por el usuario **new \(operador\)** y **delete \(operador\)** diseñadas para registrar asignaciones y desasignaciones de memoria:  
  
```  
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
  
 El código anterior se puede utilizar para detectar "pérdidas de memoria", es decir, la memoria que se asigna en el almacén libre pero que nunca se libera.  Para realizar esta detección, se vuelven a definir los operadores **new** y **delete** para determinar la asignación y desasignación de memoria.  
  
 A partir de Visual C\+\+ 5.0, el compilador admite los operadores **new** y **delete** de matriz de miembros en una declaración de clase.  Por ejemplo:  
  
```  
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
  
## Vea también  
 [Funciones miembro especiales](../misc/special-member-functions-cpp.md)