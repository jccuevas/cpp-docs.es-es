---
title: Destructores (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], destroying
- Visual C++, destructors
- destroying objects, destructors
- ~ operator [C++], specifying destructors
- destructors, about destructors
- destructors, C++
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64d75946d3ae9c1de1d59d74100de68a3b27dcc8
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704807"
---
# <a name="destructors-c"></a>Destructores (C++)

Un destructor es una función miembro que se invoca automáticamente cuando el objeto queda fuera del ámbito o se destruyeron de forma explícita mediante una llamada a `delete`. Un destructor tiene el mismo nombre que la clase, precedido por una tilde (`~`). Por ejemplo, el destructor de la clase `String` se declara como: `~String()`.

Si no se define un destructor, el compilador proporcionará un valor predeterminado; para muchas clases de esto es suficiente. Solo necesita definir un destructor personalizado cuando la clase almacena los identificadores de recursos de sistema que necesitan que se liberen o punteros que poseen la memoria que señalan a.

Considere la siguiente declaración de una clase `String`:

```cpp
// spec1_destructors.cpp
#include <string.h>

class String {
public:
   String( char *ch );  // Declare constructor
   ~String();           //  and destructor.
private:
   char    *_text;
   size_t  sizeOfText;
};

// Define the constructor.
String::String( char *ch ) {
   sizeOfText = strlen( ch ) + 1;

   // Dynamically allocate the correct amount of memory.
   _text = new char[ sizeOfText ];

   // If the allocation succeeds, copy the initialization string.
   if( _text )
      strcpy_s( _text, sizeOfText, ch );
}

// Define the destructor.
String::~String() {
   // Deallocate the memory that was previously reserved
   //  for this string.
   if (_text)
      delete[] _text;
}

int main() {
   String str("The piper in the glen...");
}
```

En el ejemplo anterior, el destructor `String::~String` utiliza el operador `delete` para desasignar el espacio asignado dinámicamente para el almacenamiento de texto.

## <a name="declaring-destructors"></a>Declarar destructores

Los destructores son funciones con el mismo nombre que la clase pero precedidos por una tilde (`~`).

Varias reglas rigen la declaración de destructores. Destructores:

- No aceptan argumentos.

- No devuelven un valor (o `void`).

- No se pueden declarar como **const**, **volátiles**, o **estático**. Sin embargo, se puede invocar para la destrucción de objetos declarados como **const**, **volátiles**, o **estático**.

- Se pueden declarar como **virtuales**. Mediante los destructores virtuales, puede destruir objetos sin conocer su tipo; se invoca el destructor correcto para el objeto mediante el mecanismo de función virtual. Observe que los destructores también se pueden declarar como funciones virtuales puras para las clases abstractas.

## <a name="using-destructors"></a>Usar destructores

Se llama a los destructores cuando se produce alguno de los eventos siguientes:

- Un objeto local (automático) con ámbito de bloque sale de ámbito.

- Un objeto asignado con el **nueva** operador se desasigna explícitamente con **eliminar**.

- La duración de un objeto temporal termina.

- Un programa termina y hay objetos globales o estáticos.

- Se llama explícitamente al destructor mediante el nombre completo de la función de destructor.

Los destructores pueden llamar libremente a funciones miembro de clase y acceder a datos de miembros de clase.

Hay dos restricciones en el uso de destructores:

- No se puede tomar su dirección.

- las clases derivadas no heredan el destructor de su clase base.

## <a name="order-of-destruction"></a>Orden de destrucción

Cuando un objeto sale del ámbito o se elimina, la secuencia de eventos para su completa destrucción es la siguiente:

1. Se llama al destructor de clase y se ejecuta el cuerpo de la función destructora.

1. Los destructores de los objetos miembro no estáticos se llaman en el orden inverso al que aparecen en la declaración de clase. La lista de inicialización miembro opcional utilizada en la construcción de estos miembros no afecta al orden de construcción o destrucción.

1. Destructores de clases base no virtuales se llaman en el orden inverso de la declaración.

1. Los destructores para las clases base virtuales se llaman en el orden inverso al de la declaración.

```cpp
// order_of_destruction.cpp
#include <stdio.h>

struct A1      { virtual ~A1() { printf("A1 dtor\n"); } };
struct A2 : A1 { virtual ~A2() { printf("A2 dtor\n"); } };
struct A3 : A2 { virtual ~A3() { printf("A3 dtor\n"); } };

struct B1      { ~B1() { printf("B1 dtor\n"); } };
struct B2 : B1 { ~B2() { printf("B2 dtor\n"); } };
struct B3 : B2 { ~B3() { printf("B3 dtor\n"); } };

int main() {
   A1 * a = new A3;
   delete a;
   printf("\n");

   B1 * b = new B3;
   delete b;
   printf("\n");

   B3 * b2 = new B3;
   delete b2;
}

Output: A3 dtor
A2 dtor
A1 dtor

B1 dtor

B3 dtor
B2 dtor
B1 dtor

```

