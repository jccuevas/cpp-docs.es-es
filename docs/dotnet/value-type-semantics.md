---
title: "La semántica de tipos de valor | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interior_ptr keyword [C++]
- virtual functions, value types
- inheritance, value types
- pinning pointers
- pin_ptr keyword [C++]
- __pin keyword
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 21a7d6bcba2fca3fddd6f5e234663d6791398f5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="value-type-semantics"></a>Semántica de los tipos de valor
La semántica de tipos de valor ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 Este es el tipo de valor simple canónico utilizado en las extensiones administradas para especificación de C++:  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
```  
  
 En extensiones administradas, podemos tener cuatro variantes sintácticas de un tipo de valor (donde forms 2 y 3 son el mismo semánticamente):  
  
```  
V v = { 0 };       // Form (1)  
V *pv = 0;         // Form (2) an implicit form of (3)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0; // Form (4) must be local   
```  
  
## <a name="invoking-inherited-virtual-methods"></a>Invocar métodos virtuales heredados  
 `Form (1)`es el objeto de valor canónico, y se entiende razonablemente bien, excepto cuando alguien intenta invocar un método virtual heredado como `ToString()`. Por ejemplo:  
  
```  
v.ToString(); // error!  
```  
  
 Para invocar este método, porque no se ha reemplazado en `V`, el compilador debe tener acceso a la tabla virtual asociada de la clase base. Dado que los tipos de valor son el almacenamiento en estado sin el puntero asociado a su tabla virtual (vptr), este método precisa que `v` realizar la conversión boxing. En el diseño del lenguaje de extensiones administradas, no se admite la conversión boxing implícita pero se debe especificar explícitamente por el programador, como en  
  
```  
__box( v )->ToString(); // Managed Extensions: note the arrow  
```  
  
 El motivo principal detrás de este diseño es pedagógico: mecanismo subyacente debe ser visible para el programador para que entienda el "costo" de no proporcionar una instancia dentro de su tipo de valor. Estaban `V` para que contenga una instancia de `ToString`, no sería necesaria la conversión boxing.  
  
 La complejidad léxica de boxing explícitamente el objeto, pero no el costo subyacente de la conversión boxing, se quita en la nueva sintaxis:  
  
```  
v.ToString(); // new syntax  
```  
  
 pero a costa de erróneo posiblemente el Diseñador de clases como el costo de no tener proporciona una instancia explícita de la `ToString` método dentro de `V`. La razón para preferir la conversión boxing implícita es que, aunque normalmente es solo un diseñador de clases, hay un número ilimitado de usuarios, ninguno de los cuales tendrá la libertad de modificar `V` para eliminar el boxing explícita posiblemente trabajosa.  
  
 Los criterios por los que se va a determinar si se debe o no proporcionar una instancia de reemplazo `ToString` dentro de un valor de clase debe ser la frecuencia y la ubicación de sus usos. Si se llama con poca frecuencia, por supuesto hay pocas ventajas en su definición. De forma similar, si se llama en áreas de rendimiento no es de la aplicación, éste se agrega también no mejorará en gran medida agregará en el rendimiento general de la aplicación. Como alternativa, se puede mantener un controlador de seguimiento para el valor de conversión boxing y llamadas a través de este identificador no requiere conversión boxing.  
  
## <a name="there-is-no-longer-a-value-class-default-constructor"></a>Ya no es un Constructor predeterminado de clase de valor  
 Otra diferencia con un tipo de valor entre extensiones administradas y la nueva sintaxis es la eliminación de la compatibilidad con un constructor predeterminado. Esto es porque hay ocasiones durante la ejecución en el que el CLR puede crear una instancia del tipo de valor sin invocar el constructor predeterminado asociado. Es decir, el intento en extensiones administradas para admitir un constructor predeterminado dentro de un tipo de valor podría no en la práctica puede garantizar. Dada la falta de garantía, se pensó que es mejor quitar por completo la compatibilidad en lugar de tener ser no determinista en su aplicación.  
  
 Esto no es tan complicado como podría parecer inicialmente. Esto es porque cada objeto de un tipo de valor se pone a cero automáticamente (es decir, cada tipo se inicializa en su valor predeterminado). Como resultado, los miembros de una instancia local nunca son indefinidos. En este sentido, la pérdida de la capacidad para definir un constructor predeterminado trivial realmente no es una pérdida en absoluto - y de hecho es más eficaz cuando el CLR realiza.  
  
 El problema es cuando un usuario de extensiones administradas define un constructor predeterminado no trivial. Esto no tiene ninguna asignación a la nueva sintaxis. El código dentro del constructor se tienen que migrarse a un método de inicialización con nombre que, a continuación, tendría que se debe invocar explícitamente por el usuario.  
  
 En caso contrario, se modifica la declaración de un objeto de tipo de valor dentro de la nueva sintaxis. El inconveniente de esto es que los tipos de valor no pueden usarse para el ajuste de tipos nativos por las razones siguientes:  
  
-   No hay ninguna compatibilidad para un destructor dentro de un tipo de valor. Es decir, no hay ninguna manera de automatizar un conjunto de acciones desencadenadas al final de la duración de un objeto.  
  
-   Una clase nativa puede incluirse solo dentro de un tipo administrado como un puntero que, a continuación, se asigna en el montón nativo.  
  
 Nos gustaría que va a contener una pequeña clase nativa en un tipo de valor en lugar de un tipo de referencia para evitar una doble asignación de montones: el montón nativo para albergar el tipo nativo y el montón CLR para albergar el contenedor administrado. Una clase nativa dentro de un tipo de valor de ajuste permite evitar el montón administrado, pero no proporciona ninguna manera para automatizar la recuperación de la memoria de montón nativo. Tipos de referencia son el único tipo administrado en el que se va a ajustar las clases nativas no triviales.  
  
## <a name="interior-pointers"></a>Punteros interiores  
 `Form (2)`y `Form (3)` versiones posteriores pueden direccionar casi cualquier cosa (es decir, cualquier elemento administrado o nativo). Por ejemplo, por lo tanto, se permiten todos los requisitos siguientes en extensiones administradas:  
  
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
  
 Por lo tanto, un `V*` puede direccionar una ubicación dentro de un bloque local (y, por tanto, puede estar pendiente), en el ámbito global, dentro de nativo (por ejemplo, si ya se ha eliminado el objeto al que apunta), un montón dentro del montón CLR (y por lo tanto, se efectuará un seguimiento de lo reubicar durante la recolección de elementos no utilizados) y en el interior de un objeto de referencia en el montón CLR (un puntero interior, tal y como se denomina, también de forma transparente un seguimiento).  
  
 En extensiones administradas, no hay ninguna manera de separar los aspectos nativos de una `V*`; es decir, se trata en inclusive, que controla la posibilidad de que direccione un objeto o subobjeto en el montón administrado.  
  
 En la nueva sintaxis, un puntero de tipo de valor se divide en dos tipos: `V*`, que se limita a ubicaciones de montón no CLR y el puntero interior, `interior_ptr<V>`, lo que permite pero no necesita una dirección dentro del montón administrado.  
  
```  
// may not address within managed heap   
V *pv = 0;   
  
