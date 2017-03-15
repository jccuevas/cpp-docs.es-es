---
title: array_view (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::array_view
dev_langs:
- C++
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
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
ms.openlocfilehash: ec096dbcd485b9360d07d1b56511b13c13d1b4cf
ms.lasthandoff: 02/24/2017

---
# <a name="arrayview-class"></a>array_view (Clase)
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
|[array_view (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `array_view`. No hay ningún constructor predeterminado para `array<T,N>`. Todos los constructores están restringidos para ejecutarse en la CPU y no se puede ejecutar en un destino de Direct3D.|  
|[~ array_view (destructor)](#ctor)|Destruye el objeto `array_view`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[copy_to (método)](#copy_to)|Copia el contenido de la `array_view` objeto en el destino especificado mediante una llamada a `copy(*this, dest)`.|  
|[datos (método)](#data)|Devuelve un puntero a los datos sin procesar de la `array_view`.|  
|[discard_data (método)](#discard_data)|Descarta los datos actuales subyacentes de esta vista.|  
|[get_extent (método)](#get_extent)|Devuelve el objeto de extensión del objeto array_view.|  
|[get_ref (método)](#get_ref)|Devuelve una referencia al elemento indizado.|  
|[get_source_accelerator_view (método)](#get_source_accelerator_view)|Devuelve el [accelerator_view](accelerator-view-class.md) donde el origen de datos de la `array_view` se encuentra.|  
|[Método Refresh](#refresh)|Notifica a la `array_view` objeto que su memoria enlazado se ha modificado fuera de la `array_view` interfaz. Una llamada a este método procesa toda la información almacenada en caché obsoletos.|  
|[reinterpret_as (método)](#reinterpret_as)|Devuelve una matriz unidimensional que contiene todos los elementos de la `array_view` objeto.|  
|[sección (método)](#section)|Devuelve una subsección de la `array_view` objeto en el origen especificado y, opcionalmente, que tiene la extensión especificada.|  
|[Synchronize (método)](#synchronize)|Sincroniza las modificaciones realizadas en el `array_view` objeto a su origen de datos.|  
|[synchronize_async (método)](#synchronize_async)|Sincroniza de forma asincrónica las modificaciones realizadas en el `array_view` objeto a su origen de datos.|  
|[synchronize_to (método)](#synchronize_to)|Sincroniza las modificaciones realizadas en el `array_view` objeto especificado [accelerator_view](accelerator-view-class.md).|  
|[synchronize_to_async (método)](#synchronize_to_async)|Sincroniza de forma asincrónica las modificaciones realizadas en el `array_view` objeto especificado [accelerator_view](accelerator-view-class.md).|  
|[view_as (método)](#view_as)|Genera un `array_view` objeto de un rango diferente con este `array_view` datos del objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Operator() (operador)](#operator_call)|Devuelve el valor del elemento especificado por el parámetro o los parámetros.|  
|[operator [] (operador)](#operator_at)|Devuelve el elemento especificado por los parámetros.|  
|[operador = (operador)](#operator_eq)|Copia el contenido del elemento `array_view` objeto en éste.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Rank (constante)](#rank)|Almacena el rango de la `array_view` objeto.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Miembro de datos de medida](#extent)|Obtiene el objeto `extent` que define la forma del objeto `array_view`.|  
|[Miembro de datos de source_accelerator_view](#source_accelerator_view)|Obtiene el [accelerator_view](accelerator-view-class.md) donde el origen de datos de la `array_view` se encuentra|  
|[Miembro de datos de value_type](#value_type)|El tipo de valor de la `array_view` y la matriz dependiente.|  
  
## <a name="remarks"></a>Comentarios  
 El `array_view` clase representa una vista de los datos que se encuentran en un [matriz](array-class.md) objeto o una subsección de un `array` objeto.  
  
 Puede tener acceso a la `array_view` objeto donde se encuentran los datos de origen (local) o en un acelerador de diferentes o en un dominio de coherencia (remota). Cuando se accede al objeto de forma remota, vistas se copian y almacenan en caché según sea necesario. Excepto los efectos del almacenamiento en caché automático, `array_view` objetos tienen un perfil de rendimiento similar de `array` objetos. Hay una penalización de rendimiento cuando tiene acceso a los datos a través de vistas.  
  
 Hay tres escenarios de uso remoto:  
  
-   Una vista a un puntero de memoria del sistema se pasa por medio de un [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each) la llamada a una tecla de aceleración y tener acceso en el acelerador.  
  
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
  
##  <a name="a-namedtora-arrayview"></a><a name="dtor"></a>~ array_view 

 Destruye el objeto `array_view`.  
  
```  
~array_view()restrict(amp,cpu);
```  
  
##  <a name="a-namectora-arrayview"></a><a name="ctor"></a>array_view 

 Inicializa una nueva instancia de la clase `array_view`.  
  
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
  
##  <a name="a-namecopytoa-copyto"></a><a name="copy_to"></a>copy_to 

 Copia el contenido de la `array_view` objeto con el objeto de destino especificado mediante una llamada a `copy(*this, dest)`.  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const;

 
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Objeto que se va a copiar a.  
  
##  <a name="a-namedataa-data"></a><a name="data"></a>datos 

 Devuelve un puntero a los datos sin procesar de la `array_view`.  
  
```  
value_type* data() const restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a los datos sin procesar de la `array_view`.  
  
##  <a name="a-namediscarddataa-discarddata"></a><a name="discard_data"></a>discard_data 

 Descarta los datos actuales subyacentes de esta vista. Se trata de una sugerencia de optimización al tiempo de ejecución utilizado para evitar copiar el contenido actual de la vista a un destino `accelerator_view` que se tiene acceso en y se recomienda su uso si el contenido existente no es necesaria. Este método es una operación inefectiva cuando se utiliza en un contexto Restrict (amp)  
  
```  
void discard_data() const restrict(cpu);
```  
  
##  <a name="a-nameextenta-extent"></a><a name="extent"></a>extensión 

 Obtiene el objeto `extent` que define la forma del objeto `array_view`.  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="a-namegetextenta-getextent"></a><a name="get_extent"></a>get_extent 

 Devuelve el [punto](extent-class.md) objeto de la `array_view` objeto.  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `extent` objeto de la `array_view` objeto  
  
##  <a name="a-namegetrefa-getref"></a><a name="get_ref"></a>get_ref 

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
  
##  <a name="a-namegetsourceacceleratorviewa-getsourceacceleratorview"></a><a name="get_source_accelerator_view"></a>get_source_accelerator_view 

 Devuelve el accelerator_view donde se encuentra el origen de datos de la array_view. Si la array_view no tiene un origen de datos, esta API produce un runtime_exception  
  
```  
accelerator_view get_source_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-nameoperatorcalla-operator"></a><a name="operator_call"></a>Operator() 

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
  
##  <a name="a-nameoperatorata-operator"></a><a name="operator_at"></a>operator] 

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
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

 Copia el contenido del elemento `array_view` objeto a ésta.  
  
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
  
##  <a name="a-nameranka-rank"></a><a name="rank"></a>rango 

 Almacena el rango de la `array_view` objeto.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="a-namerefresha-refresh"></a><a name="refresh"></a>actualización 

 Notifica a la `array_view` objeto que su memoria enlazado se ha modificado fuera de la `array_view` interfaz. Una llamada a este método procesa toda la información almacenada en caché obsoletos.  
  
```  
void refresh() const restrict(cpu);
```  
## <a name="a-namereinterpretasa-reinterpretas"></a><a name="reinterpret_as"></a>reinterpret_as 

Reinterpreta los array_view a través de un array_view unidimensional, que opcionalmente puede tener un tipo de valor diferente que el array_view de origen.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template <  
    typename _Value_type2  
>  
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);  
  
template <  
    typename _Value_type2  
>  
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Value_type2`  
 El tipo de datos del nuevo `array_view` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `array_view` objeto o const `array_view` objeto basado en este `array_view`, con el tipo de elemento convertido a partir de `T` a `_Value_type2`, y reduce el rango de *N* en 1.  
  
### <a name="remarks"></a>Comentarios  
 A veces es conveniente ver una matriz multidimensional como una matriz unidimensional lineal, lo que puede tener un tipo de valor diferente de la matriz de origen. Puede lograr esto en un `array_view` mediante este método.  
  
**Advertencia** Reinterpeting un objeto array_view con un tipo de valor distinto es una operación potencialmente insegura. Esta funcionalidad se debe utilizar con cuidado.  
  
 Por ejemplo:  
  
```cpp  
struct RGB { float r; float g; float b; };  
  
array<RGB,3>  a = ...;   
array_view<float,1> v = a.reinterpret_as<float>();   
  
assert(v.extent == 3*a.extent);  
```  
    
##  <a name="a-namesectiona-section"></a><a name="section"></a>sección 

 Devuelve una subsección de la `array_view` objeto en el origen especificado y, opcionalmente, que tiene la extensión especificada.  
  
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
 El [extensión](extent-class.md) objeto que especifica la extensión de la sección. El origen es 0.  
  
 `_Idx`  
 El [índice](index-class.md) objeto que especifica la ubicación del origen. La subsección es el resto de la extensión.  
  
 `_I0`  
 El componente más importante del origen de esta sección.  
  
 `_I1`  
 El componente siguiente-a-más significativo del origen de esta sección.  
  
 `_I2`  
 El componente menos significativo del origen de esta sección.  
  
 `_Rank`  
 El rango de la sección.  
  
 `_Section_extent`  
 El [extensión](extent-class.md) objeto que especifica la extensión de la sección.  
  
 `_Section_origin`  
 El [índice](index-class.md) objeto que especifica la ubicación del origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Una subsección de la `array_view` objeto en el origen especificado y, opcionalmente, que tiene la extensión especificada. Cuando sólo el `index` se especifica el objeto, la subsección contiene todos los elementos de la extensión asociada que tienen índices que son más grandes que los índices de los elementos de la `index` objeto.  
  
##  <a name="a-namesourceacceleratorviewa-sourceacceleratorview"></a><a name="source_accelerator_view"></a>source_accelerator_view 

 Obtiene el accelerator_view de origen que está asociado este array_view.  
  
```  
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;  
```  
  
##  <a name="a-namesynchronizea-synchronize"></a><a name="synchronize"></a>sincronizar 

 Sincroniza las modificaciones realizadas en el `array_view` objeto a su origen de datos.  
  
```  
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize() const restrict(cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Access_type`  
 El destino [access_type ()](concurrency-namespace-enums-amp.md#access_type) en el destino [accelerator_view](accelerator-view-class.md). Este parámetro tiene un valor predeterminado de `access_type_read`.  
  
##  <a name="a-namesynchronizeasynca-synchronizeasync"></a><a name="synchronize_async"></a>synchronize_async 

 Sincroniza de forma asincrónica las modificaciones realizadas en el `array_view` objeto a su origen de datos.  
  
```  
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_async() const restrict(cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Access_type`  
 El destino [access_type ()](concurrency-namespace-enums-amp.md#access_type) en el destino [accelerator_view](accelerator-view-class.md). Este parámetro tiene un valor predeterminado de `access_type_read`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un futuro en la que se espere que se complete la operación.  
  
##  <a name="a-namesynchronizetoa-synchronizeto"></a><a name="synchronize_to"></a>synchronize_to 

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
  
##  <a name="a-namesynchronizetoasynca-synchronizetoasync"></a><a name="synchronize_to_async"></a>synchronize_to_async 

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
  
##  <a name="a-namevaluetypea-valuetype"></a><a name="value_type"></a>value_type 

 El tipo de valor de la array_view y la matriz dependiente.  
  
```  
typedef typenamevalue_type value_type;  
```  
  
##  <a name="a-nameviewasa-viewas"></a><a name="view_as"></a>view_as 

 Esto reinterpreta `array_view` como un `array_view` de un rango diferente.  
  
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
 El tipo de datos de los elementos de la original [matriz](array-class.md) objeto y el valor devuelto `array_view` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 La `array_view` objeto construido.  
  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

