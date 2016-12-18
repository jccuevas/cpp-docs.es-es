---
title: "independent_bits_engine (Clase) | Microsoft Docs"
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
  - "std.tr1.independent_bits_engine"
  - "std::tr1::independent_bits_engine"
  - "tr1::independent_bits_engine"
  - "tr1.independent_bits_engine"
  - "independent_bits_engine"
  - "random/std::tr1::independent_bits_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "independent_bits_engine (clase)"
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: 17
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# independent_bits_engine (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una secuencia aleatoria de números con un número específico de bits volviendo a empaquetar bits de los valores devueltos por su motor base.  
  
## Sintaxis  
  
```  
template<class Engine, size_t W, class UIntType> class independent_bits_engine;  
```  
  
#### Parámetros  
 `Engine`  
 El tipo de motor base.  
  
 `W`  
 **Tamaño de palabra**.  Tamaño, en bits, de cada número generado.  **Condición previa**: `0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `UIntType`  
 El tipo de resultado integral sin signo.  Para obtener más información sobre los tipos posibles, vea [\<random\>](../standard-library/random.md).  
  
## Miembros  
  
||||  
|-|-|-|  
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|  
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|  
  
 Para obtener más información acerca de los miembros del motor, vea [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 Esta clase de plantilla describe un *adaptador de motor* que produce valores volviendo a empaquetar bits de los valores devueltos por su motor base, lo que resulta en valores de `W` bits.  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)