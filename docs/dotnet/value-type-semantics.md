---
title: "Sem&#225;ntica de los tipos de valor | Microsoft Docs"
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
helpviewer_keywords: 
  - "__pin (palabra clave)"
  - "herencia, tipos de valor"
  - "interior_ptr (palabra clave) [C++]"
  - "pin_ptr (palabra clave) [C++]"
  - "fijar punteros"
  - "funciones virtuales, tipos de valor"
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Sem&#225;ntica de los tipos de valor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La semántica de los tipos de valor ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 A continuación se muestra el tipo de valor simple canónico utilizado en la especificación de Extensiones administradas para C\+\+:  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
```  
  
 En Extensiones administradas, podemos tener cuatro variantes sintácticas de un tipo de valor \(donde los formatos 2 y 3 son el mismo semánticamente\):  
  
```  
V v = { 0 };       // Form (1)  
V *pv = 0;         // Form (2) an implicit form of (3)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0; // Form (4) must be local   
```  
  
## Invocar métodos virtuales heredados  
 `Form (1)` es el objeto de valor canónico, y se entiende razonablemente bien, excepto cuando alguien intenta invocar un método virtual heredado como `ToString()`.  Por ejemplo:  
  
```  
v.ToString(); // error!  
```  
  
 Para invocar este método, porque no se ha reemplazado en `V`, el compilador deberá tener acceso a la tabla virtual asociada de la clase base.  Dado que los tipos de valor están almacenados sin el puntero asociado a su tabla virtual \(vptr\), esto requiere que se aplique la conversión boxing a `v`.  En el diseño del lenguaje de Extensiones administradas, no se admite la conversión boxing implícita, por lo que debe especificarla explícitamente el programador, como en  
  
```  
__box( v )->ToString(); // Managed Extensions: note the arrow  
```  
  
 El motivo principal de este tipo de diseño es pedagógico: el mecanismo subyacente debe estar visible para el programador para que entienda el "costo" de no proporcionar una instancia dentro del tipo de valor.  Si `V` incluyera una instancia de `ToString`, no sería necesaria la conversión boxing.  
  
 En la nueva sintaxis se ha quitado la complejidad léxica de aplicar la conversión boxing explícitamente al objeto, pero no el costo subyacente la propia conversión:  
  
```  
v.ToString(); // new syntax  
```  
  
 pero las consecuencias de poder equivocar al Diseñador de clases son menores que no facilitar una instancia explícita del método `ToString` dentro de `V`.  La razón por la que se prefiere la conversión boxing implícita es que normalmente sólo existe un diseñador de clases, mientras que hay un número ilimitado de usuarios, ninguno de los cuales tendrá la libertad de modificar `V` para eliminar la posibilidad de conversión boxing explícita que resulta tan trabajosa.  
  
 El criterio por el que se determina si se debe o no proporcionar una instancia sustitutoria de `ToString` dentro de una clase de valor debe ser la frecuencia y la ubicación de su uso.  Si se llama muy raramente, por supuesto, existe poco beneficio en su definición.  De forma similar, si se llama en áreas de la aplicación que no influyen en el rendimiento, su suma no mejorará en gran medida el rendimiento general de la aplicación.  Alternativamente, se puede mantener un controlador de seguimiento para el valor convertido y las llamadas a través de dicho controlador no requerirían una conversión boxing.  
  
## Ya no hay un constructor predeterminado de clases de valores  
 Otra diferencia con un tipo de valor entre Extensiones administradas y la nueva sintaxis es la eliminación de la compatibilidad de un constructor predeterminado.  Esto se realiza porque hay ocasiones durante la ejecución en las que el CLR puede crear una instancia del tipo de valor sin invocar el constructor predeterminado asociado.  Es decir, el intento en Extensiones administradas de admitir un constructor predeterminado dentro de un tipo de valor no se pudo garantizar en la práctica.  Dada la falta de garantías, se creyó que era mejor quitar la compatibilidad por completo, en lugar de dejar que no tenga ninguna influencia en su aplicación.  
  
 Esto no es tan malo como podría parecer inicialmente.  Esto se debe a que cada objeto de un tipo de valor se pone a cero automáticamente \(es decir, cada tipo se inicializa a su valor predeterminado\).  En consecuencia, los miembros de una instancia local nunca son indefinidos.  En este sentido, la pérdida de la habilidad para definir un constructor predeterminado trivial realmente no es ninguna pérdida, y de hecho es más eficaz cuando lo realiza el CLR.  
  
 El problema es cuando un usuario de Extensiones administradas define un constructor predeterminado no trivial.  Esto no tiene ninguna asignación en la nueva sintaxis.  El código incluido en el constructor se debe migrar a un método de inicialización con nombre, que posteriormente el usuario debe invocar explícitamente.  
  
 Por lo contrario, la declaración de un objeto de tipo de valor dentro de la nueva sintaxis no se ha modificado.  El inconveniente de esto es que los tipos de valor no son satisfactorios para ajustar tipos nativos por las siguientes razones:  
  
-   No hay ninguna compatibilidad para un destructor dentro de un tipo de valor.  Es decir, hay ninguna manera de automatizar un conjunto de acciones desencadenadas al final del período de duración de un objeto.  
  
-   Una clase nativa sólo se puede incluir dentro de un tipo administrado como un puntero, que se asigna a continuación en el montón nativo.  
  
 Se ha incluido una pequeña clase nativa en un tipo de valor en lugar de en un tipo de referencia para evitar una doble asignación de montones: el montón nativo para albergar el tipo nativo, y el montón CLR para albergar el contenedor administrado.  La inclusión de una clase nativa en un tipo de valor permite evitar el montón administrado, pero no deja automatizar la reclamación de la memoria del montón nativo.  Los tipos de referencia son el único tipo administrado en el que se puede incluir clases nativas no triviales.  
  
## Punteros interiores  
 Los parámetros `Form (2)` y `Form (3)` anteriores pueden direccionar casi cualquier cosa \(es decir, cualquier elemento administrado o nativo\).  De este modo, por ejemplo, en Extensiones administradas se permite todo lo siguiente:  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
  
V v = { 0 };  // Form (1)  
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
  
 Así, `V*` puede direccionar una ubicación dentro de un bloque local \(y por ello puede estar pendiente\) en el ámbito global, dentro del montón nativo \(por ejemplo, si el objeto que direcciona ya se ha eliminado\), dentro del montón CLR \(y por ello se supervisará si se debe reubicar durante la recolección de elementos no utilizados\) y en el interior de un objeto de referencia en el montón CLR \(un puntero interior, ya que así se denomina, también se supervisa de forma transparente\).  
  
 En Extensiones administradas, no hay modo de separar los aspectos nativos de `V*`; es decir, se trata como si lo incluyera, lo que permite la posibilidad de que direccione un objeto o subobjeto en el montón administrado.  
  
 En la nueva sintaxis, un puntero de tipo de valor se divide en dos tipos: `V*`, el cual se limita a ubicaciones de montón no CLR, y el puntero interior, `interior_ptr<V>`, el cual permite, pero no requiere, una dirección dentro del montón administrado.  
  
```  
// may not address within managed heap   
V *pv = 0;   
  
