---
title: "auto_ptr (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::auto_ptr"
  - "std.auto_ptr"
  - "auto_ptr"
  - "memory/std::auto_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_ptr (clase)"
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# auto_ptr (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Encapsula un puntero inteligente en torno a un recurso que garantiza que el recurso se destruye automáticamente cuando el control abandona un bloque.  
  
 La clase `unique_ptr` de mayor capacidad reemplaza a `auto_ptr`.  Para obtener más información, consulte [unique\_ptr \(Clase\)](../standard-library/unique-ptr-class.md).  
  
 Para obtener más información sobre `throw()` y el control de excepciones, consulte [Especificaciones de excepciones \(throw\)](../cpp/exception-specifications-throw-cpp.md).  
  
## Sintaxis  
  
```  
template<class Type>  
    class auto_ptr {  
public:  
    typedef Type element_type;  
    explicit auto_ptr(Type *_Ptr = 0) throw();  
    auto_ptr(auto_ptr<Type>& _Right) throw();  
    template<class Other>  
        operator auto_ptr<Other>() throw();  
    template<class Other>  
        auto_ptr<Type>& operator=(auto_ptr<Other>& _Right) throw();  
    template<class Other>  
        auto_ptr(auto_ptr<Other>& _Right);  
    auto_ptr<Type>& operator=(auto_ptr<Type>& _Right);  
    ~auto_ptr();  
    Type& operator*() const throw();  
    Type *operator->()const throw();  
    Type *get() const throw();  
    Type *release()throw();  
    void reset(Type *_Ptr = 0);  
};  
```  
  
#### Parámetros  
 `_Right`  
 `auto_ptr` desde el que se va a obtener un recurso existente.  
  
 `_Ptr`  
 Puntero especificado para reemplazar el puntero almacenado.  
  
## Comentarios  
 La clase de plantilla describe un puntero inteligente, llamado `auto_ptr,` en un objeto asignado.  El puntero debe ser nulo o designar un objeto asignado por `new`.  `auto_ptr` transfiere la propiedad si su valor almacenado se asigna a otro objeto.  \(Reemplaza el valor almacenado después de una transferencia con un puntero nulo\). El destructor de `auto_ptr<Type>` elimina el objeto asignado.  `auto_ptr<Type>` garantiza que un objeto asignado se elimina automáticamente cuando el control abandona un bloque, incluso a través de una excepción producida.  No debe construir dos objetos `auto_ptr<Type>` que posean el mismo objeto.  
  
 Puede pasar un objeto `auto_ptr<Type>` por valor como argumento a una llamada de función.  `auto_ptr` no puede ser un elemento de ningún contenedor de la biblioteca estándar.  No puede administrar de manera fiable una secuencia de objetos `auto_ptr<Type>` con un contenedor de la biblioteca de plantillas estándar.  
  
## Miembros  
  
### Constructores  
  
|||  
|-|-|  
|[auto\_ptr](../Topic/auto_ptr::auto_ptr.md)|Constructor para los objetos de tipo `auto_ptr`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[element\_type](../Topic/auto_ptr::element_type.md)|El tipo es un sinónimo del parámetro de plantilla `Type`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[obtener](../Topic/auto_ptr::get.md)|La función miembro devuelve el puntero `myptr` almacenado.|  
|[versión](../Topic/auto_ptr::release.md)|El miembro reemplaza el puntero `myptr` almacenado con un puntero nulo y devuelve el puntero almacenado previamente.|  
|[restablecer](../Topic/auto_ptr::reset.md)|La función miembro evalúa la expresión `delete myptr`, pero solo si el valor de puntero `myptr` almacenado cambia como consecuencia de la llamada de función.  A continuación, reemplaza el puntero almacenado con `ptr`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/auto_ptr::operator=.md)|Operador de asignación que transfiere la propiedad de un objeto `auto_ptr` a otro.|  
|[operator\*](../Topic/auto_ptr::operator*.md)|Operador de desreferenciación para objetos de tipo `auto_ptr`.|  
|[operator\-\>](../Topic/auto_ptr::operator-%3E.md)|Operador para permitir el acceso a miembros.|  
|[operador auto\_ptr\<Other\>](../Topic/auto_ptr::operator%20auto_ptr%3COther%3E.md)|Convierte de un tipo de `auto_ptr` a otro tipo de `auto_ptr`.|  
|[operador auto\_ptr\_ref\<Other\>](../Topic/auto_ptr::operator%20auto_ptr_ref%3COther%3E.md)|Convierte de `auto_ptr` a `auto_ptr_ref`.|  
  
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [unique\_ptr \(Clase\)](../standard-library/unique-ptr-class.md)