---
title: Objeto de duración y administración de recursos (C++ moderno) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fae540542abcd1e5281d355788860bea74e0b61
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105458"
---
# <a name="object-lifetime-and-resource-management-modern-c"></a>Duración de objetos y administración de recursos (C++ moderno)

A diferencia de los lenguajes administrados, C++ no tiene la colección de elementos no utilizados (GC), lo que automáticamente libera los recursos de memoria no más-usados mientras se ejecuta un programa. En C++, administración de recursos está directamente relacionado con duración de objetos. Este documento describe los factores que afectan a la duración del objeto en C++ y cómo administrarlos.

C++ no tiene GC principalmente porque no controla los recursos sin memoria. Solo destructores deterministas como las de C++ pueden controlar los recursos de memoria y memoria que no son igualmente. GC también tiene otros problemas, como una mayor sobrecarga en memoria y consumo de CPU y localidad. Pero universalidad es un problema fundamental que no se pueden mitigar a través de las optimizaciones de clever.

## <a name="concepts"></a>Conceptos

Un aspecto importante de la administración de la duración del objeto es la encapsulación, el usuario que usa un objeto no tiene que saber lo que posee los recursos de ese objeto, o cómo deshacerse de ellas o incluso si lo posee ningún recurso en absoluto. Solo debe destruir el objeto. El lenguaje de C++ core está diseñado para garantizar que los objetos se destruyen en el momento adecuado, es decir, como bloques se ha cerrado, en orden inverso de la construcción. Cuando se destruye un objeto, se destruyen sus bases y miembros en un orden concreto.  El lenguaje destruye automáticamente objetos, a menos que haga cosas especiales, como la asignación del montón o la ubicación nueva.  Por ejemplo, [inteligente punteros](../cpp/smart-pointers-modern-cpp.md) como `unique_ptr` y `shared_ptr`, y como contenedores de la biblioteca estándar de C++ `vector`, encapsular **nueva** /  **eliminar** y `new[]` / `delete[]` en objetos, que tienen destructores. Por eso es tan importante usar punteros inteligentes y contenedores de la biblioteca estándar de C++.

Otro concepto importante en la administración de la duración: destructores. Los destructores encapsulan liberar el recurso.  (La tecla de acceso frecuente es RRID, Resource Release Is Destruction).  Un recurso es algo que obtener del "sistema" y tiene que devolver más adelante.  Memoria es el recurso más comunes, pero también son archivos, sockets, texturas y otros recursos de memoria no. "Posee" un recurso, significa que puede usar cuando lo necesite, pero también debe liberarla cuando haya terminado con él.  Cuando se destruye un objeto, su destructor libera los recursos que un propietario.

El concepto final es el DAG (gráfico acíclico dirigido).  La estructura de la propiedad en un programa constituye un DAG. No hay ningún objeto puede ser propietario de sí mismo, que no sólo es imposible, pero también carece de sentido intrínsecamente. Pero pueden compartir la propiedad de un tercer objeto de dos objetos.  Varios tipos de vínculos son posibles en un DAG similar al siguiente: A es miembro de B (B posee un), almacena C un `vector<D>` (C posee cada elemento D), almacenes E un `shared_ptr<F>` (E comparte la propiedad de F, posiblemente con otros objetos), y así sucesivamente.  Siempre que no hay ningún ciclo y todos los vínculos en el DAG se representan mediante un objeto que tiene un destructor (en lugar de un puntero sin formato, identificador u otro mecanismo), a continuación, pérdidas de recursos son imposibles porque evita que el lenguaje. Los recursos se liberan inmediatamente después de que deje de necesitarlos, sin un recolector de elementos que se ejecuta. La duración de seguimiento es libre de sobrecarga de ámbito de la pila, las bases, miembros y los casos relacionados y económico `shared_ptr`.

### <a name="heap-based-lifetime"></a>Duración basada en el montón

Duración de objetos del montón, use [inteligente punteros](../cpp/smart-pointers-modern-cpp.md). Use `shared_ptr` y `make_shared` como el puntero predeterminado y el asignador. Use `weak_ptr` interrumpir ciclos, realizar almacenamiento en caché y observar los objetos sin que afecte a o suponiendo que nada acerca de sus duraciones.

```cpp
void func() {

auto p = make_shared<widget>(); // no leak, and exception safe
...
p->draw();

} // no delete required, out-of-scope triggers smart pointer destructor
```

Use `unique_ptr` para una propiedad única, por ejemplo, en el *pimpl* modismo. (Consulte [Pimpl para encapsulación en tiempo de compilación](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md).) Realizar una `unique_ptr` el objetivo principal de todos explícitos **nuevo** expresiones.

```cpp
unique_ptr<widget> p(new widget());
```

Puede utilizar punteros sin formato para la ausencia de propiedad y observación. Es posible que quede colgando un puntero que no sea propietaria, pero no se puede perder.

```cpp
class node {
  ...
  vector<unique_ptr<node>> children; // node owns children
  node* parent; // node observes parent, which is not a concern
  ...
};
node::node() : parent(...) { children.emplace_back(new node(...) ); }
```

Cuando se requiere la optimización del rendimiento, es posible que deba usar *bien encapsulado* propietario punteros y las llamadas explícitas a eliminar. Un ejemplo es cuando implementa su propia estructura de datos de bajo nivel.

### <a name="stack-based-lifetime"></a>Duración basada en la pila

En C++ moderno, *ámbito basado en pila* es una manera eficaz para escribir código sólido, ya que combina automática *duración de la pila* y *duración del miembro de datos* con alta eficacia: duración de seguimiento es esencialmente gratuita de sobrecarga. Duración de objetos de montón requiere la administración manual diligente y puede ser el origen de pérdidas de recursos y la ineficacia, especialmente cuando se trabaja con punteros sin formato. Tenga en cuenta este código, que muestra el ámbito basada en la pila:

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

Se debe utilizar una duración estática (estáticas globales, estáticos locales de función) ya que pueden surgir problemas. ¿Qué ocurre cuando el constructor de un objeto global genera una excepción? Normalmente, los errores de aplicación de forma que puede ser difícil de depurar. Orden de construcción es problemático para los objetos de una duración estática y no es seguro para simultaneidad. No sólo es la construcción de objetos de un problema, el orden de destrucción puede ser complejo, especialmente si el polimorfismo está implicado. Incluso si el objeto o una variable no es polimórfico y no tiene el orden de construcción o destrucción compleja, sigue siendo el problema de simultaneidad de subprocesos. Una aplicación multiproceso no puede modificar con seguridad los datos de objetos estáticos sin necesidad de almacenamiento local de subprocesos, bloqueos de recursos y otras precauciones especiales.

## <a name="see-also"></a>Vea también

[Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)