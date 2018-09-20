---
title: Semántica de tipos de valor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
- virtual functions, value types
- inheritance, value types
- pinning pointers
- pin_ptr keyword [C++]
- __pin keyword
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 72dc6a613616d13e9ff92e8af0c39c63dfe63162
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413801"
---
# <a name="value-type-semantics"></a>Semántica de los tipos de valor

Semántica de tipos de valor ha cambiado de extensiones administradas para C++ a Visual C++.

Aquí es el tipo de valor simple canónico utilizado en las extensiones administradas para la especificación de C++:

```
__value struct V { int i; };
__gc struct R { V vr; };
```

En extensiones administradas, podemos tener cuatro variantes sintácticas de un tipo de valor (donde formularios 2 y 3 son el mismo semánticamente):

```
V v = { 0 };       // Form (1)
V *pv = 0;         // Form (2) an implicit form of (3)
V __gc *pvgc = 0;  // Form (3)
__box V* pvbx = 0; // Form (4) must be local
```

## <a name="invoking-inherited-virtual-methods"></a>Invocar métodos virtuales heredados

`Form (1)` es el objeto de valor canónico, y se entiende razonablemente bien, excepto cuando alguien intenta invocar un método virtual heredado como `ToString()`. Por ejemplo:

```
v.ToString(); // error!
```

Para invocar este método, porque no se reemplaza en `V`, el compilador debe tener acceso a la tabla virtual asociada de la clase base. Dado que los tipos de valor son el almacenamiento en estado sin el puntero asociado a su tabla virtual (vptr), esto requiere que `v` realizar la conversión boxing. En el diseño del lenguaje de extensiones administradas, no se admite la conversión boxing implícita, pero debe especificarse explícitamente por el programador, como en

```
__box( v )->ToString(); // Managed Extensions: note the arrow
```

El motivo principal de este diseño es pedagógico: mecanismo subyacente debe ser visible para el programador para que entienda el "costo" de no proporcionar una instancia dentro del tipo de valor. Eran `V` para contener una instancia de `ToString`, no sería necesaria la conversión boxing.

La complejidad léxica de explícitamente la conversión boxing del objeto, pero no el costo subyacente de la conversión boxing, se ha quitado de la nueva sintaxis:

```
v.ToString(); // new syntax
```

pero a costa de engañoso, posiblemente, el Diseñador de clases como el costo de no tener proporciona una instancia explícita de la `ToString` método dentro de `V`. La razón para preferir la conversión boxing implícita es que, aunque normalmente es solo un diseñador de clases, hay un número ilimitado de usuarios, ninguno de los cuales tendrá la libertad de modificar `V` para eliminar el cuadro posiblemente oneroso explícito.

Los criterios por los que se va a determinar si se deben proporcionar una instancia de reemplazo `ToString` dentro de un valor de clase debe ser la frecuencia y la ubicación de su uso. Si se llama con poca frecuencia, por supuesto hay pocas ventajas en su definición. De forma similar, si se llama en áreas que no son de alto rendimiento de la aplicación, éste se agrega también no mejorará en gran medida agregará el rendimiento general de la aplicación. Como alternativa, se puede mantener un controlador de seguimiento en el valor con conversión boxing, y las llamadas a través de ese controlador no requerirían conversión boxing.

## <a name="there-is-no-longer-a-value-class-default-constructor"></a>Ya No es un Constructor predeterminado de clase de valor

Otra diferencia con un tipo de valor entre extensiones administradas y la nueva sintaxis es la eliminación de la compatibilidad con un constructor predeterminado. Esto es porque hay ocasiones durante la ejecución en el que el CLR puede crear una instancia del tipo de valor sin invocar el constructor predeterminado asociado. Es decir, el intento en extensiones administradas para admitir un constructor predeterminado dentro de un tipo de valor podría no en la práctica se puede garantizar. ¿Dada la falta de garantía, pensó que mejor quitar por completo la compatibilidad en lugar de tener ser no deterministas en su aplicación.

