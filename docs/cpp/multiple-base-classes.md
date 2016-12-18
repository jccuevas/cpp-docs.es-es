---
title: "Varias clases base | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases base, múltiple"
  - "clases derivadas, bases múltiples"
  - "varias clases base"
  - "herencia múltiple, declaración de clase"
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Varias clases base
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como se describe en [Herencia múltiple](http://msdn.microsoft.com/es-es/3b74185e-2beb-4e29-8684-441e51d2a2ca), una clase se puede derivar de más de una clase base.  En un modelo de herencia múltiple \(en que las clases se derivan de más de una clase base\), las clases base se especifican utilizando el elemento de gramática *base\-list* \(vea la sección Gramática de [Información general](../misc/overview-of-derived-classes.md)\).  Por ejemplo, se puede especificar la declaración de clase para `CollectionOfBook`, derivada de `Collection` y `Book`:  
  
```  
// deriv_MultipleBaseClasses.cpp  
// compile with: /LD  
class Collection {  
};  
class Book {};  
class CollectionOfBook : public Book, public Collection {  
    // New members  
};  
```  
  
 El orden en que se especifican las clases base no es significativo salvo en algunos casos en que se invocan constructores y destructores.  En estos casos, el orden en que se especifican las clases base afecta a lo siguiente:  
  
-   El orden en que tiene lugar la inicialización mediante constructor.  Si el código se basa en la parte `Book` de `CollectionOfBook` que se va inicializar antes que la parte `Collection`, el orden de especificación es significativo.  La inicialización tiene lugar en el orden en que se especifican las clases en el elemento *base\-list*.  
  
-   El orden en que los destructores se invocan para la limpieza.  De nuevo, si una "parte concreta" de la clase debe estar presente cuando se está destruyendo la otra parte, el orden es significativo.  Los destructores se invocan en orden inverso al de las clases especificadas en *base\-list*.  
  
    > [!NOTE]
    >  El orden de especificación de clases base puede afectar al diseño de memoria de la clase.  No se deben tomar decisiones de programación basadas en el orden de los miembros base en la memoria.  
  
 Al especificar el elemento *base\-list*, no se puede especificar el mismo nombre de clase más de una vez.  Sin embargo, es posible que una clase sea una base indirecta a una clase derivada más de una vez.  
  
## Clases base virtuales  
 Dado que una clase puede ser una clase base indirecta de una clase derivada más de una vez, C\+\+ proporciona una manera de optimizar el funcionamiento de esas clases base.  Las clases base virtuales proporcionan una manera de ahorrar espacio y evitar la ambigüedad en las jerarquías de clases que usan la herencia múltiple.  
  
 Cada objeto no virtual contiene una copia de los miembros de datos definidos en la clase base.  Esta duplicación desperdicia espacio y requiere especificar qué copia de los miembros de la clase base se desea siempre que se accede a ellos.  
  
 Cuando una clase base se especifica como base virtual, puede actuar como base indirecta más de una vez sin la duplicación de sus miembros de datos.  Todas las clases base que utilizan una clase base como base virtual comparten una única copia de sus miembros de datos.  
  
 Al declarar una clase base virtual, la palabra clave de **virtual** aparece en las listas base de las clases derivadas.  
  
 Considere la jerarquía de clases de la ilustración siguiente, que muestra un gráfico Lunch\-Line simulado.  
  
 ![Gráfico de línea de comida simulada](../cpp/media/vc38xp1.png "vc38XP1")  
Gráfico de línea de comida simulada  
  
 En la ilustración, `Queue` es la clase base de `CashierQueue` y `LunchQueue`.  Sin embargo, cuando ambas clases se combinan para formar `LunchCashierQueue`, surge el siguiente problema: la nueva clase contiene dos subobjetos de tipo `Queue`, uno de `CashierQueue` y otro de `LunchQueue`.  La ilustración siguiente muestra el diseño de memoria conceptual \(el diseño de memoria real se podría optimizar\).  
  
 ![Objeto de línea de comida simulada](../cpp/media/vc38xp2.png "vc38XP2")  
Objeto de línea de comida simulada  
  
 Observe que hay dos subobjetos `Queue` en el objeto `LunchCashierQueue`.  El código siguiente declara `Queue` como clase base virtual:  
  
```  
// deriv_VirtualBaseClasses.cpp  
// compile with: /LD  
class Queue {};  
class CashierQueue : virtual public Queue {};  
class LunchQueue : virtual public Queue {};  
class LunchCashierQueue : public LunchQueue, public CashierQueue {};  
```  
  
 La palabra clave `virtual` garantiza que solo se incluye una copia del subobjeto `Queue` \(consulte la ilustración siguiente\).  
  
 ![Objeto de línea de comida simulada, clases base virtuales](../cpp/media/vc38xp3.png "vc38XP3")  
Objeto de línea de comida simulada con clases base virtuales  
  
 Una clase puede tener un componente virtual y un componente no virtual de un tipo determinado.  Esto sucede en las condiciones que se muestran en la siguiente ilustración.  
  
 ![Componentes virtuales y no virtuales de una clase](../cpp/media/vc38xp4.png "vc38XP4")  
Componente virtuales y no virtuales de la misma clase  
  
 En la ilustración, `CashierQueue` y `LunchQueue` usan `Queue` como clase base virtual.  Sin embargo, `TakeoutQueue` especifica `Queue` como clase base, no como una clase base virtual.  Por consiguiente, `LunchTakeoutCashierQueue` tiene dos subobjetos de tipo `Queue`: uno en la ruta de herencia que incluye `LunchCashierQueue` y otro en la ruta que incluye `TakeoutQueue`.  Esto se muestra en la ilustración siguiente.  
  
 ![Herencia virtual y no virtual en el diseño de objeto](../cpp/media/vc38xp5.png "vc38XP5")  
Diseño de objeto con herencia virtual y no virtual  
  
> [!NOTE]
>  La herencia virtual supone una importante ventaja con respecto al tamaño si se compara con la herencia no virtual.  Sin embargo, puede agregar una sobrecarga de procesamiento.  
  
 Si una clase derivada reemplaza una función virtual que hereda de una clase base virtual y si un constructor o destructor para la clase derivada llama a esa función con un puntero a la clase base virtual, el compilador puede incluir campos "vtordisp" ocultos adicionales en clases con bases virtuales.  La opción del compilador \/vd0 suprime la adición del miembro oculto de desplazamiento del constructor\/destructor de vtordisp.  La opción del compilador \/vd1, la predeterminada, los habilita cuando es necesario.  Desactive los vtordisp solo si está seguro de que todos los constructores y destructores de clase llaman a funciones virtuales virtualmente.  
  
 La opción del compilador \/vd afecta a un módulo de compilación completo.  Utilice la directiva pragma de **vtordisp** para suprimir y después volver a habilitar los campos de vtordisp clase por clase:  
  
```  
#pragma vtordisp( off )  
class GetReal : virtual public { ... };  
#pragma vtordisp( on )  
```  
  
## Ambigüedades en nombres  
 La herencia múltiple introduce la posibilidad de que los nombres se hereden a lo largo de más de una ruta.  Los nombres de miembros de clase a lo largo de estas rutas no son necesariamente exclusivos.  Estos conflictos de nombre se denominan "ambigüedades".  
  
 Cualquier expresión que haga referencia a un miembro de clase debe producir una referencia ambigua.  En el ejemplo siguiente se muestra cómo se desarrollan las ambigüedades:  
  
```  
// deriv_NameAmbiguities.cpp  
// compile with: /LD  
// Declare two base classes, A and B.  
class A {  
public:  
    unsigned a;  
    unsigned b();  
};  
  
class B {  
public:  
    unsigned a();  // Note that class A also has a member "a"  
    int b();       //  and a member "b".  
    char c;  
};  
  
// Define class C as derived from A and B.  
class C : public A, public B {};  
```  
  
 Dadas las declaraciones de clase anteriores, un código como el siguiente es ambiguo porque no está claro si `b` hace referencia a `b` en `A` o en `B`:  
  
```  
C *pc = new C;  
  
pc->b();  
```  
  
 Considere el ejemplo anterior.  Dado que el nombre `a` es miembro de la clase `A` y la clase `B`, el compilador no puede discernir qué `a` designa la función que se va a invocar.  El acceso a un miembro es ambiguo si puede hacer referencia a más de una función, objeto, tipo o enumerador.  
  
 El compilador detecta las ambigüedades realizando pruebas en este orden:  
  
1.  Si el acceso al nombre es ambiguo \(como se acaba de describir\), se genera un mensaje de error.  
  
2.  Si las funciones sobrecargadas no son ambiguas, se resuelven.  \(Para obtener más información sobre la ambigüedad de sobrecarga de funciones, vea [Coincidencia de argumentos](../misc/argument-matching.md)\).  
  
3.  Si el acceso al nombre infringe el permiso de acceso a miembros, se genera un mensaje de error.  \(Para obtener más información, vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md)\).  
  
 Cuando una expresión produce una ambigüedad en la herencia, la puede resolver manualmente calificando el nombre en cuestión con su nombre de clase.  Para que la compilación del ejemplo anterior se realice correctamente sin ambigüedades, utilice código como el siguiente:  
  
