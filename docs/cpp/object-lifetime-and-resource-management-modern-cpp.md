---
title: Duración de objetos y administración de recursos (RAII)
description: Siga el principio de RAII en moderno C++ para evitar pérdidas de recursos.
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
ms.openlocfilehash: 01867ec0a71ba54bb6534da1b408cb0610d652a7
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303373"
---
# <a name="object-lifetime-and-resource-management-raii"></a>Duración de objetos y administración de recursos (RAII)

A diferencia de los lenguajes administrados, no tiene recolección automática de C++ *elementos no utilizados*. Este es un proceso interno que libera la memoria del montón y otros recursos a medida que se ejecuta un programa. Un C++ programa es responsable de devolver todos los recursos adquiridos al sistema operativo. Un error al liberar un recurso sin usar se denomina *fuga*. Los recursos filtrados no están disponibles para otros programas hasta que el proceso se cierra. En concreto, las pérdidas de memoria son una causa común de errores en la programación de estilo C.

Moderno C++ evita usar la memoria del montón lo máximo posible declarando objetos en la pila. Cuando un recurso es demasiado grande para la pila, debe ser *propiedad* de un objeto. A medida que se inicializa el objeto, adquiere el recurso que posee. Después, el objeto es responsable de liberar el recurso en su destructor. El propio objeto propietario se declara en la pila. El principio de que *los objetos propios recursos* también se conoce como "adquisición de recursos," o RAII.

Cuando un objeto de pila propietario del recurso sale del ámbito, se invoca automáticamente su destructor. De esta manera, la recolección de C++ elementos no utilizados en está estrechamente relacionada con la duración de los objetos y es determinista. Un recurso siempre se libera en un punto conocido del programa, que se puede controlar. Solo los destructores deterministas, como C++ los de, pueden controlar de forma equitativa los recursos de memoria y no de memoria.

En el ejemplo siguiente se muestra un objeto simple `w`. Se declara en la pila en el ámbito de la función y se destruye al final del bloque de función. El objeto `w` no posee ningún *recurso* (por ejemplo, memoria asignada por montón). Su único `g` miembro se declara en la pila y simplemente sale del ámbito junto con `w`. No se necesita ningún código especial en el destructor `widget`.

```cpp
class widget {
private:
    gadget g;   // lifetime automatically tied to enclosing object
public:
    void draw();
};

void functionUsingWidget () {
    widget w;   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.g gadget member
    // ...
    w.draw();
    // ...
} // automatic destruction and deallocation for w and w.g
  // automatic exception safety,
  // as if "finally { w.dispose(); w.g.dispose(); }"
```

En el ejemplo siguiente, `w` posee un recurso de memoria y, por tanto, debe tener código en su destructor para eliminar la memoria.
 
```cpp
class widget
{
private:
    int* data;
public:
    widget(const int size) { data = new int[size]; } // acquire
    ~widget() { delete[] data; } // release
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                        // constructs w, including the w.data member
    w.do_something();

} // automatic destruction and deallocation for w and w.data

```

Desde C++ 11, hay una manera mejor de escribir el ejemplo anterior: mediante el uso de un puntero inteligente de la biblioteca estándar. El puntero inteligente controla la asignación y eliminación de la memoria que posee. El uso de un puntero inteligente elimina la necesidad de un destructor explícito en la clase `widget`.

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

Mediante el uso de punteros inteligentes para la asignación de memoria, puede eliminar la posible pérdida de memoria. Este modelo funciona para otros recursos, como identificadores de archivo o Sockets. Puede administrar sus propios recursos de una manera similar en sus clases. Para obtener más información, vea [punteros inteligentes](smart-pointers-modern-cpp.md).

El diseño de C++ garantiza que los objetos se destruyen cuando salen del ámbito. Es decir, se destruyen cuando se cierran los bloques, en orden inverso a la construcción. Cuando se destruye un objeto, sus bases y miembros se destruyen en un orden determinado. Los objetos declarados fuera de cualquier bloque, en el ámbito global, pueden provocar problemas. Puede ser difícil de depurar si el constructor de un objeto global produce una excepción.

## <a name="see-also"></a>Vea también

[Bienvenido de nuevo aC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
