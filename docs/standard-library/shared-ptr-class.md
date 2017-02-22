---
title: "shared_ptr (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "shared_ptr"
  - "tr1::shared_ptr"
  - "memory/std::tr1::shared_ptr"
  - "std::tr1::shared_ptr"
  - "std.tr1.shared_ptr"
  - "tr1.shared_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shared_ptr (clase)"
  - "shared_ptr (clase) [TR1]"
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# shared_ptr (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Encapsula un puntero inteligente en el que se cuentan las referencias alrededor de un objeto asignado dinámicamente.  
  
## Sintaxis  
  
```  
template<class Ty>  
   class shared_ptr {  
public:  
    typedef Ty element_type;  
  
    shared_ptr();  
    shared_ptr(nullptr_t);   
    shared_ptr(const shared_ptr& sp);  
    shared_ptr(shared_ptr&& sp);  
    template<class Other>  
        explicit shared_ptr(Other * ptr);  
    template<class Other, class D>  
        shared_ptr(Other * ptr, D dtor);  
    template<class D>  
        shared_ptr(nullptr_t, D dtor);  
    template<class Other, class D, class A>  
        shared_ptr(Other *ptr, D dtor, A alloc);  
    template<class D, class A>  
        shared_ptr(nullptr_t, D dtor, A alloc);  
    template<class Other>  
        shared_ptr(const shared_ptr<Other>& sp);  
    template<class Other>  
        shared_ptr(const shared_ptr<Other>&& sp);  
    template<class Other>  
        explicit shared_ptr(const weak_ptr<Other>& wp);  
    template<class Other>  
        shared_ptr(auto_ptr<Other>& ap);  
    template<class Other, class D>  
        shared_ptr(unique_ptr<Other, D>&& up);  
    template<class Other>  
        shared_ptr(const shared_ptr<Other>& sp, Ty *ptr);  
    ~shared_ptr();  
    shared_ptr& operator=(const shared_ptr& sp);  
    template<class Other>   
        shared_ptr& operator=(const shared_ptr<Other>& sp);  
    shared_ptr& operator=(shared_ptr&& sp);  
    template<class Other>   
        shared_ptr& operator=(shared_ptr<Other>&& sp);  
    template<class Other>   
        shared_ptr& operator=(auto_ptr< Other >&& ap);  
    template <class Other, class D>   
        shared_ptr& operator=(const unique_ptr< Other, D>& up) = delete;  
    template <class Other, class D>  
        shared_ptr& operator=(unique_ptr<Other, D>&& up);  
    void swap(shared_ptr& sp);  
    void reset();  
    template<class Other>  
        void reset(Other *ptr);  
    template<class Other, class D>  
        void reset(Other *ptr, D dtor);  
    template<class Other, class D, class A>  
        void reset(Other *ptr, D dtor, A alloc);  
    Ty *get() const;  
    Ty& operator*() const;  
    Ty *operator->() const;  
    long use_count() const;  
    bool unique() const;  
    operator bool() const;  
  
    template<class Other>  
        bool owner_before(shared_ptr<Other> const& ptr) const;  
    template<class Other>  
        bool owner_before(weak_ptr<Other> const& ptr) const;  
    template<class D, class Ty>   
        D* get_deleter(shared_ptr<Ty> const& ptr);  
};  
  
```  
  
#### Parámetros  
 `Ty`  
 Tipo controlado por el puntero compartido.  
  
 `Other`  
 Tipo controlado por el puntero de argumento.  
  
 `ptr`  
 Puntero que se va a copiar.  
  
 `D`  
 Tipo del eliminador.  
  
 `A`  
 Tipo del asignador.  
  
 `dtor`  
 Eliminador.  
  
 `alloc`  
 Asignador.  
  
 `sp`  
 Puntero inteligente que se va a copiar o mover.  
  
 `wp`  
 Puntero débil que se va a copiar o mover.  
  
 `ap`  
 Puntero automático que se va a copiar o mover.  
  
 `up`  
 Puntero único que se va a mover.  
  
## Comentarios  
 La clase de plantilla describe un objeto que utiliza el recuento de referencias para administrar recursos.  Un objeto `shared_ptr` contiene eficazmente un puntero al recurso que posee o contiene un puntero null.  Un recurso puede ser propiedad de más de un objeto `shared_ptr`; cuando se destruye el último objeto `shared_ptr` que posee un recurso determinado, se libera el recurso.  
  
 Un `shared_ptr` deja de ser el propietario de un recurso cuando se reasigna o se restablece.  
  
 El argumento de plantilla `Ty` puede ser un tipo incompleto, salvo lo indicado para ciertas funciones miembro.  
  
 Cuando se construye un objeto `shared_ptr<Ty>` desde un puntero de recursos de tipo `G*` o desde un `shared_ptr<G>`, el tipo de puntero `G*` debe poder convertirse a `Ty*`.  Si no es así, el código no se compilará.  Por ejemplo:  
  
```cpp  
class F {};  
class G : public F {};  
```  
  
```cpp  
  
#include <memory>  
  
using namespace std;  
  
shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*  
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>  
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*  
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>  
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>  
shared_ptr<int> sp5(new G); // error, G* not convertible to int*  
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>  
```  
  
 Un objeto `shared_ptr` posee un recurso:  
  
-   si se construyó con un puntero a ese recurso,  
  
-   si se construyó desde un objeto `shared_ptr` que posee ese recurso,  
  
-   si se construyó desde un objeto [weak\_ptr \(Clase\)](../standard-library/weak-ptr-class.md) que apunta a ese recurso, o  
  
