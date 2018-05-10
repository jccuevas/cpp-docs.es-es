---
title: Texture (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- texture
- AMP_GRAPHICS/texture
- AMP_GRAPHICS/concurrency::graphics::texture::texture
- AMP_GRAPHICS/concurrency::graphics::texture::copy_to
- AMP_GRAPHICS/concurrency::graphics::texture::data
- AMP_GRAPHICS/concurrency::graphics::texture::get
- AMP_GRAPHICS/concurrency::graphics::texture::get_associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::get_depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::get_row_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::set
- AMP_GRAPHICS/concurrency::graphics::texture::rank
- AMP_GRAPHICS/concurrency::graphics::texture::associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::row_pitch
dev_langs:
- C++
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b16e449f3def7b4b86932e9806fa78d422466978
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="texture-class"></a>texture (Clase)
Una textura es un agregado de datos de un `accelerator_view` en el dominio de la extensión. Es una colección de variables, uno para cada elemento en un dominio de la extensión. Cada variable contiene un valor que corresponde al tipo primitivo de C++ ( `unsigned int`, `int`, `float`, `double`), un tipo escalar ( `norm`, o `unorm`), o un tipo de vector corto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <typename value_type,  int _Rank>  
class texture;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value_type`  
 El tipo de los elementos de la textura.  
  
 `_Rank`  
 El rango de la textura.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`scalar_type`|Tipos escalares.|  
|`value_type`|Los tipos de valor.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Constructor de textura](#ctor)|Inicializa una nueva instancia de la clase `texture`.|  
|[~ texture (destructor)](#ctor)|Destruye el objeto `texture`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[copy_to](#copy_to)|Copia la `texture` objeto en el destino, al hacer una copia en profundidad.|  
|[data](#data)|Devuelve un puntero de CPU para los datos sin procesar de esta textura.|  
|[get](#get)|Devuelve el valor del elemento en el índice especificado.|  
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Devuelve el [accelerator_view](accelerator-view-class.md) que es el destino preferido para esta textura se copien en.|  
|[get_depth_pitch](#get_depth_pitch)|Devuelve el número de bytes entre cada sector de profundidad en una textura en la CPU de almacenamiento provisional de 3D.|  
|[get_row_pitch](#get_row_pitch)|Devuelve el número de bytes entre cada fila de una 2D o 3D textura en la CPU de almacenamiento provisional.|  
|[set](#set)|Establece el valor del elemento en el índice especificado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Operator()](#operator_call)|Devuelve el valor del elemento especificado por los parámetros.|  
|[operator[]](#operator_at)|Devuelve el elemento situado en el índice especificado.|  
|[operator=](#operator_eq)|Copia especificado [textura](texture-class.md) objeto a este.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Rank (constante)](#rank)|Obtiene el rango de la `texture` objeto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[associated_accelerator_view](#associated_accelerator_view)|Obtiene el [accelerator_view](accelerator-view-class.md) que es el destino preferido para esta textura se copien en.|  
|[depth_pitch](#depth_pitch)|Obtiene el número de bytes entre cada sector de profundidad en una textura de ensayo 3D en la CPU.|  
|[row_pitch](#row_pitch)|Obtiene el número de bytes entre cada fila de una 2D o 3D ensayo textura en la CPU.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Texture_base`  
  
 `texture`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_graphics.h  
  
 **Namespace:** Concurrency:: Graphics  
  
##  <a name="dtor"></a> ~ textura 

 Destruye el objeto `texture`.  
  
```  
~texture() restrict(cpu);
```  
  
##  <a name="associated_accelerator_view"></a> associated_accelerator_view 

 Obtiene el [accelerator_view](accelerator-view-class.md) que es el destino preferido para esta textura se copien en.  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="copy_to"></a> copy_to 

 Copia la `texture` objeto en el destino, al hacer una copia en profundidad.  
  
```  
void copy_to(texture& _Dest) const; 
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const; 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Objeto que se va a copiar en.  
  
 `_Rank`  
 El rango de la textura.  
  
 `value_type`  
 El tipo de los elementos de la textura.  
  
##  <a name="data"></a> Datos 

 Devuelve un puntero de CPU para los datos sin procesar de esta textura.  
  
```  
void* data() restrict(cpu);

 
const void* data() const restrict(cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a los datos sin procesar de la textura.  
  
##  <a name="depth_pitch"></a> depth_pitch 

 Obtiene el número de bytes entre cada sector de profundidad en una textura de ensayo 3D en la CPU.  
  
```  
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;  
```  
  
##  <a name="get"></a> Obtener 

 Devuelve el valor del elemento en el índice especificado.  
  
```  
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 El índice del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor del elemento en el índice especificado.  
  
##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view 

 Devuelve el accelerator_view que es el destino preferido para esta textura se copien en.  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El [accelerator_view](accelerator-view-class.md) que es el destino preferido para esta textura se copien en.  
  
##  <a name="get_depth_pitch"></a> get_depth_pitch 

 Devuelve el número de bytes entre cada sector de profundidad en una textura en la CPU de almacenamiento provisional de 3D.  
  
```  
unsigned int get_depth_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes entre cada sector de profundidad en una textura en la CPU de almacenamiento provisional de 3D.  
  
##  <a name="get_row_pitch"></a> get_row_pitch 

 Devuelve el número de bytes entre cada fila de una textura 2 dimensiones de almacenamiento provisional, o entre cada fila de una sección de profundidad de textura 3 dimensiones de almacenamiento provisional.  
  
```  
unsigned int get_row_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes entre cada fila de una textura 2 dimensiones de almacenamiento provisional, o entre cada fila de una sección de profundidad de textura 3 dimensiones de almacenamiento provisional.  
  
##  <a name="operator_call"></a> Operator() 

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
  
##  <a name="operator_at"></a> operator] 

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
 El elemento situado en el índice especificado.  
  
##  <a name="operator_eq"></a> operator= 

 Copia especificado [textura](texture-class.md) objeto a este.  
  
```  
texture& operator= (
    const texture& _Other);

 
texture& operator= (
    texture<value_type, _Rank>&& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `texture` objeto que lo copien.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `texture` objeto.  
  
##  <a name="rank"></a> Rango 

 Obtiene el rango de la `texture` objeto.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="row_pitch"></a> row_pitch 

 Obtiene el número de bytes entre cada fila de una 2D o 3D ensayo textura en la CPU.  
  
```  
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;  
```  
  
##  <a name="set"></a> Conjunto 

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
  
##  <a name="ctor"></a> textura 

 Inicializa una nueva instancia de la clase `texture`.  
  
```  
texture(const Concurrency::extent<_Rank>& _Ext) restrict(cpu);
 
texture(int _E0) restrict(cpu);
 
texture(int _E0, int _E1) restrict(cpu);
 
texture(int _E0, int _E1, int _E2) restrict(cpu);
 
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


template<typename _Input_iterator>  
texture(
    const Concurrency::extent<_Rank>& _Ext, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1,  
    int _E2, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    const Concurrency::extent<_Rank>& _Ext, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1,  
    int _E2, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
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
 Un accelerator_view que especifica el destino preferida para las copias a o desde este textura.  
  
 `_Bits_per_scalar_element`  
 El número de bits por cada elemento escalar en el tipo escalar subyacente de la textura. En general, el valor admitido son 8, 16, 32 y 64. Si se especifica 0, el número de bits es el mismo que el scalar_type subyacente. 64 solo es válida para las texturas doble.  
  
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
 El número de niveles de asignación MIP de la textura subyacente. Si se especifica 0, la textura tendrá toda la gama de niveles de asignación MIP hasta el tamaño más pequeño posible para que la extensión especificada.  
  
 `_Rank`  
 El rango de la extensión.  
  
 `_Source`  
 Un puntero a un búfer de host.  
  
 `_Src`  
 Textura a copiar.  
  
 `_Src_byte_size`  
 El número de bytes en el búfer de origen.  
  
 `_Src_first`  
 Un iterador de comienzo en el contenedor de origen.  
  
 `_Src_last`  
 Un iterador de final en el contenedor de origen.  
  
 `_Other`  
 Otro origen de datos.  
  
 `_Rank`  
 El rango de la sección.  
  
## <a name="see-also"></a>Vea también  
 [Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
