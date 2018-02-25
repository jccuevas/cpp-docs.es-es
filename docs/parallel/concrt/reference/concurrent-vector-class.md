---
title: Clase concurrent_vector | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
dev_langs:
- C++
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b1f196a4eaf8685a33b1ef4847e44f62015ed1ed
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="concurrentvector-class"></a>Clase concurrent_vector
La clase `concurrent_vector` es una clase de contenedor de secuencia que permite el acceso aleatorio a cualquier elemento. Habilita las operaciones de anexión segura para simultaneidad, acceso de elemento, acceso de iterador e iterador transversal.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
 private details::_Concurrent_vector_base_v4;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de los elementos que se almacenará en el vector.  
  
 `_Ax`  
 El tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria para el vector simultáneo. Este argumento es opcional y el valor predeterminado es `allocator<T>`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`allocator_type`|Tipo que representa la clase de asignador para el vector simultáneo.|  
|`const_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer un `const` elemento en un vector simultáneo.|  
|`const_pointer`|Un tipo que proporciona un puntero a un `const` elemento en un vector simultáneo.|  
|`const_reference`|Un tipo que proporciona una referencia a un `const` elemento almacenado en un vector simultáneo para leer y realizar `const` operaciones.|  
|`const_reverse_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede lee cualquier `const` elemento del vector simultáneo.|  
|`difference_type`|Un tipo que proporciona la distancia firmada entre dos elementos en un vector simultáneo.|  
|`iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento en un vector simultáneo. Modificación de un elemento mediante el iterador no es seguro para simultaneidad.|  
|`pointer`|Un tipo que proporciona un puntero a un elemento en un vector simultáneo.|  
|`reference`|Un tipo que proporciona una referencia a un elemento almacenado en un vector simultáneo.|  
|`reverse_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento en un vector simultáneo invertido. Modificación de un elemento mediante el iterador no es seguro para simultaneidad.|  
|`size_type`|Tipo que cuenta el número de elementos de un vector simultáneo.|  
|`value_type`|Tipo que representa el tipo de datos almacenados en un vector simultáneo.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent_vector](#ctor)|Sobrecargado. Construye un vector simultáneo.|  
|[~concurrent_vector Destructor](#dtor)|Borra todos los elementos y destruye este vector simultáneo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[assign](#assign)|Sobrecargado. Borra los elementos del vector simultáneo y asigna a él o bien `_N` copias de `_Item`, o los valores especificados por el intervalo de iterador [ `_Begin`, `_End`). Este método no es seguro para la simultaneidad.|  
|[at](#at)|Sobrecargado. Proporciona acceso al elemento en el índice especificado en el vector simultáneo. Este método es seguro para simultaneidad para las operaciones de lectura y también durante el aumento del vector, como se ha asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.|  
|[back](#back)|Sobrecargado. Devuelve una referencia o un `const` hacen referencia al último elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.|  
|[begin](#begin)|Sobrecargado. Devuelve un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|  
|[capacity](#capacity)|Devuelve el tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria. Este método es seguro para simultaneidad.|  
|[cbegin](#cbegin)|Devuelve un iterador de tipo `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|  
|[cend](#cend)|Devuelve un iterador de tipo `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|  
|[clear](#clear)|Borra todos los elementos del vector simultáneo. Este método no es seguro para la simultaneidad.|  
|[crbegin](#crbegin)|Devuelve un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|  
|[crend](#crend)|Devuelve un iterador de tipo `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|  
|[empty](#empty)|Comprueba si el vector simultáneo está vacío en el momento en que se llama a este método. Este método es seguro para simultaneidad.|  
|[end](#end)|Sobrecargado. Devuelve un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|  
|[front](#front)|Sobrecargado. Devuelve una referencia o un `const` referencia al primer elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.|  
|[get_allocator](#get_allocator)|Devuelve una copia del asignador usada para construir el vector simultáneo. Este método es seguro para simultaneidad.|  
|[grow_by](#grow_by)|Sobrecargado. Aumenta este vector simultáneo por `_Delta` elementos. Este método es seguro para simultaneidad.|  
|[grow_to_at_least](#grow_to_at_least)|Aumenta este vector simultáneo hasta que tenga al menos `_N` elementos. Este método es seguro para simultaneidad.|  
|[max_size](#max_size)|Devuelve el número máximo de elementos que puede contener el vector simultáneo. Este método es seguro para simultaneidad.|  
|[push_back](#push_back)|Sobrecargado. El elemento especificado se anexa al final del vector simultáneo. Este método es seguro para simultaneidad.|  
|[rbegin](#rbegin)|Sobrecargado. Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|  
|[rend](#rend)|Sobrecargado. Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|  
|[reserve](#reserve)|Asigna suficiente espacio para crecer el vector simultáneo al tamaño `_N` sin tener que asignar más memoria más adelante. Este método no es seguro para la simultaneidad.|  
|[resize](#resize)|Sobrecargado. Cambia el tamaño del vector simultáneo al tamaño solicitado, eliminando o agregando elementos según sea necesario. Este método no es seguro para la simultaneidad.|  
|[shrink_to_fit](#shrink_to_fit)|Compacta la representación interna del vector simultáneo para reducir la fragmentación y optimizar el uso de memoria. Este método no es seguro para la simultaneidad.|  
|[size](#size)|Devuelve el número de elementos del vector simultáneo. Este método es seguro para simultaneidad.|  
|[swap](#swap)|Intercambia el contenido de dos vectores simultáneos. Este método no es seguro para la simultaneidad.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[operator[]](#operator_at)|Sobrecargado. Proporciona acceso al elemento en el índice especificado en el vector simultáneo. Este método es seguro para simultaneidad para las operaciones de lectura y también durante el aumento del vector, siempre que se haya asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.|  
|[operator=](#operator_eq)|Sobrecargado. Asigna el contenido de otro objeto `concurrent_vector` a este. Este método no es seguro para la simultaneidad.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener información detallada sobre la `concurrent_vector` de clases, consulte [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Concurrent_vector_base_v4`  
  
 `_Allocator_base`  
  
 `concurrent_vector`  
  
## <a name="requirements"></a>Requisitos  
 **Header:** concurrent_vector.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="assign"></a> asignar 

 Borra los elementos del vector simultáneo y asigna a él o bien `_N` copias de `_Item`, o los valores especificados por el intervalo de iterador [ `_Begin`, `_End`). Este método no es seguro para la simultaneidad.  
  
```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```  
  
### <a name="parameters"></a>Parámetros  
 `_InputIterator`  
 El tipo del iterador especificado.  
  
 `_N`  
 El número de elementos que se va a copiar en el vector simultáneo.  
  
 `_Item`  
 Referencia a un valor utilizado para rellenar el vector simultáneo.  
  
 `_Begin`  
 Un iterador al primer elemento del intervalo de origen.  
  
 `_End`  
 Un iterador a uno más allá del último elemento del intervalo de origen.  
  
### <a name="remarks"></a>Comentarios  
 `assign` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo cuando se llama a este método.  
  
##  <a name="at"></a> en 

 Proporciona acceso al elemento en el índice especificado en el vector simultáneo. Este método es seguro para simultaneidad para las operaciones de lectura y también durante el aumento del vector, como se ha asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.  
  
```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 El índice del elemento que se va a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al elemento en el índice especificado.  
  
### <a name="remarks"></a>Comentarios  
 La versión de la función `at` que devuelve no `const` referencia no se puede usar para escribir simultáneamente en el elemento desde subprocesos diferentes. Un objeto de sincronización diferente debe utilizarse para sincronizar simultáneas de lectura y las operaciones de escritura al mismo elemento de datos.  
  
 El método produce `out_of_range` si `_Index` es mayor o igual que el tamaño del vector simultáneo, y `range_error` si el índice es para una parte rota del vector. Para obtener detalles sobre cómo un vector puede dejen de funcionar, consulte [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
##  <a name="back"></a> Atrás 

 Devuelve una referencia o un `const` hacen referencia al último elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.  
  
```
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia o una `const` hacen referencia al último elemento del vector simultáneo.  
  
##  <a name="begin"></a> BEGIN 

 Devuelve un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo.  
  
##  <a name="capacity"></a> Capacidad 

 Devuelve el tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria. Este método es seguro para simultaneidad.  
  
```
size_type capacity() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria.  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de una biblioteca estándar de C++ `vector`, un `concurrent_vector` objeto no mueve los elementos existentes si asigna más memoria.  
  
##  <a name="cbegin"></a> cbegin 

 Devuelve un iterador de tipo `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `const_iterator` al principio del vector simultáneo.  
  
##  <a name="cend"></a> cend 

 Devuelve un iterador de tipo `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `const_iterator` al final del vector simultáneo.  
  
##  <a name="clear"></a> Borrar 

 Borra todos los elementos del vector simultáneo. Este método no es seguro para la simultaneidad.  
  
```
void clear();
```  
  
### <a name="remarks"></a>Comentarios  
 `clear` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo cuando se llama a este método. `clear` no se libera las matrices internas. Para las matrices internas libres, llame a la función `shrink_to_fit` después `clear`.  
  
##  <a name="ctor"></a> concurrent_vector 

 Construye un vector simultáneo.  
  
```
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```  
  
### <a name="parameters"></a>Parámetros  
 `M`  
 El tipo de asignador del vector de origen.  
  
 `_InputIterator`  
 El tipo de iterador de entrada.  
  
 `_Al`  
 La clase de asignador que se usa con este objeto.  
  
 `_Vector`  
 El objeto de origen `concurrent_vector` del que copiar o mover elementos.  
  
 `_N`  
 Capacidad inicial del objeto `concurrent_vector`.  
  
 `_Item`  
 El valor de elementos en el objeto construido.  
  
 `_Begin`  
 Posición del primer elemento en el intervalo de elementos que se va a copiar.  
  
 `_End`  
 Posición del primer elemento más allá del intervalo de elementos que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Todos los constructores almacenan un objeto de asignador `_Al` e inicializan el vector.  
  
 El primer constructor especifica un vector inicial vacío y especifica explícitamente el tipo de asignador. para su uso.  
  
 El segundo y tercer constructor especifican una copia del vector simultáneo `_Vector`.  
  
 El cuarto constructor especifica un movimiento del vector simultáneo `_Vector`.  
  
 El quinto constructor especifica una repetición de un número especificado ( `_N`) de elementos del valor predeterminado para la clase `T`.  
  
 El sexto constructor especifica una repetición de ( `_N`) elementos de valor `_Item`.  
  
 El último constructor especifica los valores proporcionados por el intervalo de iterador [ `_Begin`, `_End`).  
  
##  <a name="dtor"></a> ~concurrent_vector 

 Borra todos los elementos y destruye este vector simultáneo.  
  
```
~concurrent_vector();
```  
  
##  <a name="crbegin"></a> crbegin 

 Devuelve un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo.  
  
##  <a name="crend"></a> crend 

 Devuelve un iterador de tipo `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `const_reverse_iterator` al final del vector simultáneo.  
  
##  <a name="empty"></a> vacía 

 Comprueba si el vector simultáneo está vacío en el momento en que se llama a este método. Este método es seguro para simultaneidad.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el vector está vacío en el momento en que se llamó a la función, `false` en caso contrario.  
  
##  <a name="end"></a> Final 

 Devuelve un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo.  
  
##  <a name="front"></a> Principio 

 Devuelve una referencia o un `const` referencia al primer elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.  
  
```
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia o una `const` referencia al primer elemento del vector simultáneo.  
  
##  <a name="get_allocator"></a> get_allocator 

 Devuelve una copia del asignador usada para construir el vector simultáneo. Este método es seguro para simultaneidad.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una copia del asignador usada para construir la `concurrent_vector` objeto.  
  
##  <a name="grow_by"></a> grow_by 

 Aumenta este vector simultáneo por `_Delta` elementos. Este método es seguro para simultaneidad.  
  
```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Delta`  
 El número de elementos que se va a anexar al objeto.  
  
 `_Item`  
 El valor para inicializar los nuevos elementos con.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador al primer elemento anexado.  
  
### <a name="remarks"></a>Comentarios  
 Si `_Item` no se especifica, los nuevos elementos están construido de forma predeterminada.  
  
##  <a name="grow_to_at_least"></a> grow_to_at_least 

 Aumenta este vector simultáneo hasta que tenga al menos `_N` elementos. Este método es seguro para simultaneidad.  
  
```
iterator grow_to_at_least(size_type _N);
```  
  
### <a name="parameters"></a>Parámetros  
 `_N`  
 El nuevo tamaño mínimo para el `concurrent_vector` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que apunta al principio de la secuencia anexada o al elemento en el índice `_N` si no se anexa ningún elemento.  
  
##  <a name="max_size"></a> max_size 

 Devuelve el número máximo de elementos que puede contener el vector simultáneo. Este método es seguro para simultaneidad.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de elementos de la `concurrent_vector` objeto puede contener.  
  
##  <a name="operator_eq"></a> operador = 

 Asigna el contenido de otro objeto `concurrent_vector` a este. Este método no es seguro para la simultaneidad.  
  
```
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```  
  
### <a name="parameters"></a>Parámetros  
 `M`  
 El tipo de asignador del vector de origen.  
  
 `_Vector`  
 Objeto `concurrent_vector` de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `concurrent_vector` objeto.  
  
##  <a name="operator_at"></a> operator] 

 Proporciona acceso al elemento en el índice especificado en el vector simultáneo. Este método es seguro para simultaneidad para las operaciones de lectura y también durante el aumento del vector, siempre que se haya asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.  
  
```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 El índice del elemento que se va a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al elemento en el índice especificado.  
  
### <a name="remarks"></a>Comentarios  
 La versión de `operator []` que devuelve no `const` referencia no se puede usar para escribir simultáneamente en el elemento desde subprocesos diferentes. Un objeto de sincronización diferente debe utilizarse para sincronizar simultáneas de lectura y las operaciones de escritura al mismo elemento de datos.  
  
 No hay límites para asegurarse de que no se realiza la comprobación `_Index` es un índice válido en el vector simultáneo.  
  
##  <a name="push_back"></a> push_back 

 El elemento especificado se anexa al final del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Item`  
 El valor se va a anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador al elemento anexado.  
  
##  <a name="rbegin"></a> rbegin 

 Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo.  
  
##  <a name="rend"></a> rend) 

 Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
reverse_iterator rend();

const_reverse_iterator rend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo.  
  
##  <a name="reserve"></a> reservar 

 Asigna suficiente espacio para crecer el vector simultáneo al tamaño `_N` sin tener que asignar más memoria más adelante. Este método no es seguro para la simultaneidad.  
  
```
void reserve(size_type _N);
```  
  
### <a name="parameters"></a>Parámetros  
 `_N`  
 El número de elementos que se va a reservar espacio para.  
  
### <a name="remarks"></a>Comentarios  
 `reserve` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo cuando se llama a este método. La capacidad del vector simultáneo después de que el método devuelve puede ser mayor que la reserva solicitada.  
  
##  <a name="resize"></a> Cambio de tamaño 

 Cambia el tamaño del vector simultáneo al tamaño solicitado, eliminando o agregando elementos según sea necesario. Este método no es seguro para la simultaneidad.  
  
```
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `_N`  
 El nuevo tamaño de la concurrent_vector.  
  
 `val`  
 El valor de nuevos elementos se agrega al vector si el nuevo tamaño es mayor que el tamaño original. Si se omite el valor, los nuevos objetos se asignan el valor predeterminado para su tipo.  
  
### <a name="remarks"></a>Comentarios  
 Si el tamaño del contenedor es menor que el tamaño solicitado, los elementos se agregan al vector hasta que alcance el tamaño solicitado. Si el tamaño del contenedor es mayor que el tamaño solicitado, los elementos más cercanos al final del contenedor se eliminan hasta que el contenedor alcanza el tamaño `_N`. Si el tamaño actual del contenedor es igual que el tamaño solicitado, no se lleva a cabo ninguna acción.  
  
 `resize` no es simultaneidad seguro. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo cuando se llama a este método.  
  
##  <a name="shrink_to_fit"></a> shrink_to_fit 

 Compacta la representación interna del vector simultáneo para reducir la fragmentación y optimizar el uso de memoria. Este método no es seguro para la simultaneidad.  
  
```
void shrink_to_fit();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se internamente volver a asignar elementos de movimiento de memoria, lo que invalida todos los iteradores. `shrink_to_fit` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a esta función.  
  
##  <a name="size"></a> Tamaño 

 Devuelve el número de elementos del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en esta `concurrent_vector` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño devuelto está garantizado para incluir todos los elementos anexados por llamadas a la función `push_back`, aumente o disminuya de operaciones que se han completado antes de invocar este método. Sin embargo, también puede incluir elementos que se asignan pero aún están en construcción mediante llamadas simultáneas a cualquiera de los métodos de crecimiento.  
  
##  <a name="swap"></a> Intercambiar 

 Intercambia el contenido de dos vectores simultáneos. Este método no es seguro para la simultaneidad.  
  
```
void swap(concurrent_vector& _Vector);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Vector`  
 La `concurrent_vector` objeto que se va a intercambiar el contenido.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)