### <a name="virtual-base-classes"></a>Clases base virtuales

Los destructores de las clases base virtuales se llaman en orden inverso al de su aparición en un gráfico acíclico dirigido (recorrido con prioridad de profundidad, de izquierda a derecha y en postorden). La ilustración siguiente representa un gráfico de herencia.

![Gráfico de herencia que muestra clases base virtuales](../cpp/media/vc392j1.gif "vc392J1")

Gráfico de herencia que muestra clases base virtuales

A continuación se enumeran los encabezados de las clases que se muestran en la ilustración.

```cpp
class A
class B
class C : virtual public A, virtual public B
class D : virtual public A, virtual public B
class E : public C, public D, virtual public B
```

Para determinar el orden de destrucción de las clases base virtuales de un objeto de tipo `E`, el compilador compila una lista aplicando el algoritmo siguiente:

1. Recorrer el gráfico izquierdo, desde el punto más profundo del gráfico (en este caso, `E`).

1. Realizar recorridos hacia la izquierda hasta que se hayan visitado todos los nodos. Anotar el nombre del nodo actual.

1. Revisitar el nodo anterior (abajo y a la derecha) para averiguar si el nodo recordado es una clase base virtual.

1. Si el nodo recordado es una clase base virtual, examinar la lista para ver si ya se ha especificado. Si no es una clase base virtual, omitirla.

1. Si el nodo recordado no está aún en la lista, agregarla al final de la lista.

1. Recorrer el gráfico hacia arriba y a lo largo de la ruta siguiente a la derecha.

1. Vaya al paso 2.

1. Cuando se agote la última ruta ascendente, anotar el nombre del nodo actual.

1. Vaya al paso 3.

1. Continuar este proceso hasta que el nodo inferior sea de nuevo el nodo actual.

Por consiguiente, para la clase `E`, el orden de destrucción es:

1. La clase base no virtual `E`.

1. La clase base no virtual `D`.

1. La clase base no virtual `C`.

1. La clase base virtual `B`.

1. La clase base virtual `A`.

Este proceso produce una lista ordenada de entradas únicas. Ningún nombre de clase aparece dos veces. Una vez construida la lista, se recorre en orden inverso y se llama al destructor para cada una de las clases de la lista, desde la última hasta la primera.

El orden de construcción o de destrucción es importante sobre todo cuando los constructores o destructores de una clase se basan en que el otro componente se cree primero o persista más tiempo; por ejemplo, si el destructor para `A` (en la ilustración anterior) se basa en que `B` continúa estando presente cuando se ejecute el código o viceversa.

Tales interdependencias entre clases en un gráfico de herencia son inherentemente peligrosas, porque las últimas clases derivadas pueden cambiar cuál es la ruta más a la izquierda y, en consecuencia, pueden cambiar el orden de construcción y destrucción.

### <a name="non-virtual-base-classes"></a>Clases base no virtuales

Se llaman a los destructores de clases base no virtuales en el orden inverso en el que se declaran los nombres de clase base. Considere la siguiente declaración de clase:

```cpp
class MultInherit : public Base1, public Base2
...
```

En el ejemplo anterior, el destructor para `Base2` se invoca antes que el destructor para `Base1`.

## <a name="explicit-destructor-calls"></a>Llamadas de destructor explícitas

Raras veces se necesita llamar explícitamente al destructor. Sin embargo, puede ser útil realizar la limpieza de los objetos colocados en direcciones absolutas. Estos objetos se asignan normalmente utilizando definido por el usuario **nueva** operador que toma un argumento de ubicación. El **eliminar** operador no puede desasignar esta memoria porque no está asignada desde el almacén gratuito (para obtener más información, consulte [el nuevo y eliminar operadores](../cpp/new-and-delete-operators.md)). Sin embargo, una llamada al destructor puede realizar la limpieza adecuada. Para llamar explícitamente al destructor para un objeto, `s`, de clase `String`, utilice una de las instrucciones siguientes:

```cpp
s.String::~String();     // non-virtual call
ps->String::~String();   // non-virtual call

s.~String();       // Virtual call
ps->~String();     // Virtual call
```

La notación para las llamadas explícitas a destructores, que se muestra anteriormente, puede utilizarse con independencia de que el tipo defina un destructor. Esto permite realizar llamadas explícitas sin saber si un destructor está definido para el tipo. Una llamada explícita a un destructor donde no se ha definido ninguna no tiene ningún efecto.
