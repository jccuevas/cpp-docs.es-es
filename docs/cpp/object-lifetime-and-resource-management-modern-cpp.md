---
title: "Duraci&#243;n de objetos y administraci&#243;n de recursos (C++ moderno) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Duraci&#243;n de objetos y administraci&#243;n de recursos (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A diferencia de lenguajes administrados, C\+\+ no tiene recolección de elementos no utilizados \(GC\), que automáticamente libera ninguno\-largo\- utilizaban los recursos de memoria como se ejecuta un programa.  En C\+\+, la administración de recursos se relaciona directamente con la duración del objeto.  Este documento describe los factores que afectan a la duración del objeto en C\+\+ y cómo controlarlos.  
  
 C\+\+ no tiene GC principalmente porque no controla recursos de no de memoria.  Sólo los destructores deterministas como los de C\+\+ pueden controlar recursos de memoria y de que la memoria igualmente.  GC también tiene otros problemas, como una sobrecarga mayor en memoria y el consumo de CPU, y lugar.  Pero la universalidad es un problema fundamental que no se puede reducir con optimizaciones listas.  
  
## Conceptos  
 Es importante en administración de la duración objeto es la encapsulación\- quienquiera mediante un objeto no tiene que saber qué recursos que el objeto posee, o cómo corregir de ellas, o incluso si posee los recursos en absoluto.  Solo tiene que destruir el objeto.  El lenguaje básico de C\+\+ está diseñado para asegurarse que los objetos se destruyeron en los tiempos correctos, es decir, como bloques se dejan, en orden inverso de la construcción.  Cuando se destruye un objeto, destruyen las bases y miembros en un orden determinado.  El lenguaje automáticamente destruye objetos, a menos que se haga cosas especiales como asignación o la posición de la pila nueva.  Por ejemplo, [punteros inteligentes](../cpp/smart-pointers-modern-cpp.md) como de `unique_ptr` y de `shared_ptr`, y los contenedores estándar de \(STL\) de la plantilla como `vector`, encapsula `new`\/`delete` y `new[]`\/`delete[]` en los objetos, que tienen destructores.  Por eso es tan importante utilizar punteros inteligentes y los contenedores STL.  
  
 Otro concepto importante en administración de la duración: destructores.  Los destructores encapsulan la liberación de recursos.  \(La mnemónico de uso general de No se RRID, recurso a la versión es Destruction.\)  Un recurso es algo que obtiene “system” y tiene que dar la reproducción más adelante.  La memoria es el recurso más común, pero también hay archivos, sockets, texturas, y otros recursos de no de memoria. La “propiedad” de un recurso significa que puede usarla cuando la necesita pero también tiene que iniciar el mercadola cuando haya terminado.  Cuando se destruye un objeto, las versiones del destructor los recursos que poseyó.  
  
 El concepto final es el DAG \(Directed Acyclic Gráfico\).  La estructura de la propiedad en un programa forma un DAG.  Ningún objeto puede poseer sí mismo\- no sólo imposible pero también inherentemente sentido.  Pero dos objetos pueden compartir la propiedad de un tercer objeto.  Varias clases de vínculos son posibles en un DAG como ésta: A es miembro b \(b posee A\), C almacena `vector<D>` \(C posee cada elemento de d\), E almacena `shared_ptr<F>` \(E comparte la propiedad f, posiblemente con otros objetos\), y así sucesivamente.  Mientras no haya ciclos y cada vínculo en el DAG está representado por un objeto que tiene un destructor \(en lugar de puntero sin formato, ID, u otro mecanismo\), las pérdidas de recursos son imposibles porque el lenguaje los evita.  Libera los recursos inmediatamente después de ya no necesitan, sin una ejecución del recolector de elementos no utilizados.  El seguimiento de la duración es sobrecarga\- libre para el ámbito de la pila, bases, miembros, y casos relacionados, y barato para `shared_ptr`.  
  
### Duración Pila\-basada  
 Para la duración de objeto del montón, utilice [punteros inteligentes](../cpp/smart-pointers-modern-cpp.md).  Utilice `shared_ptr` y `make_shared` como el puntero y el asignador predeterminados.  Utilice `weak_ptr` para interrumpir ciclos, haga el almacenamiento en caché, y observe los objetos sin afectar o suponiendo que nada sobre sus duraciones.  
  
```cpp  
void func() {  
  
auto p = make_shared<widget>(); // no leak, and exception safe  
...  
p->draw();   
  
} // no delete required, out-of-scope triggers smart pointer destructor  
  
```  
  
 Utilice `unique_ptr` para la propiedad única, por ejemplo, en la modismo de *pimpl* . \(Vea [Pimpl para encapsulación en tiempo de compilación](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md).\) Cree `unique_ptr` el objetivo principal de todas las expresiones explícitas de `new` .  
  
```cpp  
unique_ptr<widget> p(new widget());  
```  
  
 Puede utilizar los punteros sin formato para que la propiedad y la observación.  Un puntero no propietario puede colgar, pero no puede perder.  
  
```cpp  
class node {  
  ...  
  vector<unique_ptr<node>> children; // node owns children  
  node* parent; // node observes parent, which is not a concern  
  ...  
};  
node::node() : parent(...) { children.emplace_back(new node(...) ); }  
  
```  
  
 Cuando se requiere la optimización del rendimiento, es posible que tenga que utilizar *bien\- encapsulado* poseyendo punteros y llamadas explícitas para eliminar.  Un ejemplo es cuando se implementa posee la estructura de datos de bajo nivel.  
  
### Duración Pila\-basada  
 En C\+\+ moderno, *el ámbito pila\- basado* es una manera eficaz de escribir código eficaz porque combina *duración automática de la pila* y *duración del miembro de datos* con el alto seguimiento de la eficacia\- duración es esencialmente libre de sobrecarga.  La duración de objeto del montón requiere la administración manual diligente y puede ser el origen de pérdidas de recursos y de la pérdida de eficacia, sobre todo cuando se trabaja con punteros sin formato.  Considere este código, que muestra el ámbito pila\- basado:  
  
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
  …  
  w.draw();  
  …  
} // automatic destruction and deallocation for w and w.g  
  // automatic exception safety,   
  // as if "finally { w.dispose(); w.g.dispose(); }"  
  
```  
  
 Utilice la duración estática con moderación \(static globales, static locales de la función\) porque pueden surgir problemas.  ¿Qué ocurre al constructor de un objeto global produce una excepción?  Normalmente, la aplicación critica de manera que puede ser difícil de depurar.  El orden de la construcción es problemático para objetos estáticos de duración, y no es simultaneidad\- seguro.  No solo es la construcción del objeto un problema, orden de destrucción puede ser compleja, sobre todo cuando está implicado el polimorfismo.  Aunque el objeto o la variable no es polimórfica y no tiene construcción\/destrucción complejas de ordenación, existen la aplicación simultaneidad subproceso\- segura.  Una aplicación multiproceso no puede modificar a los datos en objetos estáticos sin tener almacenamiento local de subprocesos, el recurso se bloquea, y precauciones especiales.  
  
## Vea también  
 [Aquí está otra vez C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)