---
title: "weak_ptr (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.weak_ptr"
  - "tr1.weak_ptr"
  - "weak_ptr"
  - "tr1::weak_ptr"
  - "std::tr1::weak_ptr"
  - "memory/std::tr1::weak_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "weak_ptr (clase)"
  - "weak_ptr (clase) [TR1]"
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# weak_ptr (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contiene un puntero débilmente vinculado.  
  
## Sintaxis  
  
```  
template<class Ty> class weak_ptr {  
public:  
    typedef Ty element_type;  
  
    weak_ptr();  
    weak_ptr(const weak_ptr&);  
    template<class Other>  
        weak_ptr(const weak_ptr<Other>&);  
    template<class Other>  
        weak_ptr(const shared_ptr<Other>&);  
  
    weak_ptr& operator=(const weak_ptr&);  
    template<class Other>  
        weak_ptr& operator=(const weak_ptr<Other>&);  
    template<class Other>  
        weak_ptr& operator=(shared_ptr<Other>&);  
  
    void swap(weak_ptr&);  
    void reset();  
  
    long use_count() const;  
    bool expired() const;  
    shared_ptr<Ty> lock() const;  
    };  
```  
  
#### Parámetros  
 `Ty`  
 Tipo controlado por el puntero débil.  
  
## Comentarios  
 La clase de plantilla describe un objeto que apunta a un recurso administrado por uno o varios objetos [shared\_ptr \(Clase\)](../standard-library/shared-ptr-class.md).  Los objetos `weak_ptr` que apuntan a un recurso no afectan al recuento de referencias del recurso.  Por lo tanto, cuando se destruye el último objeto `shared_ptr` que administra dicho recurso, este se libera, aunque haya objetos `weak_ptr` apuntando a él.  Esto es esencial para evitar ciclos en estructuras de datos.  
  
 Un objeto `weak_ptr` apunta a un recurso si se construyó a partir de un objeto `shared_ptr` que posee ese recurso, si se construyó a partir de un objeto `weak_ptr` que apunta a ese recurso, o si se le asignó ese recurso con [weak\_ptr::operator\=](../Topic/weak_ptr::operator=.md).  Un objeto `weak_ptr` no proporciona acceso directo al recurso al que apunta.  El código que debe usar el recurso lo hace a través de un objeto `shared_ptr` que posee ese recurso, creado mediante una llamada a la función miembro [weak\_ptr::lock](../Topic/weak_ptr::lock.md).  Un objeto `weak_ptr` expira cuando se libera el recurso al que apunta porque todos los objetos `shared_ptr` que poseen el recurso se han destruido.  Llamar a `lock` en un objeto `weak_ptr` que ha expirado crea un objeto shared\_ptr vacío.  
  
 Un objeto weak\_ptr vacío no apunta a ningún recurso y no tiene ningún bloque de control.  Su función miembro `lock` devuelve un objeto shared\_ptr vacío.  
  
 Un ciclo se produce cuando dos o más recursos controlados por objetos `shared_ptr` contienen objetos `shared_ptr` que se hacen referencia mutuamente.  Por ejemplo, una lista vinculada circular con tres elementos tiene un nodo principal `N0`; ese nodo contiene un objeto `shared_ptr` que posee el siguiente nodo, `N1`; ese nodo contiene un objeto `shared_ptr` que posee el siguiente nodo, `N2`; ese nodo, a su vez, contiene un objeto `shared_ptr` que posee el nodo principal, `N0`, que cierra el ciclo.  En esta situación, ninguno de los recuentos de referencia será cero en ningún momento y no se liberarán los nodos del ciclo.  Para eliminar el ciclo, el último nodo `N2` debe contener un objeto `weak_ptr` que apunte a `N0` en lugar de un objeto `shared_ptr`.  Puesto que el objeto `weak_ptr` no posee `N0`, no afecta al recuento de referencias de `N0`, y cuando se destruya la última referencia al nodo principal del programa, también se destruirán los nodos de la lista.  
  
## Miembros  
  
### Constructores  
  
|||  
|-|-|  
|[weak\_ptr::weak\_ptr](../Topic/weak_ptr::weak_ptr.md)|Construye un objeto `weak_ptr`.|  
  
### Métodos  
  
|||  
|-|-|  
|[weak\_ptr::element\_type](../Topic/weak_ptr::element_type.md)|Tipo del elemento.|  
|[weak\_ptr::expired](../Topic/weak_ptr::expired.md)|Comprueba si la propiedad ha caducado.|  
|[weak\_ptr::lock](../Topic/weak_ptr::lock.md)|Obtiene la propiedad exclusiva de un recurso.|  
|[weak\_ptr::owner\_before](../Topic/weak_ptr::owner_before.md)|Devuelve `true` si este `weak_ptr` está ordenado antes \(o es menor que\) que el puntero proporcionado.|  
|[weak\_ptr::reset](../Topic/weak_ptr::reset.md)|Libera el recurso poseído.|  
|[weak\_ptr::swap](../Topic/weak_ptr::swap.md)|Intercambia dos objetos `weak_ptr`.|  
|[weak\_ptr::use\_count](../Topic/weak_ptr::use_count.md)|Cuenta el número de objetos `shared_ptr` designados.|  
  
### Operadores  
  
|||  
|-|-|  
|[weak\_ptr::operator\=](../Topic/weak_ptr::operator=.md)|Reemplaza el recurso poseído.|  
  
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [shared\_ptr \(Clase\)](../standard-library/shared-ptr-class.md)