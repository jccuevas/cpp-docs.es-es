---
title: "array_view (Clase) | Microsoft Docs"
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
  - "amp/Concurrency::array_view"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array_view (clase)"
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# array_view (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa una vista de N dimensiones sobre los datos contenidos en otro contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <
    typename value_type,  
    int _Rank = 1  
>  
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;  
 
template <
    typename value_type,  
    int _Rank  
>  
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value_type`  
 El tipo de datos de los elementos de la `array_view` objeto.  
  
 `_Rank`  
 El rango de la `array_view` objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor de array_view::array_view](#array_view__array_view_constructor)|Inicializa una nueva instancia de la clase `array_view`. No hay ningún constructor predeterminado para `array<T,N>`. Todos los constructores están restringidos para ejecutarse en la CPU y no se puede ejecutar en un destino de Direct3D.|  
|[array_view:: ~ array_view (destructor)](#array_view___dtorarray_view_destructor)|Destruye el objeto `array_view`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[array_view:: copy_to (método)](#array_view__copy_to_method)|Copia el contenido de la `array_view` objeto en el destino especificado mediante una llamada a `copy(*this, dest)`.|  
|[array_view:: Data (método)](#array_view__data_method)|Devuelve un puntero a los datos sin procesar de la `array_view`.|  
|[array_view:: discard_data (método)](#array_view__discard_data_method)|Descarta los datos actuales subyacentes de esta vista.|  
|[array_view:: get_extent (método)](#array_view__get_extent_method)|Devuelve el objeto de extensión del objeto array_view.|  
|[array_view:: get_ref (método)](#array_view__get_ref_method)|Devuelve una referencia al elemento indizado.|  
|[array_view:: get_source_accelerator_view (método)](#array_view__get_source_accelerator_view_method)|Devuelve el [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) donde el origen de datos de la `array_view` se encuentra.|  
|[array_view:: Refresh (método)](#array_view__refresh_method)|Notifica a la `array_view` objeto que su memoria enlazado se ha modificado fuera de la `array_view` interfaz. Una llamada a este método procesa toda la información almacenada en caché obsoletos.|  
|[array_view:: reinterpret_as (método)](#array_view__reinterpret_as_method)|Devuelve una matriz unidimensional que contiene todos los elementos de la `array_view` objeto.|  
|[array_view:: Section (método)](#array_view__section_method)|Devuelve una subsección de la `array_view` objeto en el origen especificado y, opcionalmente, que tiene la extensión especificada.|  
|[array_view:: Synchronize (método)](#array_view__synchronize_method)|Sincroniza las modificaciones realizadas en el `array_view` objeto a su origen de datos.|  
|[array_view:: synchronize_async (método)](#array_view__synchronize_async_method)|Sincroniza de forma asincrónica las modificaciones realizadas en el [array_view](../../../parallel/amp/reference/array-view-class.md) objeto a su origen de datos.|  
|[array_view:: synchronize_to (método)](#array_view__synchronize_to_method)|Sincroniza las modificaciones realizadas en el `array_view` objeto especificado [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md).|  
|[array_view:: synchronize_to_async (método)](#array_view__synchronize_to_async_method)|Sincroniza de forma asincrónica las modificaciones realizadas en el `array_view` objeto especificado [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md).|  
|[array_view:: view_as (método)](#array_view__view_as_method)|Genera un `array_view` objeto de un rango diferente con este `array_view` datos del objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[array_view::operator() () (operador)](#array_view__operator___operator)|Devuelve el valor del elemento especificado por el parámetro o los parámetros.|  
|[array_view:: operator [] (operador)](#array_view__operator_at_operator)|Devuelve el elemento especificado por los parámetros.|  
|[array_view:: operator = (operador)](#array_view__operator_eq_operator)|Copia el contenido del elemento `array_view` objeto en éste.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[array_view::Rank (constante)](#array_view__rank_constant)|Almacena el rango de la `array_view` objeto.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Miembro de datos de array_view::extent](#array_view__extent_data_member)|Obtiene el objeto `extent` que define la forma del objeto `array_view`.|  
|[Miembro de datos de array_view::source_accelerator_view](#array_view__source_accelerator_view_data_member)|Obtiene el [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) donde el origen de datos de la `array_view` se encuentra|  
|[Miembro de datos de array_view::value_type](#array_view__value_type_data_member)|El tipo de valor de la `array_view` y la matriz dependiente.|  
  
## <a name="remarks"></a>Comentarios  
 La `array_view` clase representa una vista de los datos que se encuentran en un [matriz](../../../parallel/amp/reference/array-class.md) objeto o una subsección de un `array` objeto.  
  
 Puede tener acceso a la `array_view` objeto donde se encuentran los datos de origen (local) o en un acelerador de diferentes o en un dominio de coherencia (remota). Cuando se accede al objeto de forma remota, vistas se copian y almacenan en caché según sea necesario. Excepto los efectos del almacenamiento en caché automático, `array_view` objetos tienen un perfil de rendimiento similar de `array` objetos. Hay una penalización de rendimiento cuando tiene acceso a los datos a través de vistas.  
  
 Hay tres escenarios de uso remoto:  
  
-   Una vista a un puntero de memoria del sistema se pasa por medio de un [parallel_for_each](concurrency%20namespace%20functions.md#parallel_for_each) la llamada a una tecla de aceleración y tener acceso en el acelerador.  
  
-   Una vista a una matriz que se encuentra en un acelerador se pasa por medio de un `parallel_for_each` la llamada a otro acelerador y se tiene acceso no existe.  
  
-   Se tiene acceso a una vista a una matriz que se encuentra en un acelerador de la CPU.  
  
 En cualquiera de estos escenarios, se copian las vistas que se hace referencia en tiempo de ejecución a la ubicación remota y, si modifica las llamadas a la `array_view` de objeto, se copian a la ubicación local. El tiempo de ejecución podría optimizar el proceso de copia de cambios, puede copiar sólo los elementos cambiados o puede copiar partes sin cambios también. Superposición de `array_view` no se garantiza que los objetos en un origen de datos para mantener la integridad referencial en una ubicación remota.  
  
 Debe sincronizar el acceso multiproceso al mismo origen de datos.  
  
 El tiempo de ejecución realiza las siguientes garantías sobre el almacenamiento en caché de datos en `array_view` objetos:  
  
-   Todos los accesos a bien sincronizados para un `array` objeto y un `array_view` objeto en él en el orden del programa siguen una serie ocurre-antes de la relación.  
  
-   Todos los accesos a bien sincronizados en superpuestas `array_view` objetos en el Acelerador de la mismo en un único `array` objeto tienen como alias a través de la `array` objeto. Crearán un total tiene lugar-antes de la relación que obedece el orden del programa. No hay ningún almacenamiento en caché. Si el `array_view` objetos se ejecutan en diferentes aceleradores, el orden de acceso es indefinido, crear una condición de carrera.  
  
 Cuando se crea un `array_view` objeto mediante un puntero de memoria del sistema, debe cambiar la vista `array_view` sólo a través del objeto del `array_view` puntero. También debe llamar a `refresh()` en uno de los `array_view` objetos que se adjuntan al puntero de sistema, si la memoria nativa subyacente se modifica directamente, en lugar de a través del `array_view` objeto.  
  
 Notifica cualquiera de estas acciones el `array_view` de objetos que se cambia la memoria nativa subyacente y que todas las copias que se encuentran en un acelerador no están actualizadas. Si sigue estas instrucciones, las vistas basadas en punteros son idénticas a las proporcionadas a las vistas de matrices de datos en paralelo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Array_view_shape`  
  
 `_Array_view_base`  
  
 `array_view`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  
  
