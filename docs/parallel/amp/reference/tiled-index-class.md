---
title: tiled_index (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
dev_langs:
- C++
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd28ab01d0d4180cc518cff230eb7df8261f4940
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="tiledindex-class"></a>tiled_index (Clase)
Proporciona un índice en una [tiled_extent](tiled-extent-class.md) objeto. Esta clase tiene propiedades para tener acceso a elementos con respecto al origen de icono local y con respecto al origen global. Para obtener más información sobre los espacios de mosaico, consulte [usando iconos](../../../parallel/amp/using-tiles.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <
    int _Dim0,  
    int _Dim1 = 0,  
    int _Dim2 = 0  
>  
class tiled_index : public _Tiled_index_base<3>;  
 
template <
    int _Dim0,  
    int _Dim1  
>  
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;  
 
template <
    int _Dim0  
>  
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;  
```  
  
#### <a name="parameters"></a>Parámetros  
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
|[tiled_index Constructor](#ctor)|Inicializa una nueva instancia de la clase `tile_index`.|  

  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[get_tile_extent](#tiled_index__get_tile_extent)|Devuelve un [extensión](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.|  


  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Barrier (constante)](#tiled_index__barrier)|Almacena un [tile_barrier](tile-barrier-class.md) objeto que representa una barrera en el mosaico actual de subprocesos.|  
|||  
|[Constante global](#tiled_index__global)|Almacena un [índice](index-class.md) objeto de índice de rango 1, 2 o 3 que representa la información global en un [cuadrícula](http://msdn.microsoft.com/en-us/f7d1b6a6-586c-4345-b09a-bfc26c492cb0) objeto.|  
|[local (constante)](#tiled_index__local)|Almacena un `index` objeto de índice de rango 1, 2 o 3 que representa la relación en el mosaico actual de un [tiled_extent](tiled-extent-class.md) objeto.|  
|[Rank (constante)](#tiled_index__rank)|Almacena el rango de la `tiled_index` objeto.|  
|[Tile (constante)](#tiled_index__tile)|Almacena un `index` objeto de rango de 1, 2 o 3 que representa las coordenadas del mosaico actual de un `tiled_extent` objeto.|  
|[tile_dim0 (constante)](#tiled_index__tile_dim0)|Almacena la longitud de la dimensión más significativa.|  
|[tile_dim1 (constante)](#tiled_index__tile_dim1)|Almacena la longitud de la dimensión importante siguiente a la mayoría.|  
|[tile_dim2 (constante)](#tiled_index__tile_dim2)|Almacena la longitud de la dimensión menos significativa.|  
|[tile_origin (constante)](#tiled_index__tile_origin)|Almacena un `index` objeto de coordenadas de rango 1, 2 o 3 que representa la información global del origen del icono actual en un `tiled_extent` objeto.|  

  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tile_extent](#tile_extent)|Obtiene un [extensión](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.|  

  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  


## <a name="tiled_index__ctor"></a>  tiled_index Constructor  
Inicializa una nueva instancia de la clase `tiled_index`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
tiled_index(  
    const index<rank>& _Global,  
    const index<rank>& _Local,  
    const index<rank>& _Tile,  
    const index<rank>& _Tile_origin,  
    const tile_barrier& _Barrier ) restrict(amp,cpu);  
  
tiled_index(  
    const tiled_index& _Other ) restrict(amp,cpu);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Global`  
 Global [índice](index-class.md) de creado `tiled_index`.  
  
 `_Local`  
 La variable local [índice](index-class.md) de creado `tiled_index`  
  
 `_Tile`  
 El icono [índice](index-class.md) de creado `tiled_index`  
  
 `_Tile_origin`  
 El origen de mosaico [índice](index-class.md) de creado `tiled_index`  
  
 `_Barrier`  
 El [tile_barrier](tile-barrier-class.md) objeto de creado `tiled_index`.  
  
 `_Other`  
 El `tile_index` objeto que se copiará a la construido `tiled_index`.  
  
## <a name="overloads"></a>Overloads  
  
|||  
|-|-|  
|nombre|Descripción|  
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicializa una nueva instancia de la `tile_index` clase desde el índice de los iconos en coordenadas globales y la posición relativa en el icono en coordenadas locales. El `_Global` y `_Tile_origin` se calculan los parámetros.|  
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicializa una nueva instancia de la `tile_index` clase copiando especificado `tiled_index` objeto.|  


## <a name="tiled_index__get_tile_extent"></a>  get_tile_extent
Devuelve un [extensión](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
extent<rank> get_tile_extent()restrict(amp,cpu);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un `extent` objeto que tiene los valores de la `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.  

## <a name="tiled_index__barrier"></a>  barrera   
Almacena un [tile_barrier](tile-barrier-class.md) objeto que representa una barrera en el mosaico actual de subprocesos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const tile_barrier barrier;  
```  

## <a name="tiled_index__global"></a>  Global   
Almacena un [índice](index-class.md) objeto de rango 1, 2 o 3, que representa el índice de un objeto global.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const index<rank> global;  
```  
  
## <a name="tiled_index__local"></a>  Local   
Almacena un [índice](index-class.md) objeto de índice de rango 1, 2 o 3 que representa la relación en el mosaico actual de un [tiled_extent](tiled-extent-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const index<rank> local;  
```  
  
## <a name="tiled_index__rank"></a>  Rango   
Almacena el rango de la `tiled_index` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const int rank = _Rank;  
```  

## <a name="tiled_index__tile"></a>  icono   
Almacena un [índice](index-class.md) objeto de rango de 1, 2 o 3 que representa las coordenadas del mosaico actual de un [tiled_extent](tiled-extent-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const index<rank> tile;  
```  
  
## <a name="tiled_index__tile_dim0"></a>  tile_dim0  
Almacena la longitud de la dimensión más significativa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const int tile_dim0 = _Dim0;  
```  
   
## <a name="tiled_index__tile_dim1"></a>  tile_dim1   
Almacena la longitud de la dimensión importante siguiente a la mayoría.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tiled_index__tile_dim2"></a>  tile_dim2   
Almacena la longitud de la dimensión menos significativa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tiled_index__tile_origin"></a>  tile_origin   
Almacena un [índice](index-class.md) objeto de coordenadas de rango 1, 2 o 3 que representa la información global del origen del icono actual dentro de un [tiled_extent](tiled-extent-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const index<rank> tile_origin  
```  
## <a name="tile_extent"></a>  tile_extent
  Obtiene un [extensión](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;  
```  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
