---
title: writeonly_texture_view (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics::writeonly_texture_view
dev_langs:
- C++
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
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
ms.openlocfilehash: a40aa0cb433b6daee19af7fdea7c6421b61c1b4c
ms.lasthandoff: 02/24/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|`scalar_type`||  
|`value_type`|El tipo de los elementos de la textura.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[writeonly_texture_view (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `writeonly_texture_view`.|  
|[~ writeonly_texture_view (destructor)](#ctor)|Destruye el objeto `writeonly_texture_view`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[establecer (método)](#set)|Establece el valor del elemento en el índice especificado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador = (operador)](#operator_eq)|Copia especificado `writeonly_texture_view` objeto a ésta.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Rank (constante)](#rank)|Obtiene el rango de la `writeonly_texture_view` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Texture_base`  
  
 `writeonly_texture_view`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_graphics.h  
  
 **Namespace:** Graphics  
  
##  <a name="a-namedtora-writeonlytextureview"></a><a name="dtor"></a>~ writeonly_texture_view 

 Destruye el objeto `writeonly_texture_view`.  
  
```  
~writeonly_texture_view() restrict(amp,cpu);
```  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

 Copia especificado `writeonly_texture_view` objeto a ésta.  
  
```  
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 `writeonly_texture_view`objeto que se va a copiar de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `writeonly_texture_view` objeto.  
  
##  <a name="a-nameranka-rank"></a><a name="rank"></a>rango 

 Obtiene el rango de la `writeonly_texture_view` objeto.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="a-nameseta-set"></a><a name="set"></a>conjunto 

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
  
##  <a name="a-namectora-writeonlytextureview"></a><a name="ctor"></a>writeonly_texture_view 

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
 [Graphics Namespace](concurrency-graphics-namespace.md)

