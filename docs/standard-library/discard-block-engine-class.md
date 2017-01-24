---
title: "discard_block_engine (Clase) | Microsoft Docs"
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
  - "tr1.discard_block_engine"
  - "std.tr1.discard_block_engine"
  - "std::tr1::discard_block_engine"
  - "random/std::tr1::discard_block_engine"
  - "discard_block_engine"
  - "tr1::discard_block_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "discard_block_engine (clase)"
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
caps.latest.revision: 18
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# discard_block_engine (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una secuencia aleatoria descartando valores devueltos por su motor base.  
  
## Sintaxis  
  
```  
template<class Engine, size_t P, size_t R> class discard_block_engine;  
```  
  
#### Parámetros  
 `Engine`  
 El tipo de motor base.  
  
 `P`  
 **Tamaño de bloque**.  El número de valores de cada bloque.  
  
 `R`  
 **Bloque utilizado**.  El número de valores de cada bloque que se utilizan.  El resto se descartan \(`P` \- `R`\).  **Condición previa**: `0 < R ≤ P`  
  
## Miembros  
  
||||  
|-|-|-|  
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|  
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|  
  
 Para obtener más información acerca de los miembros del motor, vea [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 Esta clase de plantilla describe un adaptador de motor que produce valores descartando algunos de los valores devueltos por su motor base.  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)