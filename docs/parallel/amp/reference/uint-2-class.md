---
title: uint_2 (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 1116be21d4f65b67ab967b7acedf4859df54a6e7
ms.lasthandoff: 02/24/2017

---
# <a name="uint2-class"></a>uint_2 (Clase)
Representa un vector corto de dos enteros sin signo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class uint_2;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor uint_2](#ctor)|Sobrecargado. El constructor predeterminado, inicializa todos los elementos con 0.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|Método uint_2::get_x||  
|Método uint_2::get_xy||  
|Método uint_2::get_y||  
|Método uint_2::get_yx||  
|Método uint_2::ref_g||  
|Método uint_2::ref_r||  
|Método uint_2::ref_x||  
|Método uint_2::ref_y||  
|Método uint_2::set_x||  
|Método uint_2::set_xy||  
|Método uint_2::set_y||  
|Método uint_2::set_yx||  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|Operador uint_2::operator--||  
|Operador uint_2::operator%=||  
|Operador uint_2::operator&=||  
|Operador uint_2::operator*=||  
|Operador uint_2::operator/=||  
|Operador uint_2::operator^=||  
|operador uint_2:: | = (operador)||  
|Operador uint_2::operator~||  
|Operador uint_2::operator++||  
|Operador uint_2::operator+=||  
|operador uint_2::\<= (operador)||  
|Operador uint_2::operator=||  
|Operador uint_2::operator-=||  
|operador uint_2:: >> = (operador)||  
  
### <a name="public-constants"></a>Constantes públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[tamaño (constante)](#uint_2__size)||  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|Miembro de datos uint_2::g||  
|Miembro de datos uint_2::gr||  
|Miembro de datos uint_2::r||  
|Miembro de datos uint_2::rg||  
|Miembro de datos uint_2::x||  
|Miembro de datos uint_2::xy||  
|Miembro de datos uint_2::y||  
|Miembro de datos uint_2::yx||  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `uint_2`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_short_vectors.h  
  
 **Namespace:** Graphics  
  
##  <a name="a-namectora-uint2"></a><a name="ctor"></a>uint_2 

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
 Objeto utilizado para inicializar.  
  
##  <a name="a-nameuint2sizea-size"></a><a name="uint_2__size"></a>tamaño 

```  
static const int size = 2;  
```  
  
## <a name="see-also"></a>Vea también  
 [Graphics Namespace](concurrency-graphics-namespace.md)

