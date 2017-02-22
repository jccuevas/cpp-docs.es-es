---
title: "C&#243;mo: Dise&#241;ar para la seguridad de las excepciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 19ecc5d4-297d-4c4e-b4f3-4fccab890b3d
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# C&#243;mo: Dise&#241;ar para la seguridad de las excepciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una de las ventajas del mecanismo de excepciones es que la ejecución, así como los datos sobre la excepción, saltan directamente de la instrucción que produce la excepción a la primera instrucción catch que la controla.  El controlador puede ser cualquier número de niveles en la pila de llamadas.  Las funciones a las que se llama entre la instrucción try y la instrucción throw no se requieren para saber nada sobre la excepción que se produce.  Sin embargo, tienen que diseñarse de forma que puedan quedar fuera de ámbito “inesperadamente” en cualquier punto donde una excepción pudiera propagarse de arriba a abajo, y lo hagan sin dejar detrás objetos parcialmente creados, memoria perdida o estructuras de datos que están en estado inutilizable.  
  
## Técnicas básicas  
 Una directiva sólida de control de excepciones requiere una reflexión cuidadosa y debe formar parte del proceso de diseño.  Por lo general, la mayoría de las excepciones se detectan y se producen en las capas inferiores de un módulo de software, pero estas capas no tienen normalmente suficiente contexto para controlar el error o para exponer un mensaje a los usuarios finales.  En las capas centrales, las funciones pueden detectar y volver a producir una excepción cuando tienen que inspeccionar el objeto de excepción o cuando pueden proporcionar información útil adicional para la capa superior que detecta en última instancia la excepción.  Una función debe detectar y “pasar” una excepción solo si puede recuperarse completamente de ella.  En muchos casos, el comportamiento correcto en las capas centrales consiste en dejar que una excepción se propague hacia arriba en la pila de llamadas.  Incluso en la capa superior, puede ser conveniente dejar que una excepción no controlada termine un programa si la excepción hace que quede en un estado en el que no se puede garantizar la corrección.  
  
 Independientemente de cómo una función controla una excepción, para ayudar a garantizar que es “segura para excepciones”, debe diseñarse según las reglas básicas siguientes.  
  
### Mantener clases de recursos simples  
 Cuando se encapsula la administración de recursos manual en las clases, use una clase que no haga nada más que administrar cada recurso; de lo contrario, podrían producirse pérdidas.  Utilice [punteros inteligentes](../cpp/smart-pointers-modern-cpp.md) cuando sea posible, como se muestra en el ejemplo siguiente.  Este ejemplo es deliberadamente artificial y simplista para resaltar las diferencias cuando se utiliza `shared_ptr`.  
  
```cpp  
// old-style new/delete version  
class NDResourceClass {  
private:  
    int*   m_p;  
    float* m_q;  
public:  
    NDResourceClass() : m_p(0), m_q(0) {  
        m_p = new int;  
        m_q = new float;  
    }  
  
    ~NDResourceClass() {  
        delete m_p;  
        delete m_q;  
    }  
    // Potential leak! When a constructor emits an exception,   
    // the destructor will not be invoked.     
};  
  
// shared_ptr version  
#include <memory>  
  
using namespace std;  
  
class SPResourceClass {  
private:  
    shared_ptr<int> m_p;  
    shared_ptr<float> m_q;  
public:  
    SPResourceClass() : m_p(new int), m_q(new float) { }  
    // Implicitly defined dtor is OK for these members,   
    // shared_ptr will clean up and avoid leaks regardless.  
};  
  
// A more powerful case for shared_ptr  
  
class Shape {  
    // ...  
};  
  
class Circle : public Shape {  
    // ...  
};  
  
class Triangle : public Shape {  
    // ...  
};  
  
class SPShapeResourceClass {  
private:  
    shared_ptr<Shape> m_p;  
    shared_ptr<Shape> m_q;  
public:  
    SPShapeResourceClass() : m_p(new Circle), m_q(new Triangle) { }  
};  
  
```  
  
### Utilizar la expresión RAII para administrar recursos  
 Para que una función sea segura para excepciones, una función debe garantizar que los objetos que ha asignado mediante `malloc` o `new` se destruyeron y que todos los recursos, por ejemplo, los identificadores de archivos, están cerrados o liberados incluso si se produce una excepción.  La expresión *Resource Acquisition Is Initialization* \(RAII\) enlaza la administración de estos recursos al tiempo de vida de las variables automáticas.  Cuando una función sale del ámbito, ya sea porque vuelve normalmente o debido a una excepción, se invocan los destructores para todas las variables automáticas totalmente implementadas.  Un objeto contenedor RAII, por ejemplo, un puntero inteligente, llama a la función de eliminación o cierre adecuada en el destructor.  En el código seguro para excepciones, pasar la propiedad de cada recurso inmediatamente a algún tipo de objeto RAII tiene una importancia crítica.  Observe que las clases `vector`, `string`, `make_shared`, `fstream` y otras similares controlan la adquisición de recursos automáticamente. Sin embargo, las construcciones `shared_ptr` tradicional y `unique_ptr` son especiales porque la adquisición de recursos la realiza el usuario en lugar del objeto; por consiguiente, se consideran *Resource Release Is Destruction* pero son cuestionables como RAII.  
  