// may or may not address within managed heap  
interior_ptr<V> pvgc = nullptr;   
```  
  
 `Form (2)`y `Form (3)` de extensiones administradas se asignan en `interior_ptr<V>`. `Form (4)`es un controlador de seguimiento. Trata de todo el objeto que se ha aplicado conversión boxing dentro del montón administrado. Se traduce en la nueva sintaxis en una `V^`,  
  
```  
V^ pvbx = nullptr; // __box V* pvbx = 0;    
```  
  
 Las declaraciones siguientes en extensiones administradas, todas se asignan a punteros interiores en la nueva sintaxis. (Son tipos de valor dentro de la `System` espacio de nombres.)  
  
```  
Int32 *pi;   // => interior_ptr<Int32> pi;  
Boolean *pb; // => interior_ptr<Boolean> pb;  
E *pe;       // => interior_ptr<E> pe; // Enumeration  
```  
  
 Los tipos integrados no se consideran tipos administrados, aunque actúan como alias para los tipos dentro de la `System` espacio de nombres. Por lo tanto cumplirse las siguientes asignaciones entre extensiones administradas y la nueva sintaxis:  
  
```  
int * pi;     // => int* pi;  
int __gc * pi2; // => interior_ptr<int> pi2;  
```  
  
 Al traducir una `V*` en su programa existente, la estrategia más conservadora es siempre convertirlo en un `interior_ptr<V>`. Se trata cómo se trató en extensiones administradas. En la nueva sintaxis, el programador tiene la opción de restringir un tipo de valor a direcciones de montón no administrado especificando `V*` en lugar de un puntero interior. Si, al traducir el programa, puede realizar una finalización transitiva de todos sus usos y estar seguro de que no hay ninguna dirección asignada en el montón administrado, a continuación, dejando como `V*` es correcto.  
  
## <a name="pinning-pointers"></a>Fijar punteros  
 El recolector de elementos no utilizados puede mover opcionalmente objetos que residen en el montón CLR a diferentes ubicaciones dentro del montón, normalmente durante la fase de compactación. Este movimiento no es un problema para realizar un seguimiento identificadores, referencias de seguimiento y punteros interiores que actualizan estas entidades de forma transparente. Este movimiento es un problema, sin embargo, si el usuario ha pasado la dirección de un objeto en el montón CLR fuera del entorno en tiempo de ejecución. En este caso, el movimiento volátil del objeto es probable que provocan un error en tiempo de ejecución. Para excluir objetos como éstos se traslada, se anclarlos localmente a su ubicación en el ámbito de su uso externo.  
  
 En extensiones administradas, un *puntero anclado* se declara calificando una declaración de puntero con el `__pin` palabra clave. Este es un ejemplo modificado ligeramente de la especificación de extensiones administradas:  
  
```  
__gc struct H { int j; };  
  
int main()   
{  
   H * h = new H;  
   int __pin * k = & h -> j;  
  
   // ...  
};  
```  
  
 En el nuevo diseño de lenguaje, un puntero anclado se declara con una sintaxis análoga a la de un puntero interior.  
  
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
  
 Un puntero anclado en la nueva sintaxis es un caso especial de un puntero interior. Permanecen las restricciones originales para un puntero anclado. Por ejemplo, no se puede usar como un parámetro o valor devuelto de un método; se puede declarar solo en un objeto local. Un número de restricciones adicionales, sin embargo, se han agregado en la nueva sintaxis.  
  
 El valor predeterminado de un puntero anclado es `nullptr`, no `0`. A `pin_ptr<>` no se inicializó o asignado `0`. Todas las asignaciones de `0` en el código existente deberá cambiarse a `nullptr`.  
  
 Un puntero anclado en extensiones administradas se permitía a direccionar un objeto entero, como en el siguiente ejemplo tomado de la especificación de extensiones administradas:  
  
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
  
 En la nueva sintaxis, anclar todo el objeto devuelto por la `new` no se admite la expresión. En su lugar, la dirección del miembro interior debe fijarse. Por ejemplo,  
  
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
 [Tipos de valor y sus comportamientos (C++ / CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Clases y estructuras](../windows/classes-and-structs-cpp-component-extensions.md)   
 [interior_ptr (C++ / CLI)](../windows/interior-ptr-cpp-cli.md)   
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)