Esto no es tan malo como podría parecer inicialmente. Esto es porque cada objeto de un tipo de valor se pone automáticamente (es decir, cada tipo se inicializa en su valor predeterminado). Como resultado, los miembros de una instancia local nunca son indefinidos. En este sentido, la pérdida de la capacidad para definir un constructor predeterminado trivial realmente no es una pérdida en absoluto - y de hecho es más eficaz cuando el CLR realiza.

El problema es cuando un usuario de extensiones administradas define un constructor predeterminado no trivial. Esto no tiene ninguna asignación a la nueva sintaxis. El código dentro del constructor debe migrarse a un método de inicialización con nombre que tendría que invocar explícitamente por el usuario.

En caso contrario, se modifica la declaración de un objeto de tipo de valor dentro de la nueva sintaxis. El inconveniente de esto es que los tipos de valor no son satisfactorios para el ajuste de los tipos nativos por las razones siguientes:

- No hay ninguna compatibilidad para un destructor dentro de un tipo de valor. Es decir, no hay ninguna manera de automatizar un conjunto de acciones desencadenadas por el final de la duración del objeto.

- Una clase nativa puede incluirse solo dentro de un tipo administrado como un puntero, que, a continuación, se asigna en el montón nativo.

Nos gustaría ajustar una pequeña clase nativa en un tipo de valor en lugar de un tipo de referencia para evitar una asignación del montón doble: el montón nativo para almacenar el tipo nativo y el montón CLR para albergar el contenedor administrado. Una clase nativa dentro de un tipo de valor de ajuste le permite evitar el montón administrado, pero no proporciona ninguna manera de automatizar la recuperación de la memoria de montón nativo. Tipos de referencia son el único tipo administrado en el que se va a incluir clases nativas no triviales.

## <a name="interior-pointers"></a>Punteros interiores

`Form (2)` y `Form (3)` encima puede direccionar casi cualquier cosa (es decir, cualquier elemento administrado o nativo). Por ejemplo, por lo tanto, se permiten todos los archivos siguientes en extensiones administradas:

```
__value struct V { int i; };
__gc struct R { V vr; };

V v = { 0 };  // Form (1)
V *pv = 0;  // Form (2)
V __gc *pvgc = 0;  // Form (3)
__box V* pvbx = 0;  // Form (4)

R* r;

pv = &v;            // address a value type on the stack
pv = __nogc new V;  // address a value type on native heap
pv = pvgc;          // we are not sure what this addresses
pv = pvbx;          // address a boxed value type on managed heap
pv = &r->vr;        // an interior pointer to value type within a
                    //    reference type on the managed heap
```

Por lo tanto, un `V*` puede resolver una ubicación dentro de un bloque local (y por lo tanto, puede estar pendiente), en el ámbito global, dentro de nativo en el montón (por ejemplo, si ya ha eliminado el objeto al que apunta) dentro del montón CLR (y por lo tanto, se realizará un seguimiento, en caso se reubica durante la recolección de elementos no utilizados) y en el interior de un objeto de referencia en el montón CLR (un puntero interior, tal como se llama a esto, también de forma transparente un seguimiento).

En extensiones administradas, no hay ninguna manera de separar los aspectos nativos de una `V*`; es decir, se trata en inclusive, que controla la posibilidad de que se dirige a un objeto o subobjeto en el montón administrado.

En la nueva sintaxis, un puntero de tipo de valor se divide en dos tipos: `V*`, que está limitado a ubicaciones de montón no CLR y el puntero interior, `interior_ptr<V>`, lo que permite pero no requiere una dirección dentro del montón administrado.

```
// may not address within managed heap
V *pv = 0;

// may or may not address within managed heap
interior_ptr<V> pvgc = nullptr;
```

`Form (2)` y `Form (3)` de extensiones administradas se asignan en `interior_ptr<V>`. `Form (4)` es un controlador de seguimiento. Se ocupa de todo el objeto que se ha aplicado conversión boxing dentro del montón administrado. Se traduce en la nueva sintaxis en una `V^`,

```
V^ pvbx = nullptr; // __box V* pvbx = 0;
```

Las siguientes declaraciones en todos los mapas a punteros interiores en la nueva sintaxis de extensiones administradas. (Son tipos de valor dentro de la `System` espacio de nombres.)