## Las tres garantías de excepción  
 Normalmente, la seguridad de la excepción se explica en términos de tres garantías de excepción que una función puede proporcionar: la *garantía de que no haya error*, la *garantía segura* y la *garantía básica*.  
  
### Garantía de que no haya error  
 La garantía de que no haya error \(o “ningún throw”\) es la mayor garantía que una función puede proporcionar.  Indica que la función no producirá una excepción ni permitirá que se propague.  Sin embargo, esta garantía no se puede proporcionar confiablemente a menos que \(a\) se sepa que todas las funciones a las que llama la función tampoco producen ningún error, \(b\) se sepa que cualquier excepción que se produzca se detectará antes de que llegue a esta función o \(c\) se sepa cómo detectar y controlar correctamente todas las excepciones que puedan tener acceso a esta función.  
  
 La garantía segura y la seguridad básica se basan en la hipótesis de que los destructores no producen ningún error.  Todos los contenedores y tipos de la garantía de la biblioteca estándar que los destructores no producen.  También hay un requisito inverso: la biblioteca estándar requiere que los tipos definidos por el usuario que se le proporcionan \(por ejemplo, como argumentos de plantilla\) deben tener destructores no que produzcan excepciones.  
  
### Garantía segura  
 La garantía segura establece que, si una función queda fuera de ámbito debido a una excepción, no se perderá memoria y el estado del programa no se modificará.  Una función que proporciona una garantía segura es básicamente una transacción que tiene semántica de confirmación o recuperación, es decir, se ejecuta correctamente por completo o no tiene ningún efecto.  
  
### Garantía básica  
 La garantía básica es la más débil de las tres.  Sin embargo, podría ser la mejor opción cuando una garantía segura es demasiado costosa en cuanto al uso de memoria o al rendimiento.  La garantía básica establece que si se produce una excepción, no se perderá memoria y el objeto aún estará en un estado utilizable aunque los datos se hayan modificado.  
  
## Clases seguras para excepciones  
 Una clase puede ayudar a garantizar su propia seguridad para excepciones aunque la utilicen funciones no seguras, lo que evita que se construya o se destruya parcialmente.  Si existe un constructor de clase antes de la finalización, no se crea nunca el objeto ni se llama nunca al destructor.  Aunque las variables automáticas que se inicializan antes de la excepción invoquen sus destructores, se perderá la memoria asignada dinámicamente o los recursos no administrados por un puntero inteligente o una variable automática.  
  
 Los tipos integrados garantizan todos que no se produzca ningún error y los tipos de la biblioteca estándar admiten la garantía básica como mínimo.  Siga estas instrucciones para cualquier tipo definido por el usuario que deba ser seguro para excepciones:  
  
-   Utilice punteros inteligentes u otros contenedores de tipo RAII para administrar todos los recursos.  Evite la funcionalidad de administración de recursos en el destructor de clase, porque el destructor no se invocará si el constructor produce una excepción.  Sin embargo, si la clase es un administrador de recursos dedicado que controla un único recurso, es aceptable utilizar el destructor para administrar los recursos.  
  
-   Comprenda que una excepción producida en un constructor de clase base no se pasará a un constructor de clase derivada.  Si desea convertir y volver a producir la excepción de la clase base en un constructor derivado, utilice un bloque try de función.  Para obtener más información, vea [Cómo: Identificador de excepciones en la clase base Constructores \(C\+\+\)](http://msdn.microsoft.com/es-es/53bb822e-785b-4581-9517-210dd05060a3).  
  
-   Considere la posibilidad de almacenar todo el estado de la clase en un miembro de datos que esté ajustado en un puntero inteligente, especialmente si una clase incluye el concepto de que la “inicialización puede producir errores”. Aunque C\+\+ permite miembros de datos sin inicializar, no admite instancias de clase sin inicializar o parcialmente inicializadas.  Un constructor debe ejecutarse correctamente o producir un error; no se crea ningún objeto si el constructor no se ejecuta hasta completarse.  
  
-   No permita que ninguna excepción se escape del destructor.  Un axioma básico de C\+\+ establece que los destructores no deben permitir que una excepción se propague hacia arriba por la pila de llamadas.  Si un destructor debe realizar una operación que pueda producir una excepción, debe hacerlo en un bloque try y pasar la excepción.  La biblioteca estándar proporciona esta garantía en todos los destructores que define.  
  
## Vea también  
 [Controlar errores y excepciones](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Cómo: Interfaz entre código excepcional y no excepcional](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)