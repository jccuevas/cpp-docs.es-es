---
title: Objeto de duración y administración de recursos (C++ moderno) | Documentos de Microsoft
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
ms.openlocfilehash: 634bef1bf9d2d3128497a1321631ca8665fed144
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423501"
---
# <a name="object-lifetime-and-resource-management-modern-c"></a>Duración de objetos y administración de recursos (C++ moderno)
A diferencia de los lenguajes administrados, C++ no tiene colección de elementos no utilizados (GC), que automáticamente libera los recursos de memoria no más-utilizados mientras se ejecuta un programa. En C++, administración de recursos está directamente relacionado con duración de los objetos. Este documento describe los factores que afectan a la duración de los objetos de C++ y cómo administrarla.  
  
 C++ no tiene GC principalmente debido a que no controlar recursos sin memoria. Solo deterministas destructores similares a las de C++ pueden controlar los recursos de memoria y la memoria no igual. GC también tiene otros problemas, como una mayor sobrecarga en memoria y el consumo de CPU y localidad. Pero universalidad es un problema fundamental que no se puede mitigar mediante optimizaciones inteligentes.  
  
## <a name="concepts"></a>Conceptos  
 Una cuestión importante que en la administración de la duración del objeto es la encapsulación: persona que está usando un objeto no tiene que saber lo que posee los recursos que el objeto, o cómo deshacerse de ellas, o incluso si posee todos los recursos en todo. Solo tiene que se destruirá el objeto. El lenguaje básico de C++ está diseñado para garantizar que los objetos se destruyen en el momento adecuado, es decir, tal y como se sale bloques, en orden inverso de la construcción. Cuando se destruye un objeto, se destruyen sus bases y miembros en un orden concreto.  El idioma automáticamente destruye los objetos, a menos que haga cosas especiales como asignación del montón o la ubicación nueva.  Por ejemplo, [inteligentes punteros](../cpp/smart-pointers-modern-cpp.md) como `unique_ptr` y `shared_ptr`, y contenedores de la biblioteca estándar de C++ como `vector`, encapsular `new` / `delete` y `new[]` / `delete[]` en objetos, que tienen destructores. Por eso es tan importante usar punteros inteligentes y contenedores de la biblioteca estándar de C++.  
  
 Otro concepto importante en la administración de la duración: destructores. Destructores encapsulan liberar el recurso.  (La tecla de acceso frecuente es RRID, recurso de versión es destrucción).  Un recurso es algo que obtiene del "sistema" y tiene que indicar volver más tarde.  Memoria es el recurso más comunes, pero también son archivos, sockets, texturas y otros recursos de memoria no. "Posee" un recurso significa que puede utilizar cuando lo necesite pero también debe liberarla cuando haya terminado con él.  Cuando se destruye un objeto, su destructor libera los recursos pertenece.  
  
 El concepto final es el DAG (gráfico acíclico dirigido).  La estructura de propiedad en un programa de forma un DAG. No hay ningún objeto puede ser propietario de sí mismo, que no sólo es imposible, pero también inherentemente sin sentido. Aunque dos objetos pueden compartir la propiedad de un objeto terceros.  Varios tipos de vínculos son posibles en un DAG parecido a esto: A es miembro de B (B posee un), almacenes de C una `vector<D>` (C es propietario de cada elemento D), almacenes E un `shared_ptr<F>` (E comparte la propiedad de F, posiblemente con otros objetos), y así sucesivamente.  Siempre y cuando no hay ningún ciclos y todos los vínculos de lo DAG se representa mediante un objeto que tiene un destructor (en lugar de un puntero sin formato, identificador u otro mecanismo), a continuación, son imposibles de pérdidas de recursos porque el lenguaje impide que ellos. Los recursos se liberan inmediatamente después de que ya no las necesite, sin un recolector de elementos no utilizados ejecuta. La duración de seguimiento es gratis a la sobrecarga para el ámbito de la pila, bases de datos, miembros y casos relacionados y económica para `shared_ptr`.  
  
### <a name="heap-based-lifetime"></a>Duración basada en el montón  
 Duración del objeto de montón, use [inteligentes punteros](../cpp/smart-pointers-modern-cpp.md). Use `shared_ptr` y `make_shared` como el puntero predeterminado y el asignador. Use `weak_ptr` en interrumpir ciclos, realizar el almacenamiento en caché y observar los objetos sin que ello afecte a o suponiendo nada sobre sus duraciones.  
  
```cpp  
void func() {  
  
auto p = make_shared<widget>(); // no leak, and exception safe  
...  
p->draw();   
  
} // no delete required, out-of-scope triggers smart pointer destructor  
  
```  
  
 Use `unique_ptr` para una propiedad única, por ejemplo, en la *pimpl* expresión. (Consulte [Pimpl para encapsulación en tiempo de compilación](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md).) Realizar una `unique_ptr` el destino principal de todos los explícita `new` expresiones.  
  
```cpp  
unique_ptr<widget> p(new widget());  
```  
  
 Puede utilizar punteros sin formato para la propiedad no y observación. Un puntero no es propietario posible oscile, pero no se puede perder.  
  
```cpp  
class node {  
  ...  
  vector<unique_ptr<node>> children; // node owns children  
  node* parent; // node observes parent, which is not a concern  
  ...  
};  
node::node() : parent(...) { children.emplace_back(new node(...) ); }  
  
```  
  
 Cuando se requiere la optimización del rendimiento, es posible que deba usar *bien encapsulado* propietaria de punteros y las llamadas explícitas a eliminar. Un ejemplo es cuando implementa su propia estructura de datos de bajo nivel.  
  
### <a name="stack-based-lifetime"></a>Duración basada en pilas  
 En C++ moderno, *ámbito basada en pilas* es una manera eficaz para escribir código sólido porque combina automática *duración de la pila* y *duración del miembro de datos* con alta eficacia: duración de seguimiento es esencialmente gratuita de sobrecarga. Duración de objetos de montón requiere administración manual diligente y puede ser el origen de pérdidas de recursos e ineficiencias, especialmente cuando se trabaja con punteros sin formato. Tenga en cuenta este código, que muestra el ámbito basados en la pila:  
  
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
  
 Utilice con moderación duración estática (estático global, estática local de función) ya que pueden surgir problemas. ¿Qué ocurre cuando el constructor de un objeto global produce una excepción? Normalmente, los errores de aplicación de forma que puede ser difícil de depurar. Orden de construcción resulta problemática para los objetos de una duración estática y no es seguro para simultaneidad. No solo es la construcción de objetos de un problema, el orden de destrucción puede ser complejo, especialmente cuando el polimorfismo está implicado. Incluso si el objeto o una variable no es polimórfico y no tiene compleja Construcción/destrucción de ordenación, sigue siendo el problema de simultaneidad de subprocesos. Una aplicación multiproceso con seguridad no puede modificar los datos de objetos estáticos sin necesidad de almacenamiento local de subprocesos y bloqueos de recursos, otros precauciones especiales.  
  
## <a name="see-also"></a>Vea también  
 [Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)