// may or may not address within managed heap  
interior_ptr<V> pvgc = nullptr;   
```  
  
 `Form (2)` y `Form (3)` de Extensiones administradas se asignan a `interior_ptr<V>`.  `Form (4)` es un controlador de seguimiento.  Éste direcciona todo el objeto al que se ha aplicado la conversión boxing dentro del montón administrado.  Se traduce en la nueva sintaxis como `V^`  
  
```  
V^ pvbx = nullptr; // __box V* pvbx = 0;    
```  
  
 Todas las siguientes declaraciones de Extensiones administradas se asignan a punteros interiores en la nueva sintaxis. \(Son tipos de valor dentro del espacio de nombres `System`\).  
  
```  
Int32 *pi;   // => interior_ptr<Int32> pi;  
Boolean *pb; // => interior_ptr<Boolean> pb;  
E *pe;       // => interior_ptr<E> pe; // Enumeration  
```  
  
 Los tipos integrados no se consideran tipos administrados, aunque actúan como alias para los tipos incluidos en el espacio de nombres `System`.  De este modo, son ciertas las siguientes asignaciones entre Extensiones administradas y la nueva sintaxis:  
  
```  
int * pi;     // => int* pi;  
int __gc * pi2; // => interior_ptr<int> pi2;  
```  
  
 Al traducir `V*` en su programa existente, la estrategia más conservadora es siempre convertirlo en `interior_ptr<V>`.  Así es cómo se trató en Extensiones administradas.  En la nueva sintaxis, el programador tiene la opción de restringir un tipo de valor a direcciones de montón no administrado especificando `V*` en lugar de un puntero interior.  Si, al traducir el programa, puede realizar una finalización transitiva de todos sus usos y comprobar que no hay asignada ninguna dirección dentro del montón administrado, entonces es correcto dejarlo como `V*`.  
  
## Punteros anclados  
 El recolector de elementos no utilizados puede mover opcionalmente objetos que residen en el montón CLR a diferentes ubicaciones dentro del montón, normalmente durante una fase de consolidación.  Este movimiento no es un problema para los controladores de seguimiento, referencias de seguimiento y punteros interiores que actualizan estas entidades de forma transparente.  Sin embargo, este movimiento sí es un problema si el usuario ha pasado la dirección de un objeto en el montón CLR fuera del entorno en tiempo de ejecución.  En este caso, es probable que el movimiento volátil del objeto produzca un error en tiempo de ejecución.  Para que no se desplacen objetos como éstos, hay que anclarlos localmente a su ubicación en el ámbito de su uso externo.  
  
 En Extensiones administradas, un *puntero anclado* se declara calificando una declaración de puntero con la palabra clave `__pin`.  A continuación se muestra un ejemplo ligeramente modificado de la especificación de Extensiones administradas:  
  
```  
__gc struct H { int j; };  
  
int main()   
{  
   H * h = new H;  
   int __pin * k = & h -> j;  
  
   // …  
};  
```  
  
 En el diseño del nuevo lenguaje, un puntero anclado se declara con una sintaxis análoga a la de un puntero interior.  
  
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
  
   // …  
}  
```  
  
 Un puntero anclado en la nueva sintaxis es un caso especial de puntero interior.  Permanecen las restricciones originales para un puntero anclado.  Por ejemplo, no se puede usar como un parámetro o un tipo de devolución de un método; sólo se puede declarar en un objeto local.  Sin embargo, se han agregado una serie de restricciones adicionales en la nueva sintaxis.  
  
 El valor predeterminado de un puntero anclado es `nullptr`, no `0`.  No se puede inicializar `pin_ptr<>` ni asignarle `0`.  Todas las asignaciones de `0` en el código existente deberán cambiarse a `nullptr`.  
  
 En Extensiones administradas se permitía a un puntero anclado direccionar un objeto entero, como en el ejemplo siguiente tomado de la especificación de Extensiones administradas:  
  
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
  
 En la nueva sintaxis, no se permite anclar todo el objeto devuelto por la expresión `new`.  En su lugar, debe anclarse la dirección del miembro interior.  Por ejemplo,  
  
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
  
## Vea también  
 [Tipos de valor y su comportamiento \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)   
 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)   
 [pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md)