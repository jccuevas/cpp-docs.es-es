---
title: Clase concurrent_vector | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_vector/Concurrency::concurrent_vector
- concurrent_vector/concurrency::concurrent_vector
dev_langs:
- C++
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: fdc84a03c562a4efa336f62c0cf0a7529c420f95
ms.lasthandoff: 02/24/2017

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
 El tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria para el vector simultáneo. Este argumento es opcional y el valor predeterminado es `allocator<``T``>`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`allocator_type`|Tipo que representa la clase de asignador del vector simultáneo.|  
|`const_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer un `const` elemento en un vector simultáneo.|  
|`const_pointer`|Un tipo que proporciona un puntero a un `const` elemento en un vector simultáneo.|  
|`const_reference`|Un tipo que proporciona una referencia a un `const` elemento almacenado en un vector simultáneo para leer y realizar `const` operaciones.|  
|`const_reverse_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede lee cualquier `const` elemento del vector simultáneo.|  
|`difference_type`|Un tipo que proporciona la distancia firmada entre dos elementos en un vector simultáneo.|  
|`iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento en un vector simultáneo. Modificación de un elemento utilizando el iterador no es seguro para simultaneidad.|  
|`pointer`|Un tipo que proporciona un puntero a un elemento en un vector simultáneo.|  
|`reference`|Un tipo que proporciona una referencia a un elemento almacenado en un vector simultáneo.|  
|`reverse_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento en un vector simultáneo invertido. Modificación de un elemento utilizando el iterador no es seguro para simultaneidad.|  
|`size_type`|Un tipo que cuenta el número de elementos en un vector simultáneo.|  
|`value_type`|Tipo que representa el tipo de datos almacenados en un vector simultáneo.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[concurrent_vector Constructor](#ctor)|Sobrecargado. Construye un vector simultáneo.|  
|[~ concurrent_vector (destructor)](#dtor)|Borra todos los elementos y se destruye este vector simultáneo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[assign (método)](#assign)|Sobrecargado. Borra los elementos del vector simultáneo y le asigna bien `_N` copias de `_Item`, o los valores especificados por el intervalo de iterador [ `_Begin`, `_End`). Este método no es seguro para la simultaneidad.|  
|[AT (método)](#at)|Sobrecargado. Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad para operaciones de lectura y también durante el aumento del vector, siempre que se haya asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.|  
|[back (método)](#back)|Sobrecargado. Devuelve una referencia o un `const` hacen referencia al último elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.|  
|[Begin (método)](#begin)|Sobrecargado. Devuelve un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|  
|[capacidad (método)](#capacity)|Devuelve el tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria. Este método es seguro para simultaneidad.|  
|[cbegin (método)](#cbegin)|Devuelve un iterador de tipo `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|  
|[cend (método)](#cend)|Devuelve un iterador de tipo `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|  
|[Clear (método)](#clear)|Borra todos los elementos del vector simultáneo. Este método no es seguro para la simultaneidad.|  
|[crbegin (método)](#crbegin)|Devuelve un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|  
|[crend (método)](#crend)|Devuelve un iterador de tipo `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|  
|[Empty (método)](#empty)|Comprueba si el vector simultáneo está vacío en el momento en que se llama a este método. Este método es seguro para simultaneidad.|  
|[end (método)](#end)|Sobrecargado. Devuelve un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|  
|[front (método)](#front)|Sobrecargado. Devuelve una referencia o un `const` referencia al primer elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.|  
|[get_allocator (método)](#get_allocator)|Devuelve una copia del asignador usada para construir el vector simultáneo. Este método es seguro para simultaneidad.|  
|[grow_by (método)](#grow_by)|Sobrecargado. Aumenta este vector simultáneo por `_Delta` elementos. Este método es seguro para simultaneidad.|  
|[grow_to_at_least (método)](#grow_to_at_least)|Aumenta este vector simultáneo hasta que tenga al menos `_N` elementos. Este método es seguro para simultaneidad.|  
|[max_size (método)](#max_size)|Devuelve el número máximo de elementos que puede contener el vector simultáneo. Este método es seguro para simultaneidad.|  
|[push_back (método)](#push_back)|Sobrecargado. Agrega el elemento especificado al final del vector simultáneo. Este método es seguro para simultaneidad.|  
|[rbegin (método)](#rbegin)|Sobrecargado. Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|  
|[rend (método)](#rend)|Sobrecargado. Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|  
|[Reserve (método)](#reserve)|Asigna espacio suficiente para crecer el vector simultáneo al tamaño `_N` sin tener que asignar más memoria más adelante. Este método no es seguro para la simultaneidad.|  
|[Resize (método)](#resize)|Sobrecargado. Cambia el tamaño del vector simultáneo al tamaño solicitado, eliminando o agregando elementos según sea necesario. Este método no es seguro para la simultaneidad.|  
|[shrink_to_fit (método)](#shrink_to_fit)|Compacta la representación interna del vector simultáneo para reducir la fragmentación y optimizar el uso de memoria. Este método no es seguro para la simultaneidad.|  
|[tamaño (método)](#size)|Devuelve el número de elementos del vector simultáneo. Este método es seguro para simultaneidad.|  
|[swap (método)](#swap)|Intercambia el contenido de dos vectores simultáneos. Este método no es seguro para la simultaneidad.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operator [] (operador)](#operator_at)|Sobrecargado. Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad para operaciones de lectura y también durante el aumento del vector, siempre que se haya asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.|  
|[operador = (operador)](#operator_eq)|Sobrecargado. Asigna el contenido de otro objeto `concurrent_vector` a este. Este método no es seguro para la simultaneidad.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener información detallada sobre la `concurrent_vector` de clases, consulte [objetos y contenedores paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Concurrent_vector_base_v4`  
  
 `_Allocator_base`  
  
 `concurrent_vector`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concurrent_vector.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameassigna-assign"></a><a name="assign"></a>asignar 

 Borra los elementos del vector simultáneo y le asigna bien `_N` copias de `_Item`, o los valores especificados por el intervalo de iterador [ `_Begin`, `_End`). Este método no es seguro para la simultaneidad.  
  
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
 El número de elementos que desea copiar en el vector simultáneo.  
  
 `_Item`  
 Referencia a un valor utilizado para rellenar el vector simultáneo.  
  
 `_Begin`  
 Un iterador al primer elemento del intervalo de origen.  
  
 `_End`  
 Un iterador a uno más allá del último elemento del intervalo de origen.  
  
### <a name="remarks"></a>Comentarios  
 `assign`no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a este método.  
  
##  <a name="a-nameata-at"></a><a name="at"></a>en 

 Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad para operaciones de lectura y también durante el aumento del vector, siempre que se haya asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.  
  
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
 La versión de la función `at` que devuelve no `const` referencia no se puede usar para escribir concurrentemente en el elemento de subprocesos diferentes. Un objeto de sincronización diferente se debe usar para sincronizar simultáneas de lectura y escritura al mismo elemento de datos.  
  
 El método produce `out_of_range` si `_Index` es mayor o igual que el tamaño del vector simultáneo, y `range_error` si el índice es para una parte rota del vector. Para obtener más información sobre cómo un vector puede dejen de funcionar, consulte [objetos y contenedores paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
##  <a name="a-namebacka-back"></a><a name="back"></a>Atrás 

 Devuelve una referencia o un `const` hacen referencia al último elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.  
  
```
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia o una `const` hacen referencia al último elemento del vector simultáneo.  
  
##  <a name="a-namebegina-begin"></a><a name="begin"></a>comenzar 

 Devuelve un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo.  
  
##  <a name="a-namecapacitya-capacity"></a><a name="capacity"></a>capacidad 

 Devuelve el tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria. Este método es seguro para simultaneidad.  
  
```
size_type capacity() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria.  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de una biblioteca estándar de C++ `vector`, un `concurrent_vector` objeto no mueve los elementos existentes si asigna más memoria.  
  
##  <a name="a-namecbegina-cbegin"></a><a name="cbegin"></a>cbegin 

 Devuelve un iterador de tipo `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `const_iterator` al principio del vector simultáneo.  
  
##  <a name="a-namecenda-cend"></a><a name="cend"></a>cend 

 Devuelve un iterador de tipo `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `const_iterator` al final del vector simultáneo.  
  
##  <a name="a-namecleara-clear"></a><a name="clear"></a>Borrar 

 Borra todos los elementos del vector simultáneo. Este método no es seguro para la simultaneidad.  
  
```
void clear();
```  
  
### <a name="remarks"></a>Comentarios  
 `clear`no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a este método. `clear`no se libera las matrices internas. Para las matrices internas libres, llame a la función `shrink_to_fit` después `clear`.  
  
##  <a name="a-namectora-concurrentvector"></a><a name="ctor"></a>concurrent_vector 

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
  
 El primer constructor especifica un vector inicial vacío y especifica explícitamente el tipo de asignador. que se utiliza.  
  
 El segundo y tercer constructor especifican una copia del vector simultáneo `_Vector`.  
  
 El cuarto constructor especifica un movimiento del vector simultáneo `_Vector`.  
  
 El quinto constructor especifica una repetición de un número especificado ( `_N`) de los elementos del valor predeterminado para la clase `T`.  
  
 El sexto constructor especifica una repetición de ( `_N`) elementos de valor `_Item`.  
  
 El último constructor especifica los valores proporcionados por el intervalo de iterador [ `_Begin`, `_End`).  
  
##  <a name="a-namedtora-concurrentvector"></a><a name="dtor"></a>~ concurrent_vector 

 Borra todos los elementos y se destruye este vector simultáneo.  
  
```
~concurrent_vector();
```  
  
##  <a name="a-namecrbegina-crbegin"></a><a name="crbegin"></a>crbegin 

 Devuelve un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo.  
  
##  <a name="a-namecrenda-crend"></a><a name="crend"></a>crend 

 Devuelve un iterador de tipo `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `const_reverse_iterator` al final del vector simultáneo.  
  
##  <a name="a-nameemptya-empty"></a><a name="empty"></a>vacía 

 Comprueba si el vector simultáneo está vacío en el momento en que se llama a este método. Este método es seguro para simultaneidad.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el vector está vacío en el momento en que se llama a la función, `false` en caso contrario.  
  
##  <a name="a-nameenda-end"></a><a name="end"></a>final 

 Devuelve un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo.  
  
##  <a name="a-namefronta-front"></a><a name="front"></a>parte frontal 

 Devuelve una referencia o un `const` referencia al primer elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.  
  
```
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia o una `const` referencia al primer elemento del vector simultáneo.  
  
##  <a name="a-namegetallocatora-getallocator"></a><a name="get_allocator"></a>get_allocator 

 Devuelve una copia del asignador usada para construir el vector simultáneo. Este método es seguro para simultaneidad.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una copia del asignador usada para construir la `concurrent_vector` objeto.  
  
##  <a name="a-namegrowbya-growby"></a><a name="grow_by"></a>grow_by 

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
 El valor para inicializar los nuevos elementos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador al primer elemento anexado.  
  
### <a name="remarks"></a>Comentarios  
 Si `_Item` no se especifica, los nuevos elementos son construida de forma predeterminada.  
  
##  <a name="a-namegrowtoatleasta-growtoatleast"></a><a name="grow_to_at_least"></a>grow_to_at_least 

 Aumenta este vector simultáneo hasta que tenga al menos `_N` elementos. Este método es seguro para simultaneidad.  
  
```
iterator grow_to_at_least(size_type _N);
```  
  
### <a name="parameters"></a>Parámetros  
 `_N`  
 El nuevo tamaño mínimo para el `concurrent_vector` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que apunta al principio de la secuencia anexada o al elemento en el índice `_N` si no se anexara.  
  
##  <a name="a-namemaxsizea-maxsize"></a><a name="max_size"></a>max_size 

 Devuelve el número máximo de elementos que puede contener el vector simultáneo. Este método es seguro para simultaneidad.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de elementos de la `concurrent_vector` puede contener el objeto.  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

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
  
##  <a name="a-nameoperatorata-operator"></a><a name="operator_at"></a>operator] 

 Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad para operaciones de lectura y también durante el aumento del vector, siempre que se haya asegurado de que el valor `_Index` es menor que el tamaño del vector simultáneo.  
  
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
 La versión de `operator []` que devuelve no `const` referencia no se puede usar para escribir concurrentemente en el elemento de subprocesos diferentes. Un objeto de sincronización diferente se debe usar para sincronizar simultáneas de lectura y escritura al mismo elemento de datos.  
  
 Ninguna comprobación para asegurarse de que se lleva a cabo de límites `_Index` es un índice válido en el vector simultáneo.  
  
##  <a name="a-namepushbacka-pushback"></a><a name="push_back"></a>push_back 

 Agrega el elemento especificado al final del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Item`  
 El valor que se va a anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador al elemento anexado.  
  
##  <a name="a-namerbegina-rbegin"></a><a name="rbegin"></a>rbegin 

 Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo.  
  
##  <a name="a-namerenda-rend"></a><a name="rend"></a>rend 

 Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
reverse_iterator rend();

const_reverse_iterator rend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo.  
  
##  <a name="a-namereservea-reserve"></a><a name="reserve"></a>reservar 

 Asigna espacio suficiente para crecer el vector simultáneo al tamaño `_N` sin tener que asignar más memoria más adelante. Este método no es seguro para la simultaneidad.  
  
```
void reserve(size_type _N);
```  
  
### <a name="parameters"></a>Parámetros  
 `_N`  
 El número de elementos que se va a reservar espacio para.  
  
### <a name="remarks"></a>Comentarios  
 `reserve`no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a este método. La capacidad del vector simultáneo después de que el método devuelve puede ser mayor que la reserva solicitada.  
  
##  <a name="a-nameresizea-resize"></a><a name="resize"></a>cambiar el tamaño 

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
 El valor de los nuevos elementos se agrega al vector si el nuevo tamaño es mayor que el tamaño original. Si se omite el valor, los nuevos objetos se asignan el valor predeterminado para su tipo.  
  
### <a name="remarks"></a>Comentarios  
 Si el tamaño del contenedor es menor que el tamaño solicitado, los elementos se agregan al vector hasta que alcance el tamaño solicitado. Si el tamaño del contenedor es mayor que el tamaño solicitado, los elementos más cercanos al final del contenedor se eliminan hasta que el contenedor alcance el tamaño `_N`. Si el tamaño actual del contenedor es igual que el tamaño solicitado, no se lleva a cabo ninguna acción.  
  
 `resize`no es simultaneidad seguro. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a este método.  
  
##  <a name="a-nameshrinktofita-shrinktofit"></a><a name="shrink_to_fit"></a>shrink_to_fit 

 Compacta la representación interna del vector simultáneo para reducir la fragmentación y optimizar el uso de memoria. Este método no es seguro para la simultaneidad.  
  
```
void shrink_to_fit();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se internamente volver a asignar elementos de mover memoria, invalidar todos los iteradores. `shrink_to_fit`no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en el vector simultáneo al llamar a esta función.  
  
##  <a name="a-namesizea-size"></a><a name="size"></a>tamaño 

 Devuelve el número de elementos del vector simultáneo. Este método es seguro para simultaneidad.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en esta `concurrent_vector` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño devuelto está garantizado para incluir todos los elementos anexados por llamadas a la función `push_back`, o aumentar las operaciones que se han completado antes de invocar este método. Sin embargo, también puede incluir elementos que están asignados, pero aún están en construcción por llamadas simultáneas a cualquiera de los métodos de crecimiento.  
  
##  <a name="a-nameswapa-swap"></a><a name="swap"></a>intercambio 

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