##  <a name="a-namearrayviewdtorarrayviewdestructora-arrayviewarrayview-destructor"></a><a name="array_view___dtorarray_view_destructor"></a>  array_view:: ~ array_view (destructor)  
 Destruye el [array_view](../../../parallel/amp/reference/array-view-class.md) objeto.  
  
```  
~array_view()restrict(amp,cpu);
```  
  
##  <a name="a-namearrayviewarrayviewconstructora-arrayviewarrayview-constructor"></a><a name="array_view__array_view_constructor"></a>  Constructor de array_view::array_view  
 Inicializa una nueva instancia de la [array_view](../../../parallel/amp/reference/array-view-class.md) clase.  
  
```  
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view& _Other)restrict(amp,cpu);

 
explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

 
template <
    typename _Container  
>  
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    _Container& _Src) restrict(cpu);

 
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    value_type* _Src)restrict(amp,cpu);

 
explicit array_view(
    int _E0) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    _Container& _Src,  
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    _Container& _Src) restrict(cpu);

 
explicit array_view(
    int _E0,  
    int _E1) __CPU_ONLY;  
 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    int _E1,  
    _Container& _Src) restrict(cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2) __CPU_ONLY;  
 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    _Container& _Src);

 
explicit array_view(
    int _E0,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
template <
    typename _Arr_type,  
    int _Size  
>  
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

 
template <
    typename _Container  
>  
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    const _Container& _Src) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    const _Container& _Src,  
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

 
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    const value_type* _Src)restrict(amp,cpu);

 
template <
    typename _Arr_type,  
    int _Size  
>  
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    const _Container& _Src);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    int _E1,  
    const _Container& _Src);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    const _Container& _Src);

 
array_view(
    int _E0,  
    const value_type* _Src)restrict(amp,cpu);

 
array_view(
    int _E0,  
    int _E1,  
    const value_type* _Src) restrict(amp,cpu);

 
array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    const value_type* _Src) restrict(amp,cpu);

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Arr_type`  
 El tipo de elemento de una matriz de estilo C desde el que se suministran datos.  
  
 `_Container`  
 Un argumento de plantilla que se debe especificar un contenedor lineal que admite `data()` y `size()` los miembros.  
  
 `_E0`  
 El componente más importante de la extensión de esta sección.  
  
 `_E1`  
 El componente siguiente-a-más significativo de la extensión de esta sección.  
  
 `_E2`  
 El componente menos significativo de la extensión de esta sección.  
  
 `_Extent`  
 La extensión de cada dimensión de este `array_view`.  
  
 `_Other`  
 Un objeto de tipo `array_view<T,N>` desde la que se va a inicializar la nueva `array_view`.  
  
 `_Size`  
 El tamaño de una matriz de estilo C desde el que se suministran datos.  
  
 `_Src`  
 Un puntero al origen de datos que se copiarán en la nueva matriz.  
  
