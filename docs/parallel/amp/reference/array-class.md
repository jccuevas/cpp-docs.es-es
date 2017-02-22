---
title: "array (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array (clase)"
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# array (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa un contenedor de datos que se utiliza para mover datos a una tecla de aceleración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
friend class array;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value_type`  
 El tipo de elemento de los datos.  
  
 `_Rank`  
 El rango de la matriz.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor de Array::Array](#array__array_constructor)|Inicializa una nueva instancia de la clase `array`.|  
|[Array:: ~ array (destructor)](#array___dtorarray_destructor)|Destruye el objeto `array`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Array:: copy_to (método)](#array__copy_to_method)|Copia el contenido de la matriz en otra matriz.|  
|[Array:: Data (método)](#array__data_method)|Devuelve un puntero a los datos sin procesar de la matriz.|  
|[Array:: get_accelerator_view (método)](#array__get_accelerator_view_method)|Devuelve el [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto que representa la ubicación donde se asigna la matriz. Esta propiedad puede tener acceso sólo a la CPU.|  
|[Array:: get_associated_accelerator_view (método)](#array__get_associated_accelerator_view_method)|Obtiene la segunda [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto que se pasa como parámetro cuando se llama a un constructor de ensayo para crear instancias de la [matriz](../../../parallel/amp/reference/array-class.md) objeto.|  
|[Array:: get_cpu_access_type (método)](#array__get_cpu_access_type_method)|Devuelve el [access_type ()](access_type%20Enumeration.md) de la matriz. Este método puede tener acceso sólo a la CPU.|  
|[Array:: get_extent (método)](#array__get_extent_method)|Devuelve el [extensión](../../../parallel/amp/reference/extent-class-cpp-amp.md) objeto de la matriz.|  
|[Array:: reinterpret_as (método)](#array__reinterpret_as_method)|Devuelve una matriz unidimensional que contiene todos los elementos de la `array` objeto.|  
|[Array:: Section (método)](#array__section_method)|Devuelve una subsección de la [matriz](../../../parallel/amp/reference/array-class.md) objeto que está en el origen especificado y, opcionalmente, que tiene la extensión especificada.|  
|[Array:: view_as (método)](#array__view_as_method)|Devuelve un [array_view](../../../parallel/amp/reference/array-view-class.md) objeto que se construye a partir del `array` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Array std:: vector&lt;value_type&gt; (operador)](#array__operator_std__vector_lt__value_type_gt__operator)|Utiliza `copy(*this, vector)` para convertir implícitamente la matriz en un std::[vector](vector%20Class.md) objeto.|  
|[Array::operator() (operador)](#array__operator___operator)|Devuelve el valor del elemento especificado por los parámetros.|  
|[Array:: operator [] (operador)](#array__operator_at_operator)|Devuelve el elemento situado en el índice especificado.|  
|[Array:: operator = (operador)](#array__operator_eq_operator)|Copia el contenido del elemento `array` objeto en éste.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Array::Rank (constante)](#array__rank_constant)|Almacena el rango de la matriz.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Miembro de datos de Array::accelerator_view](#array__accelerator_view_data_member)|Obtiene el [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto que representa la ubicación donde se asigna la matriz. Esta propiedad puede tener acceso sólo a la CPU.|  
|[Miembro de datos de Array::associated_accelerator_view](#array__associated_accelerator_view_data_member)|Obtiene la segunda [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto que se pasa como parámetro cuando se llama a un constructor de ensayo para crear instancias de la [matriz](../../../parallel/amp/reference/array-class.md) objeto.|  
|[Miembro de datos de Array::cpu_access_type](#array__cpu_access_type_data_member)|Obtiene el [access_type ()](access_type%20Enumeration.md) que representa cómo la CPU puede acceder al almacenamiento de la matriz.|  
|[Miembro de datos de Array::extent](#array__extent_data_member)|Obtiene la extensión que define la forma de la matriz.|  
  
## <a name="remarks"></a>Comentarios  
 El tipo `array<T,N>` representa una densa y normales (no escalonadas) *N*-matriz bidimensional que se encuentra en una ubicación específica, como una tecla de aceleración o la CPU. El tipo de datos de los elementos de la matriz es `T`, que debe ser de un tipo que es compatible con el Acelerador de destino. Aunque el rango `N`, (de la matriz se determina de forma estática y forma parte del tipo, el alcance de la matriz viene determinado por el tiempo de ejecución y se expresa mediante la clase `extent<N>`.  
  
 Una matriz puede tener cualquier número de dimensiones, aunque algunas funciones especializado para `array` objetos con rango uno, dos y tres. Si se omite el argumento de dimensión, el valor predeterminado es 1.  
  
 Datos de matriz se disponen de forma contigua en la memoria. Elementos que difieren en uno en la dimensión menos significativa son adyacentes en la memoria.  
  
 Matrices lógicamente se consideran tipos de valor, ya que cuando se copia una matriz en otra matriz, se realiza una copia en profundidad. Dos matrices nunca señalan a los mismos datos.  
  
 El `array<T,N>` tipo se utiliza en varios escenarios:  
  
-   Como un contenedor de datos que se puede utilizar en cálculos en un acelerador.  
  
-   Como un contenedor de datos para almacenar la memoria de la CPU del host (que puede utilizarse para copiar a y desde otras matrices).  
  
-   Como un objeto de almacenamiento provisional para que actúe como intermediario rápido en copias de dispositivo de host.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `array`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  
  
##  <a name="a-namearraydtorarraydestructora-arrayarray-destructor"></a><a name="array___dtorarray_destructor"></a>  Array:: ~ array (destructor)  
 Destruye el objeto `array`.  
  
```  
~array() restrict(cpu);
```  
  
##  <a name="a-namearrayacceleratorviewdatamembera-arrayacceleratorview-data-member"></a><a name="array__accelerator_view_data_member"></a>  Miembro de datos de Array::accelerator_view  
 Obtiene el [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto que representa la ubicación donde se asigna la matriz. Esta propiedad puede tener acceso sólo a la CPU.  
  
```  
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;  
```  
  
##  <a name="a-namearrayarrayconstructora-arrayarray-constructor"></a><a name="array__array_constructor"></a>  Constructor de Array::Array  
 Inicializa una nueva instancia de la [array (clase)](../../../parallel/amp/reference/array-class.md). No hay ningún constructor predeterminado para `array<T,N>`. Todos los constructores se ejecutan en la CPU. No puedan ejecutarse en un destino de Direct3D.  
  
```  
explicit array(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

 
explicit array(
    int _E0) restrict(cpu);

 
explicit array(
    int _E0,  
    int _E1) restrict(cpu);

 
explicit array(
    int _E0,  
    int _E1,  
    int _E2) restrict(cpu);

 
array(
    const Concurrency::extent<_Rank>& _Extent,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    int _E0,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    int _E2,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    const Concurrency::extent<_Rank>& _Extent,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
array(
    int _E0,  
    accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
array(
    int _E0,  
    int _E1,  
    int _E2,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    const Concurrency::extent<_Rank>& _Extent, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
template <
    typename _InputIterator  
>  
array(
    int _E0,  
    int _E1,  
    int _E2, _InputIterator _Src_first,  
    Concurrency::accelerator_view _Av,  
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

 
explicit array(
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);

 
array(
    const array_view<const value_type, _Rank>& _Src,  
    accelerator_view _Av  
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

 
array(
    const array_view<const value_type, _Rank>& _Src,  
    accelerator_view _Av,  
    accelerator_view _Associated_Av) restrict(cpu);

 
array(
    const array& _Other) restrict(cpu);

 
array(
    array&& _Other) restrict(cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Associated_Av`  
 Un accelerator_view que especifica la ubicación de destino preferido de la matriz.  
  
 `_Av`  
 Un [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto que especifica la ubicación de la matriz.  
  
 `_Cpu_access_type`  
 Deseado [access_type ()](access_type%20Enumeration.md)  para la matriz en la CPU. Este parámetro tiene un valor predeterminado de `access_type_auto` dejan la CPU `access_type` determinación al tiempo de ejecución. La CPU real `access_type` para la matriz se puede consultar mediante el `get_cpu_access_type` método.  
  
 `_Extent`  
 La extensión de cada dimensión de la matriz.  
  
 `_E0`  
 El componente más importante de la extensión de esta sección.  
  
 `_E1`  
 El componente siguiente-a-más significativo de la extensión de esta sección.  
  
 `_E2`  
 El componente menos significativo de la extensión de esta sección.  
  
 `_InputIterator`  
 El tipo de la entrada interator.  
  
 `_Src`  
 Para el objeto a copiar.  
  
 `_Src_first`  
 Un iterador de comienzo en el contenedor de origen.  
  
 `_Src_last`  
 Un iterador final en el contenedor de origen.  
  
 `_Other`  
 Otro origen de datos.  
  
 `_Rank`  
 El rango de la sección.  
  
 `value_type`  
 El tipo de datos de los elementos que se copian.  
  
##  <a name="a-namearrayassociatedacceleratorviewdatamembera-arrayassociatedacceleratorview-data-member"></a><a name="array__associated_accelerator_view_data_member"></a>  Miembro de datos de Array::associated_accelerator_view  
 Obtiene la segunda [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto que se pasa como parámetro cuando se llama a un constructor de ensayo para crear instancias de la [matriz](../../../parallel/amp/reference/array-class.md) objeto.  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="a-namearraycopytomethoda-arraycopyto-method"></a><a name="array__copy_to_method"></a>  Array:: copy_to (método)  
 Copia el contenido de la [matriz](../../../parallel/amp/reference/array-class.md) a otro `array`.  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const ;  
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 El [array_view](../../../parallel/amp/reference/array-view-class.md) objeto que se va a copiar a.  
  
##  <a name="a-namearraycpuaccesstypedatamembera-arraycpuaccesstype-data-member"></a><a name="array__cpu_access_type_data_member"></a>  Miembro de datos de Array::cpu_access_type  
 Obtiene la CPU access_type () permitido para esta matriz.  
  
```  
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;  
```  
  
##  <a name="a-namearraydatamethoda-arraydata-method"></a><a name="array__data_method"></a>  Array:: Data (método)  
 Devuelve un puntero a los datos sin procesar de la [matriz](../../../parallel/amp/reference/array-class.md).  
  
```  
value_type* data() restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a los datos sin procesar de la matriz.  
  
##  <a name="a-namearrayextentdatamembera-arrayextent-data-member"></a><a name="array__extent_data_member"></a>  Miembro de datos de Array::extent  
 Obtiene el [extensión](../../../parallel/amp/reference/extent-class-cpp-amp.md) objeto que define la forma de la [matriz](../../../parallel/amp/reference/array-class.md).  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="a-namearraygetacceleratorviewmethoda-arraygetacceleratorview-method"></a><a name="array__get_accelerator_view_method"></a>  Array:: get_accelerator_view (método)  
 Devuelve el [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto que representa la ubicación donde el [matriz](../../../parallel/amp/reference/array-class.md) se asigna el objeto. Esta propiedad puede tener acceso sólo a la CPU.  
  
```  
Concurrency::accelerator_view get_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 La `accelerator_view` objeto que representa la ubicación donde el [matriz](../../../parallel/amp/reference/array-class.md) se asigna el objeto.  
  
##  <a name="a-namearraygetassociatedacceleratorviewmethoda-arraygetassociatedacceleratorview-method"></a><a name="array__get_associated_accelerator_view_method"></a>  Array:: get_associated_accelerator_view (método)  
 Obtiene la segunda [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto que se pasa como parámetro cuando se llama a un constructor de ensayo para crear instancias de la [matriz](../../../parallel/amp/reference/array-class.md) objeto.  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const ;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El segundo [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto se pasa al constructor de ensayo.  
  
##  <a name="a-namearraygetcpuaccesstypemethoda-arraygetcpuaccesstype-method"></a><a name="array__get_cpu_access_type_method"></a>  Array:: get_cpu_access_type (método)  
 Parámetro access_type devuelve la CPU que se permite para esta matriz.  
  
```  
access_type get_cpu_access_type() const restrict(cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-namearraygetextentmethoda-arraygetextent-method"></a><a name="array__get_extent_method"></a>  Array:: get_extent (método)  
 Devuelve el [extensión](../../../parallel/amp/reference/extent-class-cpp-amp.md) objeto de la [matriz](../../../parallel/amp/reference/array-class.md).  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 La `extent` objeto de la [matriz](../../../parallel/amp/reference/array-class.md).  
  
##  <a name="a-namearrayoperatorstdvectorltvaluetypegtoperatora-arrayoperator-stdvectorltvaluetypegt-operator"></a><a name="array__operator_std__vector_lt__value_type_gt__operator"></a>  Array std:: vector&lt;value_type&gt; (operador)  
 Utiliza `copy(*this, vector)` para convertir implícitamente la matriz a un objeto std:: vector.  
  
''' operador std:: vector \< value_type > () const Restrict (CPU);
```  
  
### Parameters  
 `value_type`  
 The data type of the elements of the vector.  
  
### Return Value  
 An object of type `vector<T>` that contains a copy of the data that is contained in the array.  
  
##  <a name="array__operator___operator"></a>  array::operator() Operator  
 Returns the element value that is specified by the parameters.  
  
```  
value_type & operator() (const index \< _Rank > & _Index) restrict(amp,cpu);

 
Const value_type & operator() (const index \< _Rank > & _Index) restrict(amp,cpu) const;

 
value_type & restrict(amp,cpu) operator() (_I0 int, int _I1);

 
Const value_type & restrict(amp,cpu) const de operator() (_I0 int, int _I1);

 
value_type & restrict(amp,cpu) operator() (_I0 int, _I1 int, int _I2);

 
Const value_type & restrict(amp,cpu) const de operator() (_I0 int, _I1 int, int _I2);

 
TypeName details::_Projection_result_type \< value_type, _Rank >:: _Result_type operator() (_he int) restrict(amp,cpu);

 
TypeName details::_Projection_result_type \< value_type, _Rank >:: _Const_result_type restrict(amp,cpu) const de operator() (_he int);
```  
  
### Parameters  
 `_Index`  
 The location of the element.  
  
 `_I0`  
 The most significant component of the origin of this section.  
  
 `_I1`  
 The next-to-most-significant component of the origin of this section.  
  
 `_I2`  
 The least significant component of the origin of this section.  
  
 `_I`  
 The location of the element.  
  
### Return Value  
 The element value specified by the parameters.  
  
##  <a name="array__operator_at_operator"></a>  array::operator[] Operator  
 Returns the element that is at the specified index.  
  
```  
value_type & (operador) [] (const index \< _Rank > & _Index) restrict(amp,cpu);

 
[] de operador & value_type const (const index \< _Rank > & _Index) restrict(amp,cpu) const;

 
TypeName details::_Projection_result_type \< value_type, _Rank >:: operator _Result_type[](int _I) restrict(amp,cpu);

 
TypeName details::_Projection_result_type \< value_type, _Rank >:: operator _Const_result_type[](int _I) restrict(amp,cpu) const;
```  
  
### Parameters  
 `_Index`  
 The index.  
  
 `_I`  
 The index.  
  
### Return Value  
 The element that is at the specified index.  
  
##  <a name="array__operator_eq_operator"></a>  array::operator= Operator  
 Copies the contents of the specified [array](../../../parallel/amp/reference/array-class.md) object.  
  
```  
operador & matriz = (matriz & _Other const) Restrict (CPU);

 
operador & matriz = (matriz & & _Other) Restrict (CPU);

 
operador & matriz = (const array_view \< value_type const, _Rank > & _Src) Restrict (CPU);
```  
  
### Parameters  
 `_Other`  
 The `array` object to copy from.  
  
 `_Src`  
 The `array` object to copy from.  
  
### Return Value  
 A reference to this `array` object.  
  
##  <a name="array__rank_constant"></a>  array::rank Constant  
 Stores the rank of the [array](../../../parallel/amp/reference/array-class.md).  
  
```  
rango de int const estáticos = _Rank;  
```  
  
##  <a name="array__section_method"></a>  array::section Method  
 Returns a subsection of the [array](../../../parallel/amp/reference/array-class.md) object that is at the specified origin and, optionally, that has the specified extent.  
  
```  
array_view \< value_type, _Rank > sección (const Concurrency::index \< _Rank > & _Section_origin,  
    Const Concurrency::extent \< _Rank > & _Section_extent) restrict(amp,cpu);

 
array_view \< value_type const, _Rank > sección (const Concurrency::index \< _Rank > & _Section_origin,  
    Const Concurrency::extent \< _Rank > & _Section_extent) restrict(amp,cpu) const;

 
array_view \< value_type, _Rank > sección (const Concurrency::extent \< _Rank > & _Ext) restrict(amp,cpu);

 
array_view \< value_type const, _Rank > sección (const Concurrency::extent \< _Rank > & _Ext) restrict(amp,cpu) const;

 
array_view \< value_type, _Rank > sección (const index \< _Rank > & _Idx) restrict(amp,cpu);

 
array_view \< value_type const, _Rank > sección (const index \< _Rank > & _Idx) restrict(amp,cpu) const;

 
array_view \< value_type 1 > sección (_I0 int,  
    restrict(amp,cpu) _E0 int);

 
array_view \< const value_type, 1 > sección (_I0 int,  
    int _E0) restrict(amp,cpu) const;

 
array_view \< value_type, 2 > sección (_I0 int,  
    _I1 int,  
    _E0 int,  
    restrict(amp,cpu) _E1 int);

 
array_view \< const value_type, 2 > sección (_I0 int,  
    _I1 int,  
    _E0 int,  
    int _E1) restrict(amp,cpu) const;

 
array_view \< value_type 3 > sección (_I0 int,  
    _I1 int,  
    _I2 int,  
    _E0 int,  
    _E1 int,  
    restrict(amp,cpu) _E2 int);

 
array_view \< const value_type, 3 > sección (_I0 int,  
    _I1 int,  
    _I2 int,  
    _E0 int,  
    _E1 int,  
    int _E2) restrict(amp,cpu) const;
```  
  
### Parameters  
 `_E0`  
 The most significant component of the extent of this section.  
  
 `_E1`  
 The next-to-most-significant component of the extent of this section.  
  
 `_E2`  
 The least significant component of the extent of this section.  
  
 `_Ext`  
 The [extent](../../../parallel/amp/reference/extent-class-cpp-amp.md) object that specifies the extent of the section. The origin is 0.  
  
 `_Idx`  
 The [index](../../../parallel/amp/reference/index-class.md) object that specifies the location of the origin. The subsection is the rest of the extent.  
  
 `_I0`  
 The most significant component of the origin of this section.  
  
 `_I1`  
 The next-to-most-significant component of the origin of this section.  
  
 `_I2`  
 The least significant component of the origin of this section.  
  
 `_Rank`  
 The rank of the section.  
  
 `_Section_extent`  
 The [extent](../../../parallel/amp/reference/extent-class-cpp-amp.md) object that specifies the extent of the section.  
  
 `_Section_origin`  
 The [index](../../../parallel/amp/reference/index-class.md) object that specifies the location of the origin.  
  
 `value_type`  
 The data type of the elements that are copied.  
  
### Return Value  
 Returns a subsection of the `array` object that is at the specified origin and, optionally, that has the specified extent. When only the `index` object is specified, the subsection contains all elements in the associated grid that have indexes that are larger than the indexes of the elements in the `index` object.  
  
##  <a name="array__view_as_method"></a>  array::view_as Method  
 Reinterprets this array as an [array_view](../../../parallel/amp/reference/array-view-class.md) of a different rank.  
  
```  
plantilla \< int _New_rank  
>  
array_view \< value_type, _New_rank > view_as (const Concurrency::extent \< _New_rank > & _View_extent) restrict(amp,cpu);

 
plantilla \< int _New_rank  
>  
array_view \< value_type const, _New_rank > view_as (const Concurrency::extent \< _New_rank > & _View_extent) restrict(amp,cpu) const;
```  
  
### Parameters  
 `_New_rank`  
 The rank of the `extent` object passed as a parameter.  
  
 `_View_extent`  
 The extent that is used to construct the new [array_view](../../../parallel/amp/reference/array-view-class.md) object.  
  
 `value_type`  
 The data type of the elements in both the original [array](../../../parallel/amp/reference/array-class.md) object and the returned `array_view` object.  
  
### Return Value  
 The [array_view](../../../parallel/amp/reference/array-view-class.md) object that is constructed.  
  
## See Also  
 [Concurrency Namespace (C++ AMP)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
