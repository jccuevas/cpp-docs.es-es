---
title: scoped_allocator_adaptor (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.scoped_allocator_adaptor
- scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor
dev_langs:
- C++
helpviewer_keywords:
- scoped_allocator_adaptor Class
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: f4c343592c2c767d52a66091ecca5b1bd4ae9e88
ms.lasthandoff: 02/24/2017

---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor (clase)
Representa una anidación de asignadores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <class Outer, class... Inner>  
class scoped_allocator_adaptor;  
```  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla encapsula una anidación de uno o más asignadores. Cada clase tiene un asignador exterior de tipo `outer_allocator_type`, un sinónimo de `Outer`, que es una base pública del objeto `scoped_allocator_adaptor`. `Outer` se usa para asignar la memoria que va a usar un contenedor. Puede obtener una referencia a este objeto base de asignador mediante una llamada a `outer_allocator`.  
  
 El resto de la anidación tiene el tipo `inner_allocator_type`. Un asignador interno se usa para asignar memoria para los elementos dentro de un contenedor. Puede obtener una referencia al objeto almacenado de este tipo mediante una llamada a `inner_allocator`. Si `Inner...` no está vacío, `inner_allocator_type` tiene el tipo `scoped_allocator_adaptor<Inner...>` y `inner_allocator` designa un objeto miembro. De lo contrario, `inner_allocator_type` tiene el tipo `scoped_allocator_adaptor<Outer>` y `inner_allocator` designa el objeto completo.  
  
 La anidación se comporta como si tuviera una profundidad arbitraria, y replica su asignador interior encapsulado según sea necesario.  
  
 Varios conceptos que no forman parte de la interfaz visible ayudan a describir el comportamiento de esta clase de plantilla. Un *asignador exterior* media en todas las llamadas a los métodos de construcción y destrucción. Se define eficazmente mediante la función recursiva `OUTERMOST(X)`, donde `OUTERMOST(X)` es uno de los siguientes.  
  
-   Si `X.outer_allocator()` está bien formado, entonces `OUTERMOST(X)` es `OUTERMOST(X.outer_allocator())`.  
  
-   En caso contrario, `OUTERMOST(X)` es `X`.  
  
 Como ejemplo, se definen tres tipos:  
  
|Tipo|Descripción|  
|----------|-----------------|  
|`Outermost`|Tipo de `OUTERMOST(*this)`.|  
|`Outermost_traits`|`allocator_traits<Outermost>`|  
|`Outer_traits`|`allocator_traits<Outer>`|  
  
### <a name="constructors"></a>Constructores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[scoped_allocator_adaptor::scoped_allocator_adaptor (Constructor)](#scoped_allocator_adaptor__scoped_allocator_adaptor_constructor)|Construye un objeto `scoped_allocator_adaptor`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|Name|Descripción|  
|----------|-----------------|  
|`const_pointer`|Este tipo es un sinónimo del `const_pointer` que está asociado con el asignador `Outer`.|  
|`const_void_pointer`|Este tipo es un sinónimo del `const_void_pointer` que está asociado con el asignador `Outer`.|  
|`difference_type`|Este tipo es un sinónimo del `difference_type` que está asociado con el asignador `Outer`.|  
|`inner_allocator_type`|Este tipo es un sinónimo del tipo del adaptador anidado `scoped_allocator_adaptor<Inner...>`.|  
|`outer_allocator_type`|Este tipo es un sinónimo del tipo del asignador base `Outer`.|  
|`pointer`|Este tipo es un sinónimo del `pointer` asociado con el asignador `Outer`.|  
|`propagate_on_container_copy_assignment`|El tipo es verdadero solo si `Outer_traits::propagate_on_container_copy_assignment` es verdadero o `inner_allocator_type::propagate_on_container_copy_assignment` es verdadero.|  
|`propagate_on_container_move_assignment`|El tipo es verdadero solo si `Outer_traits::propagate_on_container_move_assignment` es verdadero o `inner_allocator_type::propagate_on_container_move_assignment` es verdadero.|  
|`propagate_on_container_swap`|El tipo es verdadero solo si `Outer_traits::propagate_on_container_swap` es verdadero o `inner_allocator_type::propagate_on_container_swap` es verdadero.|  
|`size_type`|Este tipo es un sinónimo del `size_type` asociado con el asignador `Outer`.|  
|`value_type`|Este tipo es un sinónimo del `value_type` asociado con el asignador `Outer`.|  
|`void_pointer`|Este tipo es un sinónimo del `void_pointer` asociado con el asignador `Outer`.|  
  
### <a name="structs"></a>Structs  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[scoped_allocator_adaptor::rebind (Struct)](#scoped_allocator_adaptor__rebind_struct)|Define el tipo `Outer::rebind\<Other>::other` como sinónimo de `scoped_allocator_adaptor\<Other, Inner...>`.|  
  
### <a name="methods"></a>Métodos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[scoped_allocator_adaptor::allocate (método)](#scoped_allocator_adaptor__allocate_method)|Asigna memoria usando el asignador `Outer`.|  
|[scoped_allocator_adaptor::construct (método)](#scoped_allocator_adaptor__construct_method)|Construye un objeto.|  
|[scoped_allocator_adaptor::deallocate (método)](#scoped_allocator_adaptor__deallocate_method)|Desasigna los objetos mediante el asignador exterior.|  
|[scoped_allocator_adaptor::destroy (método)](#scoped_allocator_adaptor__destroy_method)|Destruye un objeto especificado.|  
|[scoped_allocator_adaptor::inner_allocator (método)](#scoped_allocator_adaptor__inner_allocator_method)|Recupera una referencia al objeto almacenado de tipo `inner_allocator_type`.|  
|[scoped_allocator_adaptor::max_size (método)](#scoped_allocator_adaptor__max_size_method)|Determina el número máximo de objetos que el asignador exterior puede asignar.|  
|[scoped_allocator_adaptor::outer_allocator (método)](#scoped_allocator_adaptor__outer_allocator_method)|Recupera una referencia al objeto almacenado de tipo `outer_allocator_type`.|  
|[scoped_allocator_adaptor::select_on_container_copy_construction (método)](#scoped_allocator_adaptor__select_on_container_copy_construction_method)|Crea un nuevo objeto `scoped_allocator_adaptor` con cada objeto de asignador almacenado inicializado mediante una llamada a `select_on_container_copy_construction` para cada asignador correspondiente.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<scoped_allocator>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namescopedallocatoradaptorallocatemethoda--scopedallocatoradaptorallocate-method"></a><a name="scoped_allocator_adaptor__allocate_method"></a>  scoped_allocator_adaptor::allocate (método)  
 Asigna memoria usando el asignador `Outer`.  
  
```cpp  
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```  
  
### <a name="parameters"></a>Parámetros  
 `count`  
 El número de elementos para los que se puede asignar suficiente espacio de almacenamiento.  
  
 `hint`  
 Un puntero que es posible que ayude el objeto de asignador ubicando la dirección de un objeto asignado antes de la solicitud.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera función miembro devuelve `Outer_traits::allocate(outer_allocator(), count)`. La segunda función miembro devuelve `Outer_traits::allocate(outer_allocator(), count, hint)`.  
  
##  <a name="a-namescopedallocatoradaptorconstructmethoda--scopedallocatoradaptorconstruct-method"></a><a name="scoped_allocator_adaptor__construct_method"></a>  scoped_allocator_adaptor::construct (método)  
 Construye un objeto.  
  
```cpp  
template <class Ty, class... Atypes>  
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>  
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,  
    tuple<Atypes1&&...>  
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>  
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr,  
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptr`  
 Un puntero a la ubicación de memoria donde se va a crear el objeto.  
  
 `args`  
 Una lista de argumentos.  
  
 `first`  
 Un objeto del primer tipo en un par.  
  
 `second`  
 Un objeto del segundo tipo en un par.  
  
 `right`  
 Un objeto existente para mover o copiar.  
  
### <a name="remarks"></a>Comentarios  
 El primer método construye el objeto en `ptr` mediante una llamada a `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, donde `xargs...` es uno de los siguientes.  
  
-   Si `uses_allocator<Ty, inner_allocator_type>` es falso `xargs...` es `args...`.  
  
-   Si `uses_allocator<Ty, inner_allocator_type>` es verdadero y `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` es verdadero, entonces `xargs...` es `allocator_arg, inner_allocator(), args...`.  
  
-   Si `uses_allocator<Ty, inner_allocator_type>` es verdadero y `is_constructible<Ty, args..., inner_allocator()>` es verdadero, entonces `xargs...` es `args..., inner_allocator()`.  
  
 El segundo método construye el objeto de par en `ptr` mediante una llamada a `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`, donde `xargs...` es `first...` modificado como en la lista anterior, y `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, donde `xargs...` es `second...` modificado como en la lista anterior.  
  
 El tercer método se comporta igual que `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.  
  
 El cuarto método se comporta igual que `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.  
  
 El quinto método se comporta igual que `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.  
  
 El sexto método se comporta igual que `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.  
  
##  <a name="a-namescopedallocatoradaptordeallocatemethoda--scopedallocatoradaptordeallocate-method"></a><a name="scoped_allocator_adaptor__deallocate_method"></a>  scoped_allocator_adaptor::deallocate (método)  
 Desasigna los objetos mediante el asignador exterior.  
  
```cpp  
void deallocate(pointer ptr, size_type count);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptr`  
 Un puntero a la ubicación inicial de los objetos que se van a desasignar.  
  
 `count`  
 El número de objetos para desasignar.  
  
##  <a name="a-namescopedallocatoradaptordestroymethoda--scopedallocatoradaptordestroy-method"></a><a name="scoped_allocator_adaptor__destroy_method"></a>  scoped_allocator_adaptor::destroy (método)  
 Destruye un objeto especificado.  
  
```cpp  
template <class Ty>  
void destroy(Ty* ptr)  
```  
  
### <a name="parameters"></a>Parámetros  
 `ptr`  
 Un puntero al objeto que se va a destruir.  
  
### <a name="return-value"></a>Valor devuelto  
 `Outermost_traits::destroy(OUTERMOST(*this), ptr)`  
  
##  <a name="a-namescopedallocatoradaptorinnerallocatormethoda--scopedallocatoradaptorinnerallocator-method"></a><a name="scoped_allocator_adaptor__inner_allocator_method"></a>  scoped_allocator_adaptor::inner_allocator (método)  
 Recupera una referencia al objeto almacenado de tipo `inner_allocator_type`.  
  
```cpp  
inner_allocator_type& inner_allocator() noexcept;  
const inner_allocator_type& inner_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al objeto almacenado de tipo `inner_allocator_type`.  
  
##  <a name="a-namescopedallocatoradaptormaxsizemethoda--scopedallocatoradaptormaxsize-method"></a><a name="scoped_allocator_adaptor__max_size_method"></a>  scoped_allocator_adaptor::max_size (método)  
 Determina el número máximo de objetos que el asignador exterior puede asignar.  
  
```cpp  
size_type max_size();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `Outer_traits::max_size(outer_allocator())`  
  
##  <a name="a-namescopedallocatoradaptorouterallocatormethoda--scopedallocatoradaptorouterallocator-method"></a><a name="scoped_allocator_adaptor__outer_allocator_method"></a>  scoped_allocator_adaptor::outer_allocator (método)  
 Recupera una referencia al objeto almacenado de tipo `outer_allocator_type`.  
  
```cpp  
outer_allocator_type& outer_allocator() noexcept;  
const outer_allocator_type& outer_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al objeto almacenado de tipo `outer_allocator_type`.  
  
##  <a name="a-namescopedallocatoradaptorrebindstructa--scopedallocatoradaptorrebind-struct"></a><a name="scoped_allocator_adaptor__rebind_struct"></a>  scoped_allocator_adaptor::rebind (Struct)  
 Define el tipo `Outer::rebind\<Other>::other` como sinónimo de `scoped_allocator_adaptor\<Other, Inner...>`.  
  
struct rebind{  
   typedef Other_traits::rebind\<Other>  
   Other_alloc;  
   typedef scoped_allocator_adaptor\<Other_alloc, Inner...> other;  
   };  
  
##  <a name="a-namescopedallocatoradaptorscopedallocatoradaptorconstructora--scopedallocatoradaptorscopedallocatoradaptor-constructor"></a><a name="scoped_allocator_adaptor__scoped_allocator_adaptor_constructor"></a>  scoped_allocator_adaptor::scoped_allocator_adaptor (constructor)  
 Construye un objeto `scoped_allocator_adaptor`.  
  
```cpp  
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(Outer2&& al,  
    const Inner&... rest) noexcept;  
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Un `scoped_allocator_adaptor` existente.  
  
 `al`  
 Un asignador existente que se usará como el asignador exterior.  
  
 `rest`  
 Una lista de asignadores que se usarán como los asignadores exteriores.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor construye de manera predeterminada sus objetos de asignador almacenado. Cada uno de los tres constructores siguientes construye los objetos de asignador almacenado de los objetos correspondientes en `right`. El último constructor construye los objetos de asignador almacenado a partir de los argumentos correspondientes en la lista de argumentos.  
  
##  <a name="a-namescopedallocatoradaptorselectoncontainercopyconstructionmethoda--scopedallocatoradaptorselectoncontainercopyconstruction-method"></a><a name="scoped_allocator_adaptor__select_on_container_copy_construction_method"></a>  scoped_allocator_adaptor::select_on_container_copy_construction (método)  
 Crea un nuevo objeto `scoped_allocator_adaptor` con cada objeto de asignador almacenado inicializado mediante una llamada a `select_on_container_copy_construction` para cada asignador correspondiente.  
  
```cpp  
scoped_allocator_adaptor select_on_container_copy_construction();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve eficazmente `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. El resultado es un nuevo objeto `scoped_allocator_adaptor` con cada objeto de asignador almacenado inicializado mediante una llamada a `al.select_on_container_copy_construction()` para el correspondiente asignador `al`.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)




