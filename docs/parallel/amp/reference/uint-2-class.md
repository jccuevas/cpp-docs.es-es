---
title: uint_2 (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp_short_vectors/Concurrency::graphics::uint_2::set_xy
- amp_short_vectors/Concurrency::graphics::uint_2::y
- amp_short_vectors/Concurrency::graphics::uint_2::gr
- amp_short_vectors/Concurrency::graphics::uint_2::operator-
- amp_short_vectors/Concurrency::graphics::uint_2::get_x
- amp_short_vectors/Concurrency::graphics::uint_2::operator-=
- amp_short_vectors/Concurrency::graphics::uint_2::r
- amp_short_vectors/Concurrency::graphics::uint_2::yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator--
- amp_short_vectors/Concurrency::graphics::uint_2::set_yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator=
- amp_short_vectors/Concurrency::graphics::uint_2::set_x
- amp_short_vectors/Concurrency::graphics::uint_2::operator+=
- amp_short_vectors/Concurrency::graphics::uint_2::get_y
- amp_short_vectors/Concurrency::graphics::uint_2::xy
- amp_short_vectors/Concurrency::graphics::uint_2::x
- amp_short_vectors/Concurrency::graphics::uint_2::get_xy
- amp_short_vectors/Concurrency::graphics::uint_2::set_y
- amp_short_vectors/Concurrency::graphics::uint_2
- amp_short_vectors/Concurrency::graphics::uint_2::operator*=
- amp_short_vectors/Concurrency::graphics::uint_2::get_yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator/=
- amp_short_vectors/Concurrency::graphics::uint_2::g
- amp_short_vectors/Concurrency::graphics::uint_2::operator++
- amp_short_vectors/Concurrency::graphics::uint_2::rg
dev_langs:
- C++
ms.assetid: 9fcc9129-72b1-4da7-9012-4d3be15f1c52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03447d24f77b671b0a2cb171e84c266df1908fb3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="uint2-class"></a>uint_2 (Clase)
Representa un vector corto de dos enteros sin signo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class uint_2;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Constructor uint_2](#ctor)|Sobrecargado. El constructor predeterminado, inicializa todos los elementos con 0.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|uint_2::get_x||  
|uint_2::get_xy||  
|uint_2:: get_Y||  
|uint_2::get_yx||  
|Método uint_2::ref_g||  
|Método uint_2::ref_r||  
|Método uint_2::ref_x||  
|Método uint_2::ref_y||  
|uint_2::set_x||  
|uint_2::set_xy||  
|uint_2:: set_y||  
|uint_2::set_yx||  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|uint_2::operator--||  
|uint_2::operator%=||  
|uint_2::operator&=||  
|uint_2::operator*=||  
|uint_2::operator/=||  
|uint_2::operator^=||  
|uint_2::operator&#124;=||  
|uint_2::operator~||  
|uint_2::operator++||  
|uint_2::operator+=||  
|uint_2::operator<\<=||  
|uint_2::operator=||  
|uint_2::operator-=||  
|uint_2::operator>>=||  
  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[cambio de tamaño constante](#uint_2__size)||  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|uint_2:: g||  
|uint_2:: GR||  
|uint_2:: r||  
|uint_2::rg||  
|uint_2:: x||  
|uint_2:: XY||  
|uint_2:: y||  
|uint_2:: YX||  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `uint_2`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_short_vectors.h  
  
 **Namespace:** Concurrency:: Graphics  
  
##  <a name="ctor"></a> uint_2 

 El constructor predeterminado, inicializa todos los elementos con 0.  
  
```  
uint_2() restrict(amp,
    cpu);

 
uint_2(
    unsigned int _V0,  
    unsigned int _V1) restrict(amp,
    cpu);

 
uint_2(
    unsigned int _V) restrict(amp,
    cpu);

 
uint_2(
    const uint_2& _Other) restrict(amp,
    cpu);

 
explicit inline uint_2(
    const int_2& _Other) restrict(amp,
    cpu);

 
explicit inline uint_2(
    const float_2& _Other) restrict(amp,
    cpu);

 
explicit inline uint_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

 
explicit inline uint_2(
    const norm_2& _Other) restrict(amp,
    cpu);

 
explicit inline uint_2(
    const double_2& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_V0`  
 El valor para inicializar el elemento 0.  
  
 `_V1`  
 El valor para inicializar el elemento 1.  
  
 `_V`  
 El valor de inicialización.  
  
 `_Other`  
 El objeto utilizado para inicializar.  
  
##  <a name="uint_2__size"></a> Tamaño 

```  
static const int size = 2;  
```  
  
## <a name="see-also"></a>Vea también  
 [Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