```  
C *pc = new C;  
  
pc->B::a();  
```  
  
> [!NOTE]
>  Cuando se declara `C`, tiene la posibilidad de producir errores cuando se hace referencia a `B` en el ámbito de `C`.  Sin embargo, no se emite ningún error hasta se realice realmente una referencia no calificada a `B` en el ámbito de `C`.  
  
### Dominación  
 Es posible que se llegue a varios nombres \(función, objeto o enumerador\) a través de un gráfico de herencia.  Estos casos se consideran ambiguos con las clases base no virtuales.  También son ambiguos con las clases base virtuales, a menos que uno de los nombres “domine” a los otros.  
  
 Un nombre domina a otro nombre si está definido en ambas clases y una clase se deriva de la otra.  El nombre dominante es el nombre de la clase derivada; este nombre se utiliza cuando podría producirse una ambigüedad, como se muestra en el ejemplo siguiente:  
  
```  
// deriv_Dominance.cpp  
// compile with: /LD  
class A {  
public:  
    int a;  
};  
  
class B : public virtual A {  
public:  
    int a();  
};  
  
class C : public virtual A {};  
  
class D : public B, public C {  
public:  
    D() { a(); } // Not ambiguous. B::a() dominates A::a.  
};  
```  
  
### Conversiones ambiguas  
 Las conversiones explícitas e implícitas de punteros o referencias a los tipos de clase pueden producir ambigüedades.  En la ilustración siguiente, Conversión ambigua de punteros a clases base, se muestra lo siguiente:  
  
