---
title: Filtrar Diseño de seguridad de las excepciones
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19ecc5d4-297d-4c4e-b4f3-4fccab890b3d
ms.openlocfilehash: 37ebcc646864774b15513c9e1891ba14e0705298
ms.sourcegitcommit: 35c4b3478f8cc310ebbd932a18963ad8ab846ed9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2019
ms.locfileid: "59237203"
---
# <a name="how-to-design-for-exception-safety"></a>Filtrar Diseño de seguridad de las excepciones

Una de las ventajas del mecanismo de excepciones es que la ejecución, así como los datos sobre la excepción, saltan directamente de la instrucción que produce la excepción a la primera instrucción catch que la controla. El controlador puede ser cualquier número de niveles en la pila de llamadas. Las funciones a las que se llama entre la instrucción try y la instrucción throw no se requieren para saber nada sobre la excepción que se produce.  Sin embargo, tienen que diseñarse de forma que puedan quedar fuera de ámbito “inesperadamente” en cualquier punto donde una excepción pudiera propagarse de arriba a abajo, y lo hagan sin dejar detrás objetos parcialmente creados, memoria perdida o estructuras de datos que están en estado inutilizable.

## <a name="basic-techniques"></a>Técnicas básicas

Una directiva sólida de control de excepciones requiere una reflexión cuidadosa y debe formar parte del proceso de diseño. Por lo general, la mayoría de las excepciones se detectan y se producen en las capas inferiores de un módulo de software, pero estas capas no tienen normalmente suficiente contexto para controlar el error o para exponer un mensaje a los usuarios finales. En las capas centrales, las funciones pueden detectar y volver a producir una excepción cuando tienen que inspeccionar el objeto de excepción o cuando pueden proporcionar información útil adicional para la capa superior que detecta en última instancia la excepción. Una función debe detectar y “pasar” una excepción solo si puede recuperarse completamente de ella. En muchos casos, el comportamiento correcto en las capas centrales consiste en dejar que una excepción se propague hacia arriba en la pila de llamadas. Incluso en la capa superior, puede ser conveniente dejar que una excepción no controlada termine un programa si la excepción hace que quede en un estado en el que no se puede garantizar la corrección.

Independientemente de cómo una función controla una excepción, para ayudar a garantizar que es “segura para excepciones”, debe diseñarse según las reglas básicas siguientes.

### <a name="keep-resource-classes-simple"></a>Mantener clases de recursos simples

Al encapsular la administración de recursos manual de clases, use una clase que no hace nada, salvo que administrar un único recurso. Si se mantiene la clase simple, reducir el riesgo de introducir pérdidas de recursos. Use [inteligente punteros](../cpp/smart-pointers-modern-cpp.md) cuando sea posible, como se muestra en el ejemplo siguiente. Este ejemplo es deliberadamente artificial y simplista para resaltar las diferencias cuando se utiliza `shared_ptr`.

```cpp
// old-style new/delete version
class NDResourceClass {
private:
    int*   m_p;
    float* m_q;
public:
    NDResourceClass() : m_p(0), m_q(0) {
        m_p = new int;
        m_q = new float;
    }

    ~NDResourceClass() {
        delete m_p;
        delete m_q;
    }
    // Potential leak! When a constructor emits an exception,
    // the destructor will not be invoked.
};

// shared_ptr version
#include <memory>

using namespace std;

class SPResourceClass {
private:
    shared_ptr<int> m_p;
    shared_ptr<float> m_q;
public:
    SPResourceClass() : m_p(new int), m_q(new float) { }
    // Implicitly defined dtor is OK for these members,
    // shared_ptr will clean up and avoid leaks regardless.
};

// A more powerful case for shared_ptr

class Shape {
    // ...
};

class Circle : public Shape {
    // ...
};

class Triangle : public Shape {
    // ...
};

class SPShapeResourceClass {
private:
    shared_ptr<Shape> m_p;
    shared_ptr<Shape> m_q;
public:
    SPShapeResourceClass() : m_p(new Circle), m_q(new Triangle) { }
};
```

### <a name="use-the-raii-idiom-to-manage-resources"></a>Utilizar la expresión RAII para administrar recursos

Para que sea seguro ante excepciones, una función debe asegurarse de que los objetos que ha asignado mediante `malloc` o **nuevo** se destruyen, y todos los recursos como identificadores de archivo están cerrados o liberados incluso si se produce una excepción. El *Resource Acquisition Is Initialization* expresión (RAII) enlaza la administración de estos recursos para la duración de las variables automáticas. Cuando una función sale del ámbito, ya sea porque vuelve normalmente o debido a una excepción, se invocan los destructores para todas las variables automáticas totalmente implementadas. Un objeto contenedor RAII, por ejemplo, un puntero inteligente, llama a la función de eliminación o cierre adecuada en el destructor. En el código seguro para excepciones, pasar la propiedad de cada recurso inmediatamente a algún tipo de objeto RAII tiene una importancia crítica. Tenga en cuenta que el `vector`, `string`, `make_shared`, `fstream`, y las clases similares controlan la adquisición del recurso para usted.  Sin embargo, `unique_ptr` tradicional y `shared_ptr` construcciones son especiales porque la adquisición de recursos se realiza por el usuario en lugar del objeto; por lo tanto, se consideran *Resource Release Is Destruction* pero son cuestionables como RAII.

