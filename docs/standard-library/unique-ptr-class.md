---
title: "unique_ptr (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "unique_ptr"
  - "std.unique_ptr"
  - "std::unique_ptr"
  - "memory/std::unique_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unique_ptr (clase)"
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
caps.latest.revision: 22
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unique_ptr (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Almacena un puntero a un objeto o matriz en propiedad.  El objeto o matriz no es propiedad de ningún otro `unique_ptr`.  El objeto o matriz se destruye cuando `unique_ptr` se destruye.  
  
## Sintaxis  
  
```  
template< class T, class Del = default_delete<T> >  
    class unique_ptr {  
public:  
    unique_ptr( );  
    unique_ptr( nullptr_t Nptr );  
    explicit unique_ptr( pointer Ptr );  
    unique_ptr( pointer Ptr,  
        typename conditional<is_reference<Del>::value,   
            Del,  
            typename add_reference<const Del>::type>::type Deleter);  
    unique_ptr (pointer Ptr,  
        typename remove_reference<Del>::type&& Deleter);  
    unique_ptr (unique_ptr&& Right);  
    template<class T2, Class Del2> unique_ptr( unique_ptr<T2, Del2>&& Right );  
    unique_ptr( const unique_ptr& Right    ) = delete;  
    unique_ptr& operator=(const unique_ptr& Right     ) = delete;  
};  
  
```  
  
```  
//Specialization for arrays:  
template <class T, class D> class unique_ptr<T[], D>   
{   public:       
     typedef pointer;  
     typedef T element_type;  
     typedef D deleter_type;  
  
     constexpr unique_ptr() noexcept;  
     template <class U> explicit unique_ptr(U p) noexcept;  
     template <class U> unique_ptr(U p, see below d) noexcept;  
     template <class U> unique_ptr(U p, see below d) noexcept;  
     unique_ptr(unique_ptr&& u) noexcept;  
     constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }  
     template <class U, class E>  
       unique_ptr(unique_ptr<U, E>&& u) noexcept;  
  
     ~unique_ptr();  
  
     unique_ptr& operator=(unique_ptr&& u) noexcept;  
     template <class U, class E>  
       unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;  
     unique_ptr& operator=(nullptr_t) noexcept;  
  
     T& operator[](size_t i) const;  
     pointer get() const noexcept;  
     deleter_type& get_deleter() noexcept;  
     const deleter_type& get_deleter() const noexcept;  
     explicit operator bool() const noexcept;  
  
     pointer release() noexcept;  
     void reset(pointer p = pointer()) noexcept;  
     void reset(nullptr_t = nullptr) noexcept;  
     template <class U> void reset(U p) noexcept = delete;  
     void swap(unique_ptr& u) noexcept;  
  
    // disable copy from lvalue  
     unique_ptr(const unique_ptr&) = delete;  
     unique_ptr& operator=(const unique_ptr&) = delete;  
   };  
 }  
  
```  
  
#### Parámetros  
 `Right`  
 Objeto `unique_ptr`.  
  
 `Nptr`  
 Interfaz `rvalue` cuyo tipo es `std::nullptr_t`.  
  
 `Ptr`  
 Objeto `pointer`.  
  
 `Deleter`  
 Una función `deleter` enlazada a `unique_ptr`.  
  
## Excepciones  
 `unique_ptr` no produce ninguna excepción.  
  
## Comentarios  
 La clase `unique_ptr` reemplaza a `auto_ptr` y se puede usar como un elemento de los contenedores STL.  
  
 Use la función auxiliar [make\_unique](../Topic/make_unique.md) para crear eficazmente nuevas instancias de `unique_ptr`.  
  
 `unique_ptr` administra de forma única un recurso.  Cada objeto `unique_ptr` almacena un puntero al objeto que posee o almacena un puntero null.  Un recurso no puede pertenecer a más de un objeto `unique_ptr`;  cuando se destruye el objeto `unique_ptr` que posee un recurso concreto, se libera el recurso.  Los objetos `unique_ptr` se pueden mover pero no copiar.  Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 El recurso se libera llamando a un objeto almacenado `deleter` de tipo `Del` que sabe cómo se asignan los recursos de un `unique_ptr` determinado.  El objeto `deleter` predeterminado `default_delete``<T>` supone que el recurso al que apunta `_Ptr` se asigna con `new` y que se puede liberar llamando a `delete _``Ptr`.  \(Una especialización parcial `unique_ptr<T[]>`administra los objetos de matriz asignados con `new[]`, y tiene el `deleter` `default_delete<T[]>` predeterminado, especializado en llamar a delete\[\] `_Ptr`.\)  
  
 El puntero almacenado en un recurso propio, `stored_ptr` tiene el tipo `pointer`.  Es `Del::pointer` si se define y `T *` si no se define.  El objeto almacenado `deleter` `stored_deleter` no ocupa ningún espacio en el objeto si `deleter` no tiene estado.  Observe que `Del` puede ser un tipo de referencia.  
  
## Miembros  
  
### Constructores  
  
|||  
|-|-|  
|[unique\_ptr::unique\_ptr](../Topic/unique_ptr::unique_ptr.md)|Hay siete constructores de `unique_ptr`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[deleter\_type](../Topic/deleter_type.md)|Sinónimo del parámetro de plantilla `Del`.|  
|[element\_type](../Topic/element_type.md)|Sinónimo del parámetro de plantilla `T``.`|  
|[puntero](../Topic/pointer.md)|Sinónimo de `Del::pointer` si se define, si no `T *`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[unique\_ptr::get](../Topic/unique_ptr::get.md)|Devuelve `stored_ptr`.|  
|[unique\_ptr::get\_deleter](../Topic/unique_ptr::get_deleter.md)|Devuelve una referencia a `stored_deleter`.|  
|[unique\_ptr::release](../Topic/unique_ptr::release.md)|Almacena `pointer()` en `stored_ptr` y devuelve su contenido anterior.|  
|[unique\_ptr::reset](../Topic/unique_ptr::reset.md)|Libera el recurso actualmente en propiedad y acepta un nuevo recurso.|  
|[unique\_ptr::swap](../Topic/unique_ptr::swap.md)|Intercambia el recurso y `deleter` con el `unique_ptr` proporcionado.|  
  
### Operadores  
  
|||  
|-|-|  
|`operator bool`|El operador devuelve un valor de un tipo que pueda convertirse en `bool`.  El resultado de la conversión en `bool` es `true` cuando `get() != pointer()`, si no `false`.|  
|`operator->`|La función miembro devuelve `stored_ptr``.`|  
|`operator*`|La función miembro devuelve\*`stored_ptr``.`|  
|[unique\_ptr operator\=](../Topic/unique_ptr%20operator=.md)|Asigna el valor de `unique_ptr` \(o un `pointer-type`\) al `unique_ptr` actual.|  
  
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<memory\>](../standard-library/memory.md)