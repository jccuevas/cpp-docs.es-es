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
ms.openlocfilehash: a8c6733a9f6e5c9650333f96a92ff18eedb9c356
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516500"
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)

Declara un *puntero anclado*, que se usa solo con Common Language Runtime.

## <a name="all-runtimes"></a>Todos los runtimes

(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

(Esta característica del lenguaje no se admite en Windows Runtime).

## <a name="common-language-runtime"></a>Common Language Runtime

Un *puntero anclado* es un puntero interior que impide que el objeto al que se señala se mueva en el montón de recolección de elementos no utilizados. Es decir, Common Language Runtime no cambia el valor de un puntero anclado. Esto es necesario cuando se pasa la dirección de una clase administrada a una función no administrada, ya que la dirección no cambiará de forma inesperada durante la resolución de la llamada de función no administrada.

### <a name="syntax"></a>Sintaxis

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>Parámetros

*cv_qualifier*<br/>
Calificadores **const** o **volatile**. De forma predeterminada, un puntero anclado es **volatile**. Aunque no es un error declarar un puntero anclado **volatile**, sí es redundante.

*type*<br/>
El tipo de *initializer*.

*var*<br/>
El nombre de la variable **pin_ptr**.

*initializer*<br/>
Un miembro de un tipo de referencia, elemento de una matriz administrada o cualquier otro objeto que se pueda asignar a un puntero nativo.

### <a name="remarks"></a>Comentarios

Una variable **pin_ptr** constituye un supraconjunto de la funcionalidad de un puntero nativo. Por lo tanto, todo lo que se puede asignar a un puntero nativo también se puede asignar a una variable **pin_ptr**. Se permite que un puntero interior realice el mismo conjunto de operaciones que los punteros nativos, incluida la comparación y la aritmética de punteros.

Se puede anclar un objeto o un subobjeto de una clase administrada, en cuyo caso Common Language Runtime no lo moverá durante la recolección de elementos no utilizados. El principal uso de esta operación es pasar un puntero a datos administrados como un parámetro real de una llamada a función no administrada. Durante un ciclo de recopilación, se inspeccionarán en tiempo de ejecución los metadatos creados para el puntero anclado y no se moverá el elemento al que apunta.

Anclar un objeto también ancla sus campos de valor; es decir, los campos de primitivo o tipo de valor. Sin embargo, los campos declarados por el manipulador de seguimiento (`%`) no están anclados.

Anclar un subobjeto definido en un objeto administrado tiene el efecto de anclar el objeto entero.

Si el puntero anclado se reasigna para que apunte a un nuevo valor, la instancia anterior a la que señala ya no se considera anclada.

Un objeto está anclado solo mientras una variable **pin_ptr** lo señala. El objeto ya no está anclado cuando su puntero anclado queda fuera del ámbito o se establece en [nullptr](nullptr-cpp-component-extensions.md). Después de que la variable **pin_ptr** queda fuera del ámbito, el objeto que se ancló se puede mover en el ámbito mediante el recolector de elementos no utilizados. Los punteros nativos que siguen apuntando al objeto no se actualizarán y, si se anula la referencia a uno de ellos, se podría producir una excepción irrecuperable.

Si ningún puntero anclado apunta al objeto (todos los punteros anclados quedan fuera del ámbito, se reasignaron para que apunten a otros objetos o se les asignó [nullptr](nullptr-cpp-component-extensions.md)), es seguro que el objeto no se anclará.

Un puntero interior puede apuntar a un manipulador de referencia, un tipo de valor, un manipulador de tipo al que se aplica la conversión boxing, el miembro de un tipo administrado o a un elemento de una matriz administrada. No puede apuntar a un tipo de referencia.

Al tomar la dirección de una variable **pin_ptr** que apunta a un objeto nativo se produce un comportamiento indefinido.

Los punteros anclados solo pueden declararse como variables locales no estáticas en la pila.

Los punteros anclados no se pueden usar como:

- parámetros de la función

- el tipo devuelto de una función

- un miembro de una clase

- el tipo de destino de una conversión.

**pin_ptr** está en el espacio de nombres `cli`. Para más información, consulte [Espacios de nombres de plataforma, predeterminado y CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md).

Para más información sobre los punteros interiores, consulte [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md).

Para más información sobre los punteros anclados, consulte [Procedimiento: Anclar puntero y matrices](how-to-pin-pointers-and-arrays.md) y [Procedimiento: Declarar punteros anclados y tipos de valor](how-to-declare-pinning-pointers-and-value-types.md).

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

En el ejemplo siguiente se muestra que un puntero interior se puede convertir en un puntero anclado, y que el tipo de valor devuelto de la dirección del operador (`&`) es un puntero interior cuando el operando está en el montón administrado.

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

En el ejemplo siguiente se muestra que un puntero anclado se puede convertir en otro tipo.

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