```
Int32 *pi;   // => interior_ptr<Int32> pi;
Boolean *pb; // => interior_ptr<Boolean> pb;
E *pe;       // => interior_ptr<E> pe; // Enumeration
```

Los tipos integrados no se consideran tipos administrados, aunque actúan como alias para los tipos dentro de la `System` espacio de nombres. Por lo tanto cumplirse las siguientes asignaciones entre las extensiones administradas y la nueva sintaxis:

```
int * pi;     // => int* pi;
int __gc * pi2; // => interior_ptr<int> pi2;
```

Al traducir una `V*` en su programa existente, la estrategia más conservadora es siempre convertirlo en un `interior_ptr<V>`. Se trata cómo se trató en extensiones administradas. En la nueva sintaxis, el programador tiene la opción de restringir un tipo de valor a direcciones de montón no administrado mediante la especificación de `V*` en lugar de un puntero interior. Si, al traducir el programa, puede hacer un cierre transitivo de todas sus usos y compruebe que no está asignada ninguna dirección dentro del montón administrado, a continuación, dejando como `V*` está bien.

## <a name="pinning-pointers"></a>Punteros anclados

El recolector de elementos se pueden mover, opcionalmente, los objetos que residen en el montón CLR a diferentes ubicaciones dentro del montón, normalmente durante la fase de compactación. Este movimiento no es un problema al seguimiento de identificadores, referencias de seguimiento y punteros interiores que actualizan estas entidades de forma transparente. Este movimiento es un problema, sin embargo, si el usuario ha pasado la dirección de un objeto en el montón CLR fuera del entorno en tiempo de ejecución. En este caso, el movimiento del objeto volátil es puede provocar un error en tiempo de ejecución. Para excluir objetos como éstos se traslada, se anclarlos localmente a su ubicación en el ámbito de su uso externo.

En extensiones administradas, un *puntero anclado* se declara calificando una declaración de puntero con el `__pin` palabra clave. Este es un ejemplo que se ha modificado ligeramente de la especificación de extensiones administradas:

```
__gc struct H { int j; };

int main()
{
   H * h = new H;
   int __pin * k = & h -> j;

   // ...
};
```

En el nuevo diseño del lenguaje, un puntero anclado se declara con una sintaxis análoga a la de un puntero interior.

```
ref struct H
{
public:
   int j;
};

int main()
{
   H^ h = gcnew H;
   pin_ptr<int> k = &h->j;

   // ...
}
```

Un puntero anclado en la nueva sintaxis es un caso especial de un puntero interior. Permanecen las restricciones originales en un puntero anclado. Por ejemplo, no se puede usar como un parámetro o devolver el tipo de un método; se puede declarar solo en un objeto local. Un número de restricciones adicionales, sin embargo, se han agregado en la nueva sintaxis.

Es el valor predeterminado de un puntero anclado `nullptr`, no `0`. Un `pin_ptr<>` no se puede inicializar ni asignado `0`. Todas las asignaciones de `0` en el código existente se deberá cambiarse a `nullptr`.

Se permite un puntero anclado en extensiones administradas para abordar un objeto completo, como en el ejemplo siguiente, tomado de la especificación de extensiones administradas:

```
__gc class G {
public:
   void incr(int* pi) { pi += 1; }
};
__gc struct H { int j; };
void f( G * g ) {
   H __pin * pH = new H;
   g->incr(& pH -> j);
};
```

En la nueva sintaxis, anclar todo el objeto devuelto por la `new` no se admite la expresión. En su lugar, la dirección del miembro interior debe anclarse. Por ejemplo,

```
ref class G {
public:
   void incr(int* pi) { *pi += 1; }
};
ref struct H { int j; };
void f( G^ g ) {
   H ^ph = gcnew H;
   Console::WriteLine(ph->j);
   pin_ptr<int> pj = &ph->j;
   g->incr(  pj );
   Console::WriteLine(ph->j);
}
```

## <a name="see-also"></a>Vea también

[Tipos de valor y su comportamiento (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)<br/>
[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)