## <a name="the-three-exception-guarantees"></a>Las tres garantías de excepción

Normalmente, se explica la seguridad de las excepciones en cuanto a las tres garantías de excepción que se puede proporcionar una función: la *garantía de ningún error*, *garantía segura*y el *garantía básica* .

### <a name="no-fail-guarantee"></a>Garantía de que no haya error

La garantía de que no haya error (o “ningún throw”) es la mayor garantía que una función puede proporcionar. Indica que la función no producirá una excepción ni permitirá que se propague. Sin embargo, esta garantía no se puede proporcionar confiablemente a menos que (a) se sepa que todas las funciones a las que llama la función tampoco producen ningún error, (b) se sepa que cualquier excepción que se produzca se detectará antes de que llegue a esta función o (c) se sepa cómo detectar y controlar correctamente todas las excepciones que puedan tener acceso a esta función.

La garantía segura y la seguridad básica se basan en la hipótesis de que los destructores no producen ningún error. Todos los contenedores y tipos de la garantía de la biblioteca estándar que los destructores no producen. También es un requisito inverso: La biblioteca estándar requiere que los definidos por el usuario tipos que se les proporciona, por ejemplo, como argumentos de plantilla, debe tener destructores no producen excepciones.

### <a name="strong-guarantee"></a>Garantía segura

La garantía segura establece que, si una función queda fuera de ámbito debido a una excepción, no se perderá memoria y el estado del programa no se modificará. Una función que proporciona una garantía segura es básicamente una transacción que tiene semántica de confirmación o recuperación, es decir, se ejecuta correctamente por completo o no tiene ningún efecto.

### <a name="basic-guarantee"></a>Garantía básica

La garantía básica es la más débil de las tres. Sin embargo, podría ser la mejor opción cuando una garantía segura es demasiado costosa en cuanto al uso de memoria o al rendimiento. La garantía básica establece que si se produce una excepción, no se perderá memoria y el objeto aún estará en un estado utilizable aunque los datos se hayan modificado.

## <a name="exception-safe-classes"></a>Clases seguras para excepciones

Una clase puede ayudar a garantizar su propia seguridad para excepciones aunque la utilicen funciones no seguras, lo que evita que se construya o se destruya parcialmente. Si existe un constructor de clase antes de la finalización, no se crea nunca el objeto ni se llama nunca al destructor. Aunque las variables automáticas que se inicializan antes de la excepción invoquen sus destructores, se perderá la memoria asignada dinámicamente o los recursos no administrados por un puntero inteligente o una variable automática.

Los tipos integrados garantizan todos que no se produzca ningún error y los tipos de la biblioteca estándar admiten la garantía básica como mínimo. Siga estas instrucciones para cualquier tipo definido por el usuario que deba ser seguro para excepciones:

- Utilice punteros inteligentes u otros contenedores de tipo RAII para administrar todos los recursos. Evite la funcionalidad de administración de recursos en el destructor de clase, porque el destructor no se invocará si el constructor produce una excepción. Sin embargo, si la clase es un administrador de recursos dedicado que controla un único recurso, es aceptable utilizar el destructor para administrar los recursos.

- Comprenda que una excepción producida en un constructor de clase base no se pasará a un constructor de clase derivada. Si desea convertir y volver a producir la excepción de la clase base en un constructor derivado, utilice un bloque try de función.

- Considere la posibilidad de almacenar todo el estado de la clase en un miembro de datos que esté ajustado en un puntero inteligente, especialmente si una clase incluye el concepto de que la “inicialización puede producir errores”. Aunque C++ permite miembros de datos sin inicializar, no admite instancias de clase sin inicializar o parcialmente inicializadas. Un constructor debe ejecutarse correctamente o producir un error; no se crea ningún objeto si el constructor no se ejecuta hasta completarse.

- No permita que ninguna excepción se escape del destructor. Un axioma básico de C++ establece que los destructores no deben permitir que una excepción se propague hacia arriba por la pila de llamadas. Si un destructor debe realizar una operación que pueda producir una excepción, debe hacerlo en un bloque try y pasar la excepción. La biblioteca estándar proporciona esta garantía en todos los destructores que define.

## <a name="see-also"></a>Vea también

[Controlar errores y excepciones (C++ moderno)](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Filtrar La interfaz entre código excepcional y no excepcional](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)