##  <a name="a-namearrayviewcopytomethoda-arrayviewcopyto-method"></a><a name="array_view__copy_to_method"></a>  array_view:: copy_to (método)  
 Copia el contenido de la [array_view](../../../parallel/amp/reference/array-view-class.md) objeto con el objeto de destino especificado mediante una llamada a `copy(*this, dest)`.  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const;

 
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Objeto que se va a copiar a.  
  
##  <a name="a-namearrayviewdatamethoda-arrayviewdata-method"></a><a name="array_view__data_method"></a>  array_view:: Data (método)  
 Devuelve un puntero a los datos sin procesar de la [array_view](../../../parallel/amp/reference/array-view-class.md).  
  
```  
value_type* data() const restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a los datos sin procesar de la `array_view`.  
  
##  <a name="a-namearrayviewdiscarddatamethoda-arrayviewdiscarddata-method"></a><a name="array_view__discard_data_method"></a>  array_view:: discard_data (método)  
 Descarta los datos actuales subyacentes de esta vista. Se trata de una sugerencia de optimización al tiempo de ejecución utilizado para evitar copiar el contenido actual de la vista a un destino `accelerator_view` que se tiene acceso en y se recomienda su uso si el contenido existente no es necesaria. Este método es una operación inefectiva cuando se utiliza en un contexto Restrict (amp)  
  
```  
void discard_data() const restrict(cpu);
```  
  
##  <a name="a-namearrayviewextentdatamembera-arrayviewextent-data-member"></a><a name="array_view__extent_data_member"></a>  Miembro de datos de array_view::extent  
 Obtiene el objeto `extent` que define la forma del objeto `array_view`.  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="a-namearrayviewgetextentmethoda-arrayviewgetextent-method"></a><a name="array_view__get_extent_method"></a>  array_view:: get_extent (método)  
 Devuelve el [extensión](../../../parallel/amp/reference/extent-class-cpp-amp.md) objeto de la [array_view](../../../parallel/amp/reference/array-view-class.md) objeto.  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```  
  
### <a name="return-value"></a>Valor devuelto  
 La `extent` objeto de la `array_view` objeto  
  
##  <a name="a-namearrayviewgetrefmethoda-arrayviewgetref-method"></a><a name="array_view__get_ref_method"></a>  array_view:: get_ref (método)  
 Obtenga una referencia al elemento indizado por _Index. A diferencia de los otros operadores de indización para obtener acceso a la array_view en la CPU, este método no implícitamente sincronizar el contenido de esta array_view a la CPU. Después de obtener acceso a la array_view en una ubicación remota o realizar una operación de copia que implica este array_view usuarios son responsables a sincronizar explícitamente el array_view a la CPU antes de llamar a este método. Si no se hace así, se producirá un comportamiento indefinido.  
  
