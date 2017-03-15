---
title: tiled_index (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::tiled_index
dev_langs:
- C++
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
caps.latest.revision: 19
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
ms.openlocfilehash: 2c10721f40bd1c90a196ba82655482f35a8e10d8
ms.lasthandoff: 02/24/2017

---
# <a name="tiledindex-class"></a>tiled_index (Clase)
Proporciona un índice en una [tiled_extent ()](tiled-extent-class.md) objeto. Esta clase tiene propiedades para tener acceso a elementos con respecto al origen local del mosaico y con el origen global. Para obtener más información sobre los espacios de mosaico, consulte [mosaicos utilizando](../../../parallel/amp/using-tiles.md).  
  
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
 La longitud de la dimensión más importante.  
  
 `_Dim1`  
 La longitud de la dimensión importante siguiente a la mayoría.  
  
 `_Dim2`  
 La longitud de la dimensión menos significativa.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[tiled_index (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `tile_index`.|  

  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[get_tile_extent (método)](#tiled_index__get_tile_extent)|Devuelve un [punto](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.|  


  
### <a name="public-constants"></a>Constantes públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Barrier (constante)](#tiled_index__barrier)|Almacena un [tile_barrier](tile-barrier-class.md) objeto que representa una barrera en el mosaico actual de subprocesos.|  
|||  
|[Constante global](#tiled_index__global)|Almacena un [índice](index-class.md) objeto de índice de rango 1, 2 o 3 que representa la información global en un [cuadrícula](http://msdn.microsoft.com/en-us/f7d1b6a6-586c-4345-b09a-bfc26c492cb0) objeto.|  
|[local (constante)](#tiled_index__local)|Almacena un `index` objeto de índice de rango 1, 2 o 3 que representa la relación en el mosaico actual de un [tiled_extent ()](tiled-extent-class.md) objeto.|  
|[Rank (constante)](#tiled_index__rank)|Almacena el rango de la `tiled_index` objeto.|  
|[Tile (constante)](#tiled_index__tile)|Almacena un `index` objeto de rango de 1, 2 o 3 que representa las coordenadas del mosaico actual de un `tiled_extent` objeto.|  
|[tile_dim0 (constante)](#tiled_index__tile_dim0)|Almacena la longitud de la dimensión más importante.|  
|[tile_dim1 (constante)](#tiled_index__tile_dim1)|Almacena la longitud de la dimensión de siguiente a más significativo.|  
|[tile_dim2 (constante)](#tiled_index__tile_dim2)|Almacena la longitud de la dimensión menos significativa.|  
|[tile_origin (constante)](#tiled_index__tile_origin)|Almacena un `index` objeto de coordenadas de rango 1, 2 o 3 que representa la información global del origen de la ventana actual en un `tiled_extent` objeto.|  

  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[tile_extent miembro de datos](#tile_extent)|Obtiene un [punto](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.|  

  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  


## <a name="a-nametiledindexctora--tiledindex-constructor"></a><a name="tiled_index__ctor"></a>tiled_index (Constructor)  
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
 Local [índice](index-class.md) de creado`tiled_index`  
  
 `_Tile`  
 El mosaico [índice](index-class.md) de creado`tiled_index`  
  
 `_Tile_origin`  
 El origen del mosaico [índice](index-class.md) de creado`tiled_index`  
  
 `_Barrier`  
 El [tile_barrier](tile-barrier-class.md) objeto de creado `tiled_index`.  
  
 `_Other`  
 El `tile_index` objeto que se copiará a la construido `tiled_index`.  
  
## <a name="overloads"></a>Overloads  
  
|||  
|-|-|  
|Nombre|Descripción|  
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicializa una nueva instancia de la `tile_index` clase desde el índice de la imagen en coordenadas globales y la posición relativa en el mosaico en coordenadas locales. El `_Global` y `_Tile_origin` se calculan los parámetros.|  
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicializa una nueva instancia de la `tile_index` clase copiando especificado `tiled_index` objeto.|  


## <a name="a-nametiledindexgettileextenta--gettileextent"></a><a name="tiled_index__get_tile_extent"></a>get_tile_extent
Devuelve un [punto](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
extent<rank> get_tile_extent()restrict(amp,cpu);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un `extent` objeto que tiene los valores de la `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.  

## <a name="a-nametiledindexbarriera--barrier"></a><a name="tiled_index__barrier"></a>barrera   
Almacena un [tile_barrier](tile-barrier-class.md) objeto que representa una barrera en el mosaico actual de subprocesos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const tile_barrier barrier;  
```  

## <a name="a-nametiledindexglobala--global"></a><a name="tiled_index__global"></a>global   
Almacena un [índice](index-class.md) objeto de rango 1, 2 o 3 que representa el índice de un objeto global.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const index<rank> global;  
```  
  
## <a name="a-nametiledindexlocala--local"></a><a name="tiled_index__local"></a>local   
Almacena un [índice](index-class.md) objeto de índice de rango 1, 2 o 3 que representa la relación en el mosaico actual de un [tiled_extent ()](tiled-extent-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const index<rank> local;  
```  
  
## <a name="a-nametiledindexranka--rank"></a><a name="tiled_index__rank"></a>rango   
Almacena el rango de la `tiled_index` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const int rank = _Rank;  
```  

## <a name="a-nametiledindextilea--tile"></a><a name="tiled_index__tile"></a>Mosaico   
Almacena un [índice](index-class.md) objeto de rango de 1, 2 o 3 que representa las coordenadas del mosaico actual de un [tiled_extent ()](tiled-extent-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const index<rank> tile;  
```  
  
## <a name="a-nametiledindextiledim0a--tiledim0"></a><a name="tiled_index__tile_dim0"></a>tile_dim0  
Almacena la longitud de la dimensión más importante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const int tile_dim0 = _Dim0;  
```  
   
## <a name="a-nametiledindextiledim1a--tiledim1"></a><a name="tiled_index__tile_dim1"></a>tile_dim1   
Almacena la longitud de la dimensión de siguiente a más significativo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="a-nametiledindextiledim2a--tiledim2"></a><a name="tiled_index__tile_dim2"></a>tile_dim2   
Almacena la longitud de la dimensión menos significativa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="a-nametiledindextileorigina--tileorigin"></a><a name="tiled_index__tile_origin"></a>tile_origin   
Almacena un [índice](index-class.md) objeto de coordenadas de rango 1, 2 o 3 que representa la información global del origen del mosaico actual dentro de un [tiled_extent ()](tiled-extent-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const index<rank> tile_origin  
```  
## <a name="a-nametileextenta--tileextent"></a><a name="tile_extent"></a>tile_extent
  Obtiene un [punto](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;  
```  
  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

