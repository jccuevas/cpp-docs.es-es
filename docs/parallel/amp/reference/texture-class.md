---
title: Texture (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics::texture
dev_langs:
- C++
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
caps.latest.revision: 9
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
ms.openlocfilehash: aafb23ac4d366baed37f1cf667984253160af9c3
ms.lasthandoff: 02/24/2017

---
# <a name="texture-class"></a>texture (Clase)
Una textura es un agregado de datos de un `accelerator_view` en el dominio de la extensión. Es una colección de variables, uno para cada elemento en un dominio de la extensión. Cada variable contiene un valor que corresponde al tipo primitivo de C++ ( `unsigned int`, `int`, `float`, `double`), un tipo escalar ( `norm`, o `unorm`), o un tipo de vector corto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
class texture;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value_type`  
 El tipo de los elementos de la textura.  
  
 `_Rank`  
 El rango de la textura.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`scalar_type`|Tipos escalares.|  
|`value_type`|Tipos de valor.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor de textura](#ctor)|Inicializa una nueva instancia de la clase `texture`.|  
|[~ texture (destructor)](#ctor)|Destruye el objeto `texture`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[copy_to (método)](#copy_to)|Copia la `texture` objeto en el destino, realice una copia en profundidad.|  
|[datos (método)](#data)|Devuelve un puntero de la CPU a los datos sin procesar de esta textura.|  
|[Get (método)](#get)|Devuelve el valor del elemento en el índice especificado.|  
|[get_associated_accelerator_view (método)](#get_associated_accelerator_view)|Devuelve el [accelerator_view](accelerator-view-class.md) que es el destino preferido para esta textura copiarse a.|  
|[get_depth_pitch (método)](#get_depth_pitch)|Devuelve el número de bytes entre cada segmento de profundidad en 3D ensayo textura en la CPU.|  
|[get_row_pitch (método)](#get_row_pitch)|Devuelve el número de bytes entre cada fila de una 2D o 3D ensayo textura en la CPU.|  
|[establecer (método)](#set)|Establece el valor del elemento en el índice especificado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Operator() (operador)](#operator_call)|Devuelve el valor del elemento especificado por los parámetros.|  
|[operator [] (operador)](#operator_at)|Devuelve el elemento situado en el índice especificado.|  
|[operador = (operador)](#operator_eq)|Copia especificado [textura](texture-class.md) objeto a ésta.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Rank (constante)](#rank)|Obtiene el rango de la `texture` objeto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[associated_accelerator_view miembro de datos](#associated_accelerator_view)|Obtiene el [accelerator_view](accelerator-view-class.md) que es el destino preferido para esta textura copiarse a.|  
|[Miembro de datos de depth_pitch](#depth_pitch)|Obtiene el número de bytes entre cada segmento de profundidad en una textura 3D de ensayo en la CPU.|  
|[Miembro de datos de row_pitch](#row_pitch)|Obtiene el número de bytes entre cada fila de una 2D o 3D ensayo textura en la CPU.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Texture_base`  
  
 `texture`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_graphics.h  
  
 **Namespace:** Graphics  
  
##  <a name="a-namedtora-texture"></a><a name="dtor"></a>~ textura 

 Destruye el objeto `texture`.  
  
```  
~texture() restrict(cpu);
```  
  
##  <a name="a-nameassociatedacceleratorviewa-associatedacceleratorview"></a><a name="associated_accelerator_view"></a>associated_accelerator_view 

 Obtiene el [accelerator_view](accelerator-view-class.md) que es el destino preferido para esta textura copiarse a.  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="a-namecopytoa-copyto"></a><a name="copy_to"></a>copy_to 

 Copia la `texture` objeto en el destino, realice una copia en profundidad.  
  
```  
void copy_to(
    texture& _Dest) const;

 
 
void copy_to(
    writeonly_texture_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Objeto que se va a copiar a.  
  
 `_Rank`  
 El rango de la textura.  
  
 `value_type`  
 El tipo de los elementos de la textura.  
  
##  <a name="a-namedataa-data"></a><a name="data"></a>datos 

 Devuelve un puntero de la CPU a los datos sin procesar de esta textura.  
  
```  
void* data() restrict(cpu);

 
const void* data() const restrict(cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a los datos sin procesar de la textura.  
  
##  <a name="a-namedepthpitcha-depthpitch"></a><a name="depth_pitch"></a>depth_pitch 

 Obtiene el número de bytes entre cada segmento de profundidad en una textura 3D de ensayo en la CPU.  
  
```  
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;  
```  
  
##  <a name="a-namegeta-get"></a><a name="get"></a>Obtener 

 Devuelve el valor del elemento en el índice especificado.  
  
```  
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 El índice del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor del elemento en el índice especificado.  
  
##  <a name="a-namegetassociatedacceleratorviewa-getassociatedacceleratorview"></a><a name="get_associated_accelerator_view"></a>get_associated_accelerator_view 

 Devuelve el accelerator_view que es el destino preferido para esta textura copiarse a.  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El [accelerator_view](accelerator-view-class.md) que es el destino preferido para esta textura copiarse a.  
  
##  <a name="a-namegetdepthpitcha-getdepthpitch"></a><a name="get_depth_pitch"></a>get_depth_pitch 

 Devuelve el número de bytes entre cada segmento de profundidad en 3D ensayo textura en la CPU.  
  
```  
unsigned int get_depth_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes entre cada segmento de profundidad en 3D ensayo textura en la CPU.  
  
##  <a name="a-namegetrowpitcha-getrowpitch"></a><a name="get_row_pitch"></a>get_row_pitch 

 Devuelve el número de bytes entre cada fila de una textura de ensayo 2 dimensiones o entre cada fila de un segmento de la profundidad de textura 3 dimensiones de almacenamiento provisional.  
  
```  
unsigned int get_row_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes entre cada fila de una textura de ensayo 2 dimensiones o entre cada fila de un segmento de la profundidad de textura 3 dimensiones de almacenamiento provisional.  
  
##  <a name="a-nameoperatorcalla-operator"></a><a name="operator_call"></a>Operator() 

 Devuelve el valor del elemento especificado por los parámetros.  
  
```  
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator() (
    int _I0) const restrict(amp);

 
const value_type operator() (
    int _I0,  
    int _I1) const restrict(amp);

 
const value_type operator() (
    int _I0,  
    int _I1,  
    int _I2) const restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 Índice.  
  
 `_I0`  
 El componente más significativo del índice.  
  
 `_I1`  
 El componente siguiente-a-más significativo del índice.  
  
 `_I2`  
 El componente menos significativos del índice.  
  
 `_Rank`  
 El rango del índice.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor del elemento especificado por los parámetros.  
  
##  <a name="a-nameoperatorata-operator"></a><a name="operator_at"></a>operator] 

 Devuelve el elemento situado en el índice especificado.  
  
```  
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator[] (int _I0) const restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 Índice.  
  
 `_I0`  
 Índice.  
  
### <a name="return-value"></a>Valor devuelto  
 El elemento que se encuentra en el índice especificado.  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

 Copia especificado [textura](texture-class.md) objeto a ésta.  
  
```  
texture& operator= (
    const texture& _Other);

 
texture& operator= (
    texture<value_type, _Rank>&& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `texture` objeto que se va a copiar de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `texture` objeto.  
  
##  <a name="a-nameranka-rank"></a><a name="rank"></a>rango 

 Obtiene el rango de la `texture` objeto.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="a-namerowpitcha-rowpitch"></a><a name="row_pitch"></a>row_pitch 

 Obtiene el número de bytes entre cada fila de una 2D o 3D ensayo textura en la CPU.  
  
```  
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;  
```  
  
##  <a name="a-nameseta-set"></a><a name="set"></a>conjunto 

 Establece el valor del elemento en el índice especificado.  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 El índice del elemento.  
  
 `_Rank`  
 El rango del índice.  
  
 `value`  
 Nuevo valor del elemento.  
  
##  <a name="a-namectora-texture"></a><a name="ctor"></a>textura 

 Inicializa una nueva instancia de la clase `texture`.  
  
```  
texture(
    const Concurrency::extent<_Rank>& _Ext) restrict(cpu);

 
texture(
    int _E0) restrict(cpu);

 
texture(
    int _E0,  
    int _E1) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    const Concurrency::extent<_Rank>& _Ext, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1,  
    int _E2, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    const Concurrency::extent<_Rank>& _Ext, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1,  
    int _E2, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu))  ;  
 
texture(
    int _E0,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av)  ;  
 
texture(
    int _E0,  
    int _E1,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av)  ;  
 
texture(
    int _E0,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    const texture& _Src,  
    const Concurrency::accelerator_view& _Acc_view);

 
texture(
    texture&& _Other);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,   
    unsigned int _Bits_per_scalar_element,   
    const Concurrency::accelerator_view& _Av);

 
texture(
    const texture& _Src);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Acc_view`  
 El [accelerator_view](accelerator-view-class.md) que especifica la ubicación de la textura.  
  
 `_Av`  
 El [accelerator_view](accelerator-view-class.md) que especifica la ubicación de la textura.  
  
 `_Associated_av`  
 Un accelerator_view que especifica el destino preferido para copias de seguridad a o desde este textura.  
  
 `_Bits_per_scalar_element`  
 El número de bits por cada elemento escalar en el tipo subyacente de escalar de la textura. En general, el valor admitido son 8, 16, 32 y 64. Si se especifica 0, el número de bits es el mismo que el scalar_type subyacente. 64 solo es válida para las texturas doble.  
  
 `_Ext`  
 La extensión de cada dimensión de la textura.  
  
 `_E0`  
 El componente más importante de la textura.  
  
 `_E1`  
 El componente siguiente-a-más significativo de la textura.  
  
 `_E2`  
 El componente menos significativo de la extensión de la textura.  
  
 `_Input_iterator`  
 El tipo de la entrada interator.  
  
 `_Mipmap_levels`  
 El número de niveles de mipmap de la textura subyacente. Si se especifica 0, la textura tendrá la gama completa de los niveles de mipmap hasta el tamaño más pequeño posible para la extensión especificada.  
  
 `_Rank`  
 El rango de la extensión.  
  
 `_Source`  
 Un puntero a un búfer de host.  
  
 `_Src`  
 Textura para copiar.  
  
 `_Src_byte_size`  
 El número de bytes en el búfer de origen.  
  
 `_Src_first`  
 Un iterador de comienzo en el contenedor de origen.  
  
 `_Src_last`  
 Un iterador final en el contenedor de origen.  
  
 `_Other`  
 Otro origen de datos.  
  
 `_Rank`  
 El rango de la sección.  
  
## <a name="see-also"></a>Vea también  
 [Graphics Namespace](concurrency-graphics-namespace.md)