```  
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 Índice.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al elemento indizado por _Index  
  
##  <a name="a-namearrayviewgetsourceacceleratorviewmethoda-arrayviewgetsourceacceleratorview-method"></a><a name="array_view__get_source_accelerator_view_method"></a>  array_view:: get_source_accelerator_view (método)  
 Devuelve el accelerator_view donde se encuentra el origen de datos de la array_view. Si la array_view no tiene un origen de datos, esta API produce un runtime_exception  
  
```  
accelerator_view get_source_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-namearrayviewoperatoroperatora-arrayviewoperator-operator"></a><a name="array_view__operator___operator"></a>  array_view::operator() () (operador)  
 Devuelve el valor del elemento especificado por el parámetro o los parámetros.  
  
```  
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

 
typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

 
value_type& operator() (
    int _I0,  
    int _I1) const restrict(amp,cpu);

 
value_type& operator() (
    int _I0,  
    int _I1,  
    int _I2) const restrict(amp,cpu);

 
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 La ubicación del elemento.  
  
 `_I0`  
 El índice de la primera dimensión.  
  
 `_I1`  
 Índice de la segunda dimensión.  
  
 `_I2`  
 Índice de la tercera dimensión.  
  
 `_I`  
 La ubicación del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor del elemento especificado por el parámetro o los parámetros.  
  
##  <a name="a-namearrayviewoperatoratoperatora-arrayviewoperator-operator"></a><a name="array_view__operator_at_operator"></a>  array_view:: operator [] (operador)  
 Devuelve el elemento especificado por los parámetros.  
  
```  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

 
value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 Índice.  
  
 `_I`  
 Índice.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor del elemento en el índice, o un `array_view` proyectados en la dimensión más significativo.  
  
##  <a name="a-namearrayviewoperatoreqoperatora-arrayviewoperator-operator"></a><a name="array_view__operator_eq_operator"></a>  array_view:: operator = (operador)  
 Copia el contenido del elemento [array_view](../../../parallel/amp/reference/array-view-class.md) objeto a ésta.  
  
