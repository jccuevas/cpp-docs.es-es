---
title: "function (Clase) | Microsoft Docs"
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
  - "functional/std::tr1::function"
  - "std.tr1.function"
  - "std::tr1::function"
  - "function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "function (clase) [TR1]"
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
caps.latest.revision: 26
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# function (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contenedor para un objeto accesible.  
  
## Sintaxis  
  
```cpp  
template<class Fty>  
   class function  // Fty of type Ret(T1, T2, ..., TN)  
   : public unary_function<T1, Ret>       // when Fty is Ret(T1)  
   : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)  
   {  
public:  
   typedef Ret result_type;  
  
   function();  
   function(nullptr_t);  
   function(const function& _Right);  
   template<class Fty2>  
      function(Fty2 fn);  
   template<class Fty2, class Alloc>  
       function (reference_wrapper<Fty2>, const Alloc& _Ax);  
   template<class Fty2, class Alloc>  
       void assign (Fty2, const Alloc& _Ax);  
   template<class Fty2, class Alloc>  
       assign (reference_wrapper<Fty2>, const Alloc& _Ax);  
```  
  
```cpp  
function& operator=(nullptr_t);  
function& operator=(const function&);  
template<class Fty2>  
   function& operator=(Fty2);  
template<class Fty2>  
   function& operator=(reference_wrapper<Fty2>);  
void swap(function&);  
  
explicit operator bool() const;  
result_type operator()(T1, T2, ....., TN) const;  
  
const std::type_info& target_type() const;  
template<class Fty2>  
   Fty2 *target();  
template<class Fty2>  
   const Fty2 *target() const;  
```  
  
```cpp  
   template<class Fty2>  
      void operator==(const Fty2&) const = delete;  
   template<class Fty2>  
      void operator!=(const Fty2&) const = delete;  
};  
```  
  
#### Parámetros  
 `Fty`  
 El tipo de función a ajustar.  
  
 `_Ax`  
 La función de asignador.  
  
## Comentarios  
 La clase de plantilla es un contenedor de llamada cuya firma de llamada es `Ret(T1, T2, ..., TN)`.  Se utiliza para agregar diversos objetos accesibles en un contenedor uniforme.  
  
 Algunas funciones miembro toman un operando que los nombres el objeto deseado de destino.  Puede especificar un operando de varias maneras:  
  
 `fn` \-\- el objeto accesible `fn`; después de la llamada al objeto de `function` contiene una copia de `fn`  
  
 `fnref` \-\- el objeto accesible denominado por `fnref.get()`; después de la llamada al objeto de `function` contiene una referencia a `fnref.get()`  
  
 `right` \-\- el objeto accesible, si existe, almacenado por el objeto `right`de `function`  
  
 `npc` \-\- un puntero NULL; después de la llamada al objeto de `function` está vacío  
  
 En todos los casos, `INVOKE(f, t1, t2, ..., tN)`, donde es el objeto `f` accesible y `t1, t2, ..., tN` es son de los tipos `T1, T2, ..., TN` respectivamente, debe ser correcto y, si `Ret` no está vacío, convertible a `Ret`.  
  
 Un objeto vacío de `function` no contiene un objeto accesible o una referencia a un objeto accesible.  
  
### Constructores  
  
|||  
|-|-|  
|[function::function](../Topic/function::function.md)|Construye un contenedor que está vacío o almacena un objeto accesible de tipo arbitrario con una firma fija.|  
  
### Typedefs  
  
|||  
|-|-|  
|[function::result\_type](../Topic/function::result_type.md)|El del objeto accesible almacenado.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[function::assign](../Topic/function::assign.md)|Asigna un objeto accesible a este objeto de función.|  
|[function::swap](../Topic/function::swap.md)|Intercambio dos objetos accesibles.|  
|[function::target](../Topic/function::target.md)|Comprueba si el objeto accesible almacenado es accesible especificadas.|  
|[function::target\_type](../Topic/function::target_type.md)|Obtiene la información de tipo del objeto accesible.|  
  
### Operadores  
  
|||  
|-|-|  
|[function::operator unspecified](../Topic/function::operator%20unspecified.md)|Comprueba si existe el objeto accesible almacenado.|  
|[function::operator\(\)](../Topic/function::operator\(\).md)|Llama a un objeto accesible.|  
|[function::operator\=](../Topic/function::operator=.md)|Reemplaza el objeto accesible almacenado.|  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [mem\_fn \(Función\)](../Topic/mem_fn%20Function.md)   
 [reference\_wrapper \(Clase\)](../standard-library/reference-wrapper-class.md)