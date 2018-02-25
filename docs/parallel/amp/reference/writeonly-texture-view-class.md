---
title: writeonly_texture_view (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
dev_langs:
- C++
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d3ab115301a6d7063ba443cf528b382ae955360f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="writeonlytextureview-class"></a>writeonly_texture_view (Clase)
Proporciona acceso de writeonly a una textura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
class writeonly_texture_view;  
 
template <
    typename value_type,  
    int _Rank  
>  
class writeonly_texture_view<value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;  
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
|`scalar_type`||  
|`value_type`|El tipo de los elementos de la textura.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[writeonly_texture_view Constructor](#ctor)|Inicializa una nueva instancia de la clase `writeonly_texture_view`.|  
|[~writeonly_texture_view Destructor](#ctor)|Destruye el objeto `writeonly_texture_view`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[set](#set)|Establece el valor del elemento en el índice especificado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[operator=](#operator_eq)|Copia especificado `writeonly_texture_view` objeto a este.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Rank (constante)](#rank)|Obtiene el rango de la `writeonly_texture_view` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Texture_base`  
  
 `writeonly_texture_view`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_graphics.h  
  
 **Namespace:** Concurrency:: Graphics  
  
##  <a name="dtor"></a> ~writeonly_texture_view 

 Destruye el objeto `writeonly_texture_view`.  
  
```  
~writeonly_texture_view() restrict(amp,cpu);
```  
  
##  <a name="operator_eq"></a> operador = 

 Copia especificado `writeonly_texture_view` objeto a este.  
  
```  
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 `writeonly_texture_view` objeto que se va a copiar de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `writeonly_texture_view` objeto.  
  
##  <a name="rank"></a> Rango 

 Obtiene el rango de la `writeonly_texture_view` objeto.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="set"></a> Conjunto 

 Establece el valor del elemento en el índice especificado.  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) const restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Index`  
 El índice del elemento.  
  
 `value`  
 Nuevo valor del elemento.  
  
##  <a name="ctor"></a> writeonly_texture_view está 

 Inicializa una nueva instancia de la clase `writeonly_texture_view`.  
  
```  
writeonly_texture_view(
    texture<value_type, 
    _Rank>& _Src) restrict(amp);

 
writeonly_texture_view(
    const writeonly_texture_view<value_type,  
    _Rank>& _Src) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rank`  
 El rango de la textura.  
  
 `value_type`  
 El tipo de los elementos de la textura.  
  
 `_Src`  
 La textura que se utiliza para crear la `writeonly_texture_view`.  
  
## <a name="see-also"></a>Vea también  
 [Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