```  
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

 
array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `array_view` objeto que se va a copiar de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `array_view` objeto.  
  
##  <a name="a-namearrayviewrankconstanta-arrayviewrank-constant"></a><a name="array_view__rank_constant"></a>  array_view::Rank (constante)  
 Almacena el rango de la [array_view](../../../parallel/amp/reference/array-view-class.md) objeto.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="a-namearrayviewrefreshmethoda-arrayviewrefresh-method"></a><a name="array_view__refresh_method"></a>  array_view:: Refresh (método)  
 Notifica a la [array_view](../../../parallel/amp/reference/array-view-class.md) objeto que su memoria enlazado se ha modificado fuera de la `array_view` interfaz. Una llamada a este método procesa toda la información almacenada en caché obsoletos.  
  
```  
void refresh() const restrict(cpu);
```  
  
##  <a name="a-namearrayviewsectionmethoda-arrayviewsection-method"></a><a name="array_view__section_method"></a>  array_view:: Section (método)  
 Devuelve una subsección de la [array_view](../../../parallel/amp/reference/array-view-class.md) objeto que está en el origen especificado y, opcionalmente, que tiene la extensión especificada.  
  
```  
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,  
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

 
array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

 
array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _E0) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _I1,  
    int _E0,  
    int _E1) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _I1,  
    int _I2,  
    int _E0,  
    int _E1,  
    int _E2) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_E0`  
 El componente más importante de la extensión de esta sección.  
  
 `_E1`  
 El componente siguiente-a-más significativo de la extensión de esta sección.  
  
 `_E2`  
 El componente menos significativo de la extensión de esta sección.  
  
 `_Ext`  
 El [extensión](../../../parallel/amp/reference/extent-class-cpp-amp.md) objeto que especifica la extensión de la sección. El origen es 0.  
  
 `_Idx`  
 El [índice](../../../parallel/amp/reference/index-class.md) objeto que especifica la ubicación del origen. La subsección es el resto de la extensión.  
  
 `_I0`  
 El componente más importante del origen de esta sección.  
  
 `_I1`  
 El componente siguiente-a-más significativo del origen de esta sección.  
  
 `_I2`  
 El componente menos significativo del origen de esta sección.  
  
 `_Rank`  
 El rango de la sección.  
  
 `_Section_extent`  
 El [extensión](../../../parallel/amp/reference/extent-class-cpp-amp.md) objeto que especifica la extensión de la sección.  
  
 `_Section_origin`  
 El [índice](../../../parallel/amp/reference/index-class.md) objeto que especifica la ubicación del origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Una subsección de la `array_view` objeto en el origen especificado y, opcionalmente, que tiene la extensión especificada. Cuando sólo el `index` se especifica el objeto, la subsección contiene todos los elementos de la extensión asociada que tienen índices que son más grandes que los índices de los elementos de la `index` objeto.  
  
##  <a name="a-namearrayviewsourceacceleratorviewdatamembera-arrayviewsourceacceleratorview-data-member"></a><a name="array_view__source_accelerator_view_data_member"></a>  Miembro de datos de array_view::source_accelerator_view  
 Obtiene el accelerator_view de origen que está asociado este array_view.  
  
```  
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;  
```  
  
##  <a name="a-namearrayviewsynchronizemethoda-arrayviewsynchronize-method"></a><a name="array_view__synchronize_method"></a>  array_view:: Synchronize (método)  
 Sincroniza las modificaciones realizadas en el `array_view` objeto a su origen de datos.  
  
```  
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize() const restrict(cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Access_type`  
 El destino [access_type ()](concurrency%20namespace%20enums.md#access_type) en el destino [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md). Este parámetro tiene un valor predeterminado de `access_type_read`.  
  
##  <a name="a-namearrayviewsynchronizeasyncmethoda-arrayviewsynchronizeasync-method"></a><a name="array_view__synchronize_async_method"></a>  array_view:: synchronize_async (método)  
 Sincroniza de forma asincrónica las modificaciones realizadas en el [array_view](../../../parallel/amp/reference/array-view-class.md) objeto a su origen de datos.  
  
```  
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_async() const restrict(cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Access_type`  
 El destino [access_type ()](concurrency%20namespace%20enums.md#access_type) en el destino [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md). Este parámetro tiene un valor predeterminado de `access_type_read`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un futuro en la que se espere que se complete la operación.  
  
##  <a name="a-namearrayviewsynchronizetomethoda-arrayviewsynchronizeto-method"></a><a name="array_view__synchronize_to_method"></a>  array_view:: synchronize_to (método)  
 Sincroniza las modificaciones realizadas en esta array_view para el accelerator_view especificado.  
  
```  
void synchronize_to(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Accl_view`  
 Accelerator_view de destino para sincronizar.  
  
 `_Access_type`  
 Parámetro de access_type deseado en el accelerator_view de destino. Este parámetro tiene un valor predeterminado de access_type_read.  
  
##  <a name="a-namearrayviewsynchronizetoasyncmethoda-arrayviewsynchronizetoasync-method"></a><a name="array_view__synchronize_to_async_method"></a>  array_view:: synchronize_to_async (método)  
 Asincrónicamente sincroniza las modificaciones realizadas en esta array_view para el accelerator_view especificado.  
  
```  
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Accl_view`  
 Accelerator_view de destino para sincronizar.  
  
 `_Access_type`  
 Parámetro de access_type deseado en el accelerator_view de destino. Este parámetro tiene un valor predeterminado de access_type_read.  
  
### <a name="return-value"></a>Valor devuelto  
 Un futuro en la que se espere que se complete la operación.  
  
##  <a name="a-namearrayviewvaluetypedatamembera-arrayviewvaluetype-data-member"></a><a name="array_view__value_type_data_member"></a>  Miembro de datos de array_view::value_type  
 El tipo de valor de la array_view y la matriz dependiente.  
  
```  
typedef typenamevalue_type value_type;  
```  
  
##  <a name="a-namearrayviewviewasmethoda-arrayviewviewas-method"></a><a name="array_view__view_as_method"></a>  array_view:: view_as (método)  
 Esto vuelve a interpretar `array_view` como un `array_view` de un rango diferente.  
  
```  
template <
    int _New_rank  
>  
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

 
template <
    int _New_rank  
>  
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_New_rank`  
 El rango del nuevo `array_view` objeto.  
  
 `_View_extent`  
 Cambiar la forma `extent`.  
  
 `value_type`  
 El tipo de datos de los elementos de la original [matriz](../../../parallel/amp/reference/array-class.md) objeto y el valor devuelto `array_view` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 El [array_view](../../../parallel/amp/reference/array-view-class.md) objeto construido.  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
