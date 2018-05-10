---
title: tiled_extent (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
dev_langs:
- C++
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59ac4e878ee67e03498d4d29efe7c91d34c1b4c7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="tiledextent-class"></a>tiled_extent (Clase)
A `tiled_extent` objeto es un `extent` objeto de uno a tres dimensiones que divide el espacio de la extensión en uno, dos o iconos tridimensionales.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template <
    int _Dim0,  
    int _Dim1,  
    int _Dim2  
>  
class tiled_extent : public Concurrency::extent<3>;  
 
template <
    int _Dim0,  
    int _Dim1  
>  
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;  
 
template <
    int _Dim0  
>  
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dim0`  
 La longitud de la dimensión más significativa.  
  
 `_Dim1`  
 La longitud de la dimensión importante siguiente a la mayoría.  
  
 `_Dim2`  
 La longitud de la dimensión menos significativa.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tiled_extent Constructor](#ctor)|Inicializa una nueva instancia de la clase `tiled_extent`.|  

  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[get_tile_extent](#get_tile_extent)|Devuelve un `extent` objeto que capture los valores de la `tiled_extent` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.|  
|[pad](#pad)|Devuelve un nuevo `tiled_extent` objeto con extensiones ajustadas seguridad para ser divisible por las dimensiones del mosaico.|  
|[truncate](#truncate)|Devuelve un nuevo `tiled_extent` objeto con extensiones ajustadas hacia abajo para ser divisible por las dimensiones del mosaico.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[operator=](#operator_eq)|Copia el contenido del elemento especificado `tiled_index` objeto en éste.|  

  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[tile_dim0 (constante)](#tile_dim0)|Almacena la longitud de la dimensión más significativa.|  
|[tile_dim1 (constante)](#tile_dim1)|Almacena la longitud de la dimensión importante siguiente a la mayoría.|  
|[tile_dim2 (constante)](#tile_dim2)|Almacena la longitud de la dimensión menos significativa.|  

  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tile_extent](#tile_extent)|Obtiene un `extent` objeto que capture los valores de la `tiled_extent` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `extent`  
  
 `tiled_extent`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  

## <a name="ctor"> </a>  tiled_extent Constructor  
Inicializa una nueva instancia de la clase `tiled_extent`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
tiled_extent();  
  
tiled_extent(  
    const Concurrency::extent<rank>& _Other );  
  
tiled_extent(  
    const tiled_extent& _Other );  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 El `extent` o `tiled_extent` objeto que se va a copiar.  
  

  

## <a name="get_tile_extent"> </a>  get_tile_extent   
Devuelve un `extent` objeto que capture los valores de la `tiled_extent` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `extent` objeto que captura las dimensiones de esta `tiled_extent` instancia.  
  

## <a name="pad"> </a>  panel   
Devuelve un nuevo `tiled_extent` objeto con extensiones ajustadas seguridad para ser divisible por las dimensiones del mosaico.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
tiled_extent pad() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nuevo `tiled_extent` objeto por valor. 
## <a name="truncate"> </a>  truncar   
Devuelve un nuevo `tiled_extent` objeto con extensiones ajustadas hacia abajo para ser divisible por las dimensiones del mosaico.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
tiled_extent truncate() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un nuevo `tiled_extent` objeto con extensiones ajustadas hacia abajo para ser divisible por las dimensiones del mosaico.  

## <a name="operator_eq"> </a>  operator=   
Copia el contenido del elemento especificado `tiled_index` objeto en éste.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
tiled_extent&  operator= (  
    const tiled_extent& _Other ) restrict (amp, cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `tiled_index` objeto que lo copien.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `tiled_index` instancia.  

## <a name="tile_dim0"> </a>  tile_dim0   
Almacena la longitud de la dimensión más significativa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
static const int tile_dim0 = _Dim0;  
```  
  
## <a name="tile_dim1"> </a>  tile_dim1   
Almacena la longitud de la dimensión importante siguiente a la mayoría.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tile_dim2"> </a>  tile_dim2   
Almacena la longitud de la dimensión menos significativa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tile_extent"> </a>  tile_extent   
  Obtiene un `extent` objeto que capture los valores de la `tiled_extent` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;  
```  
  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
