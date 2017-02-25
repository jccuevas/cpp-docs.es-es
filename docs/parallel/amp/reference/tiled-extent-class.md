---
title: "tiled_extent (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::tiled_extent"
dev_langs: 
  - "C++"
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# tiled_extent (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un objeto `tiled_extent` es un objeto `extent` de una a tres dimensiones que divide el espacio de la extensión en un mosaico de una, dos o tres dimensiones.  
  
## Sintaxis  
  
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
|[tiled\_extent::tiled\_extent \(Constructor\)](../Topic/tiled_extent::tiled_extent%20Constructor.md)|Inicializa una nueva instancia de la clase `tiled_extent`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tiled\_extent::get\_tile\_extent \(Método\)](../Topic/tiled_extent::get_tile_extent%20Method.md)|Devuelve un objeto `extent` que captura los valores de los argumentos `_Dim0`, `_Dim1`, y `_Dim2` de la plantilla de `tiled_extent`.|  
|[tiled\_extent::pad \(Método\)](../Topic/tiled_extent::pad%20Method.md)|Devuelve un nuevo objeto `tiled_extent` con extensiones ajustadas para ser equitativamente divisibles por las dimensiones de la tesela.|  
|[tiled\_extent::truncate \(Método\)](../Topic/tiled_extent::truncate%20Method.md)|Devuelve un nuevo objeto `tiled_extent` con extensiones ajustadas a la baja para ser divisible en pares por las dimensiones de la tesela.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tiled\_extent::operator\= \(Operador\)](../Topic/tiled_extent::operator=%20Operator.md)|Copia el contenido del objeto especificado `tiled_index` en este.|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[tiled\_extent::tile\_dim0 \(Constante\)](../Topic/tiled_extent::tile_dim0%20Constant.md)|Almacena la longitud de la dimensión más significativa.|  
|[tiled\_extent::tile\_dim1 \(Constante\)](../Topic/tiled_extent::tile_dim1%20Constant.md)|Almacena la longitud de la siguiente dimension más significativa.|  
|[tiled\_extent::tile\_dim2 \(Constante\)](../Topic/tiled_extent::tile_dim2%20Constant.md)|Almacena la longitud de la dimensión menos significativa.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tiled\_extent::tile\_extent \(Miembro de datos\)](../Topic/tiled_extent::tile_extent%20Data%20Member.md)|Obtiene un objeto `extent` que captura los valores de los argumentos de la plantilla `_Dim0`, `_Dim1` y `_Dim2` `tiled_extent`.|  
  
## Jerarquía de herencia  
 `extent`  
  
 `tiled_extent`  
  
## Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)