---
title: "tiled_index (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::tiled_index"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tiled_index (clase)"
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
caps.latest.revision: 19
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# tiled_index (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Ofrece un índice a un objeto [tiled\_extent](../../../parallel/amp/reference/tiled-extent-class.md) .  Esta clase tiene propiedades para tener acceso a elementos relacionados con el origen local del mosaico y con el origen global.  Para obtener más información acerca de los espacios de mosaico, consulte [Usar mosaicos](../../../parallel/amp/using-tiles.md).  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `_Dim0`  
 La longitud de la dimensión más significativa.  
  
 `_Dim1`  
 La longitud de la siguiente dimensión más significativa.  
  
 `_Dim2`  
 La longitud de la dimensión menos significativa.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tiled\_index::tiled\_index \(Constructor\)](../Topic/tiled_index::tiled_index%20Constructor.md)|Inicializa una nueva instancia de la clase `tile_index`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tiled\_index::get\_tile\_extent \(Método\)](../Topic/tiled_index::get_tile_extent%20Method.md)|Devuelve un objeto [extent](../../../parallel/amp/reference/extent-class-cpp-amp.md) con los valores de los argumentos de plantilla `_Dim0`, `_Dim1`, `_Dim2` y [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md).|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[tiled\_index::barrier \(Constante\)](../Topic/tiled_index::barrier%20Constant.md)|Almacena un objeto [tile\_barrier](../../../parallel/amp/reference/tile-barrier-class.md) que representa una barrera en el mosaico actual de subprocesos.|  
|||  
|[tiled\_index::global \(Constante\)](../Topic/tiled_index::global%20Constant.md)|Almacena un objeto [index](../../../parallel/amp/reference/index-class.md) del rango 1, 2 ó 3 que representa el índice global en un objeto [grid](http://msdn.microsoft.com/es-es/f7d1b6a6-586c-4345-b09a-bfc26c492cb0).|  
|[tiled\_index::local \(Constante\)](../Topic/tiled_index::local%20Constant.md)|Almacena un objeto `index` del rango 1, 2 ó 3 que representa el índice relativo en el mosaico actual de un objeto [tiled\_extent](../../../parallel/amp/reference/tiled-extent-class.md).|  
|[tiled\_index::rank \(Constante\)](../Topic/tiled_index::rank%20Constant.md)|Almacena el rango del objeto [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md).|  
|[tiled\_index::tile \(Constante\)](../Topic/tiled_index::tile%20Constant.md)|Almacena un objeto `index` del rango 1, 2 ó 3 que representa las coordenadas del mosaico actual de un objeto `tiled_extent`.|  
|[tiled\_index::tile\_dim0 \(Constante\)](../Topic/tiled_index::tile_dim0%20Constant.md)|Almacena la longitud de la dimensión más significativa.|  
|[tiled\_index::tile\_dim1 \(Constante\)](../Topic/tiled_index::tile_dim1%20Constant.md)|Almacena la longitud de la siguiente dimension más significativa.|  
|[tiled\_index::tile\_dim2 \(Constante\)](../Topic/tiled_index::tile_dim2%20Constant.md)|Almacena la longitud de la dimensión menos significativa.|  
|[tiled\_index::tile\_origin \(Constante\)](../Topic/tiled_index::tile_origin%20Constant.md)|Almacena un objeto `index` del rango 1, 2 ó 3 que representa las coordenadas globales del origen del mosaico actual en un objeto `tiled_extent`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tiled\_index::tile\_extent \(Miembro de datos\)](../Topic/tiled_index::tile_extent%20Data%20Member.md)|Obtiene un objeto [extent](../../../parallel/amp/reference/extent-class-cpp-amp.md) que tiene los valores de [tiled\_index](../../../parallel/amp/reference/tiled-index-class.md) en los [](../../../parallel/amp/reference/tiled-index-class.md "tiled_index Class") argumentos de plantilla `_Dim0`, `_Dim1` y `_Dim2`.|  
  
## Jerarquía de herencia  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)