-   La declaración de un objeto de tipo `D`.  
  
-   El efecto de aplicar el operador address\-of \(**&**\) a ese objeto.  Observe que el operador address\-of siempre proporciona la dirección base del objeto.  
  
-   El efecto de convertir explícitamente el puntero obtenido mediante el operador address\-of al tipo de clase base `A`.  Observe que forzar la dirección del objeto al tipo `A*` no siempre proporciona al compilador la información suficiente para determinar qué objeto secundario de tipo `A` debe seleccionar; en este caso, existen dos objetos secundarios.  
  
 ![Conversión ambigua de punteros a clases base](../cpp/media/vc38xt1.png "vc38XT1")  
Conversión ambigua de punteros a clases base  
  
 La conversión al tipo `A*` \(puntero a `A`\) es ambigua porque no hay ninguna manera de discernir qué objeto secundario de tipo `A` es el correcto.  Observe que puede evitar la ambigüedad si especifica explícitamente el objeto secundario que quiere utilizar, como sigue:  
  
```  
(A *)(B *)&d       // Use B subobject.  
(A *)(C *)&d       // Use C subobject.  
```  
  
### Ambigüedades y clases base virtuales  
 Si se utilizan clases base virtuales, se puede tener acceso a las funciones, objetos, tipos y enumeradores a través de rutas de herencia múltiple.  Como solo hay una instancia de la clase base, no se produce ambigüedad a la hora de acceder a estos nombres.  
  
 En la ilustración siguiente se muestra cómo se componen los objetos mediante herencia virtual y no virtual.  
  
 ![Derivación virtual y no virtual](../cpp/media/vc38xr1.png "vc38XR1")  
Derivación virtual frente ano virtual  
  
 En la ilustración, el acceso a cualquier miembro de la clase `A` a través de clases base no virtuales produce ambigüedad; el compilador no tiene información que explique si se debe usar el subobjeto asociado a `B` o el subobjeto asociado a `C`.  Sin embargo, cuando se especifica `A` como una clase base virtual, no hay dudas acerca de a qué subobjeto se está accediendo.  
  
## Vea también  
 [Herencia](../cpp/inheritance-cpp.md)