-   si se le asignó la propiedad de ese recurso, ya sea con [shared\_ptr::operator\=](../Topic/shared_ptr::operator=.md) o llamando a la función miembro [shared\_ptr::reset](../Topic/shared_ptr::reset.md).  
  
 Los objetos `shared_ptr` que poseen un recurso comparten un bloque de control.  El bloque de control contiene:  
  
-   el número de objetos `shared_ptr` que poseen el recurso,  
  
-   el número de objetos `weak_ptr` que apuntan al recurso,  
  
-   el eliminador para ese recurso, si existe,  
  
-   el asignador personalizado para el bloque de control, si tiene alguno.  
  
 Un objeto `shared_ptr` que se inicializa mediante un puntero NULL tiene un bloque de control y no está vacío.  Después de que un objeto `shared_ptr` libera un recurso, ya no posee ese recurso.  Después de que un objeto `weak_ptr` libera un recurso, ya no apunta a ese recurso.  
  
 Cuando el número de objetos `shared_ptr` que poseen un recurso es cero, el recurso se libera eliminándolo o pasando su dirección a un eliminador, según cómo se creara originalmente la propiedad del recurso.  Cuando el número de objetos `shared_ptr` que poseen un recurso es cero, y el número de objetos `weak_ptr` que apuntan a ese recurso es cero, el bloque de control se libera, utilizando el asignador personalizado para el bloque de control si tiene alguno.  
  
 Un objeto `shared_ptr` vacío no posee ningún recurso y no tiene ningún bloque de control.  
  
 Un eliminador es un objeto de función que tiene una función miembro `operator()`.  Su tipo se debe poder construir mediante copia, y su constructor y destructor de copias no deben producir excepciones.  Acepta un parámetro: el objeto que se va a eliminar.  
  
 Algunas funciones toman una lista de argumentos que define propiedades del objeto `shared_ptr<Ty>` o `weak_ptr<Ty>` resultante.  Hay varias maneras de especificar esta lista de argumentos:  
  
 sin argumentos: el objeto resultante es un objeto `shared_ptr` o `weak_ptr` vacío.  
  
 `ptr`: puntero de tipo `Other*` al recurso que se va a administrar.  `Ty` debe ser un tipo completo.  Si se produce un error en la función \(porque no se puede asignar el bloque de control\), evalúa la expresión `delete ptr`.  
  
 `ptr, dtor`: puntero de tipo `Other*` al recurso que se va a administrar y un eliminador para ese recurso.  Si se produce un error en la función \(porque no se puede asignar el bloque de control\), llama a `dtor(ptr)`, que deben estar bien definido.  
  
 `ptr, dtor, alloc`: puntero de tipo `Other*` al recurso que se va a administrar, un eliminador para ese recurso y un asignador para administrar cualquier almacenamiento que se deba asignar y liberar.  Si se produce un error en la función \(porque no se puede asignar el bloque de control\), llama a `dtor(ptr)`, que deben estar bien definido.  
  
 `sp`: objeto `shared_ptr<Other>` que posee el recurso que se va a administrar.  
  
 `wp`: objeto `weak_ptr<Other>` que apunta al recurso que se va a administrar.  
  
 `ap`: objeto `auto_ptr<Other>` que contiene un puntero al recurso que se va a administrar.  Si la función se ejecuta correctamente, llama a `ap.release()`; de lo contrario, deja `ap` sin modificar.  
  
 En todos los casos, el tipo de puntero `Other*` debe poder convertirse a `Ty*`.  
  
## Seguridad para subprocesos  
 Varios subprocesos pueden leer y escribir diferentes objetos `shared_ptr` al mismo tiempo, incluso cuando los objetos son copias que comparten la propiedad.  
  
## Miembros  
  
### Constructores  
  
|||  
|-|-|  
|[shared\_ptr::shared\_ptr](../Topic/shared_ptr::shared_ptr.md)|Construye un objeto `shared_ptr`.|  
|[shared\_ptr::~shared\_ptr](../Topic/shared_ptr::~shared_ptr.md)|Destruye un objeto `shared_ptr`.|  
  
### Métodos  
  
|||  
|-|-|  
|[shared\_ptr::element\_type](../Topic/shared_ptr::element_type.md)|El tipo de un elemento.|  
|[shared\_ptr::get](../Topic/shared_ptr::get.md)|Obtiene la dirección del recurso propio.|  
|[shared\_ptr::owner\_before](../Topic/shared_ptr::owner_before.md)|Devuelve true si este `shared_ptr` está ordenado antes \(o es menor que\) que el puntero proporcionado.|  
|[shared\_ptr::reset](../Topic/shared_ptr::reset.md)|Reemplaza el recurso propio.|  
|[shared\_ptr::swap](../Topic/shared_ptr::swap.md)|Intercambia dos objetos `shared_ptr`.|  
|[shared\_ptr::unique](../Topic/shared_ptr::unique.md)|Comprueba si el recurso propio es único.|  
|[shared\_ptr::use\_count](../Topic/shared_ptr::use_count.md)|Cuenta los números de propietarios del recurso.|  
  
### Operadores  
  
|||  
|-|-|  
|[shared\_ptr::operator boolean\-type](../Topic/shared_ptr::operator%20boolean-type.md)|Comprueba si existe un recurso propio.|  
|[shared\_ptr::operator\*](../Topic/shared_ptr::operator*.md)|Obtiene el valor designado.|  
|[shared\_ptr::operator\=](../Topic/shared_ptr::operator=.md)|Reemplaza el recurso propio.|  
|[shared\_ptr::operator\-\>](../Topic/shared_ptr::operator-%3E.md)|Obtiene un puntero al valor designado.|  
  
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [weak\_ptr \(Clase\)](../standard-library/weak-ptr-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)