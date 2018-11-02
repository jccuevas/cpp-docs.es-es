---
title: pin_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
ms.openlocfilehash: 1e1d7959825284cc9c239147d33e54cc56352fa2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587283"
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)

Declara un *puntero anclado*, que se usa solo con common language runtime.

## <a name="all-runtimes"></a>Todos los runtimes

(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

(Esta característica del lenguaje no se admite en el tiempo de ejecución de Windows).

## <a name="common-language-runtime"></a>Common Language Runtime

Un *puntero anclado* es un puntero interior que impide que el objeto que señala de la migración en el montón de recolección. Es decir, no se cambia el valor de un puntero anclado por common language runtime. Esto es necesario cuando se pasa la dirección de una clase administrada a una función no administrada para que la dirección no cambia inesperadamente durante la resolución de la llamada de función no administrada.

### <a name="syntax"></a>Sintaxis

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>Parámetros

*cv_qualifier*<br/>
**Const** o **volátil** calificadores. De forma predeterminada, es un puntero anclado **volátil**. Es redundante, pero no un error declarar un puntero anclado **volátil**.

*type*<br/>
El tipo de *inicializador*.

*var*<br/>
El nombre de la **pin_ptr** variable.

*initializer*<br/>
Un miembro de un tipo de referencia, el elemento de una matriz administrada o cualquier otro objeto que se puede asignar a un puntero nativo.

### <a name="remarks"></a>Comentarios

Un **pin_ptr** constituye un supraconjunto de la funcionalidad de un puntero nativo. Por lo tanto, todo lo que se pueden asignar a un puntero nativo también se puede asignar a un **pin_ptr**. Se permite un puntero interior para realizar el mismo conjunto de operaciones como punteros nativos, incluida la comparación y la aritmética de puntero.

Puede anclar un objeto o subobjeto de una clase administrada, en cuyo caso el common language runtime no la moverá durante la recolección de elementos no utilizados. El uso principal de esto consiste en pasar un puntero a datos administrados como un parámetro real de una llamada de función no administrada. Durante un ciclo de recopilación, el tiempo de ejecución inspeccionará los metadatos creados para el puntero anclado y no moverá el elemento al a que apunta.

Anclar un objeto ancla también sus campos de valor; es decir, los campos de tipo primitivo o valor de tipo. Sin embargo, los campos declaran por identificador de seguimiento (`%`) no están anclados.

Anclar un subobjeto definido en un objeto administrado tiene el efecto de anclar todo el objeto.

Si el puntero anclado se reasigna para que apunte a un nuevo valor, la instancia anterior que señala ya no se considera anclado.

Un objeto está anclado solo mientras un **pin_ptr** hace referencia a ella. El objeto ya no está fijado cuando el puntero anclado sale del ámbito o se establece en [nullptr](../windows/nullptr-cpp-component-extensions.md). Después de la **pin_ptr** se puede mover en el montón se sale del ámbito, el objeto que se ancló el recolector de elementos no utilizados. Los punteros nativos que apuntan al objeto aún no se actualizará y anulando las referencias a uno de ellos podrían producir una excepción irrecuperable.

Si no hay punteros anclados apuntan al objeto (todos los punteros anclados está fuera del ámbito, se reasignaron para que apunte a otros objetos o se asignaron [nullptr](../windows/nullptr-cpp-component-extensions.md)), el objeto se garantiza que no quede anclada.

Un puntero anclado puede señalar a un identificador de referencia tipo de valor o el identificador del tipo de conversión boxing, miembro de un tipo administrado o un elemento de una matriz administrada. No puede apuntar a un tipo de referencia.

Tomar la dirección de un **pin_ptr** que apunta a un objeto nativo produce un comportamiento indefinido.

Punteros anclados solo pueden declararse como variables locales no estáticas en la pila.

No se puede usar punteros anclados como:

- parámetros de la función

- el tipo de valor devuelto de una función

- un miembro de una clase

- el tipo de destino de una conversión.

**pin_ptr** está en el `cli` espacio de nombres. Para obtener más información, consulte [de plataforma, predeterminado y cli de espacios de nombres](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).

Para obtener más información sobre los punteros interiores, consulte [interior_ptr (C++ / c++ / CLI)](../windows/interior-ptr-cpp-cli.md).

Para obtener más información sobre punteros anclados, vea [Cómo: anclar punteros y matrices](../windows/how-to-pin-pointers-and-arrays.md) y [Cómo: declarar punteros de anclaje y tipos de valor](../windows/how-to-declare-pinning-pointers-and-value-types.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo siguiente se usa **pin_ptr** para restringir la posición del primer elemento de una matriz.

```cpp
// pin_ptr_1.cpp
// compile with: /clr
using namespace System;
#define SIZE 10

#pragma unmanaged
// native function that initializes an array
void native_function(int* p) {
   for(int i = 0 ; i < 10 ; i++)
    p[i] = i;
}
#pragma managed

public ref class A {
private:
   array<int>^ arr;   // CLR integer array

public:
   A() {
      arr = gcnew array<int>(SIZE);
   }

   void load() {
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr
   int* np = p;   // pointer to the first element in arr
   native_function(np);   // pass pointer to native function
   }

   int sum() {
      int total = 0;
      for (int i = 0 ; i < SIZE ; i++)
         total += arr[i];
      return total;
   }
};

int main() {
   A^ a = gcnew A;
   a->load();   // initialize managed array using the native function
   Console::WriteLine(a->sum());
}
```

```Output
45
```

El ejemplo siguiente se muestra que se puede convertir un puntero interior a un puntero anclado y tipo de valor devuelto del operador de dirección (`&`) es un puntero interior cuando el operando es en el montón administrado.

```cpp
// pin_ptr_2.cpp
// compile with: /clr
using namespace System;

ref struct G {
   G() : i(1) {}
   int i;
};

ref struct H {
   H() : j(2) {}
   int j;
};

int main() {
   G ^ g = gcnew G;   // g is a whole reference object pointer
   H ^ h = gcnew H;

   interior_ptr<int> l = &(g->i);   // l is interior pointer

   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer

   k = l;   // ok
   Console::WriteLine(*k);
};
```

```Output
1
```

El ejemplo siguiente se muestra que se puede convertir un puntero anclado a otro tipo.

```cpp
// pin_ptr_3.cpp
// compile with: /clr
using namespace System;

ref class ManagedType {
public:
   int i;
};

int main() {
   ManagedType ^mt = gcnew ManagedType;
   pin_ptr<int> pt = &mt->i;
   *pt = 8;
   Console::WriteLine(mt->i);

   char *pc = ( char* ) pt;
   *pc = 255;
   Console::WriteLine(mt->i);
}
```

```Output
8
255
```