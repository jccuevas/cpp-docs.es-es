---
title: "Concurrency::graphics (Espacio de nombres) | Microsoft Docs"
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
  - "amp_graphics/Concurrency::graphics"
  - "amp_short_vectors/Concurrency::graphics"
dev_langs: 
  - "C++"
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::graphics (Espacio de nombres)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

El espacio de nombres para gráficos proporciona tipos y funciones diseñados para la programación de gráficos.  
  
## Sintaxis  
  
```  
namespace graphics;  
```  
  
## Miembros  
  
### Espacios de nombres  
  
|Name|Descripción|  
|----------|-----------------|  
|[Concurrency::graphics::direct3d \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md)|Proporciona funciones para la interoperabilidad de Direct3D.|  
  
### Typedefs  
  
|Name|Descripción|  
|----------|-----------------|  
|`uint`|El tipo de elemento para [uint\_2 \(Clase\)](../../../parallel/amp/reference/uint-2-class.md), [uint\_3 \(Clase\)](../../../parallel/amp/reference/uint-3-class.md), y [uint\_4 \(Clase\)](../../../parallel/amp/reference/uint-4-class.md).  Definida como `typedef unsigned int uint;`.|  
  
### Enumeraciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[address\_mode \(Enumeración\)](../Topic/address_mode%20Enumeration.md)|Especifica modos de dirección compatibles para el muestreo de textura.|  
|[filter\_mode \(Enumeración\)](../Topic/filter_mode%20Enumeration.md)|Especifica modos de filtro compatibles con el muestreo de textura.|  
  
### Clases  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture \(Clase\)](../../../parallel/amp/reference/texture-class.md)|Una textura es un agregado de datos en un accelerator\_view en el dominio de la extensión.  Es una recopilación de variables, una por cada elemento de un dominio de extensión.  Cada variable tiene un valor que corresponde a C\+\+ de tipo primitivo \(unsigned int, int, float, double\), a un estándar de tipo escalar, a un unorm \(definido en concurrency::graphics\) o a un tipo elegible de vectores cortos definidos en concurrency::graphics.|  
|[writeonly\_texture\_view \(Clase\)](../../../parallel/amp/reference/writeonly-texture-view-class.md)|Un writeonly\_texture\_view proporciona un acceso de solo lectura a una textura.|  
|[double\_2 \(Clase\)](../../../parallel/amp/reference/double-2-class.md)|Representa un vector corto con 2 valores de `double`.|  
|[double\_3 \(Clase\)](../../../parallel/amp/reference/double-3-class.md)|Representa un vector corto con 3 valores de `double`.|  
|[double\_4 \(Clase\)](../../../parallel/amp/reference/double-4-class.md)|Representa un vector corto con 4 valores de `double`.|  
|[float\_2 \(Clase\)](../../../parallel/amp/reference/float-2-class.md)|Representa un vector corto con 2 valores de `float`.|  
|[float\_3 \(Clase\)](../../../parallel/amp/reference/float-3-class.md)|Representa un vector corto con 3 valores de `float`.|  
|[float\_4 \(Clase\)](../../../parallel/amp/reference/float-4-class.md)|Representa un vector corto con 4 valores de `float`.|  
|[int\_2 \(Clase\)](../../../parallel/amp/reference/int-2-class.md)|Representa un vector corto con 2 valores de `int`.|  
|[int\_3 \(Clase\)](../../../parallel/amp/reference/int-3-class.md)|Representa un vector corto con 3 valores de `int`.|  
|[int\_4 \(Clase\)](../../../parallel/amp/reference/int-4-class.md)|Representa un vector corto con 4 valores de `int`.|  
|[norm\_2 \(Clase\)](../../../parallel/amp/reference/norm-2-class.md)|Representa un vector corto con 2 valores de `norm`.|  
|[norm\_3 \(Clase\)](../../../parallel/amp/reference/norm-3-class.md)|Representa un vector corto con 3 valores de `norm`.|  
|[norm\_4 \(Clase\)](../../../parallel/amp/reference/norm-4-class.md)|Representa un vector corto con 4 valores de `norm`.|  
|[uint\_2 \(Clase\)](../../../parallel/amp/reference/uint-2-class.md)|Representa un vector corto con 2 valores de `uint`.|  
|[uint\_3 \(Clase\)](../../../parallel/amp/reference/uint-3-class.md)|Representa un vector corto con 3 valores de `uint`.|  
|[uint\_4 \(Clase\)](../../../parallel/amp/reference/uint-4-class.md)|Representa un vector corto con 4 valores de `uint`.|  
|[unorm\_2 \(Clase\)](../../../parallel/amp/reference/unorm-2-class.md)|Representa un vector corto con 2 valores de `unorm`.|  
|[unorm\_3 \(Clase\)](../../../parallel/amp/reference/unorm-3-class.md)|Representa un vector corto con 3 valores de `unorm`.|  
|[unorm\_4 \(Clase\)](../../../parallel/amp/reference/unorm-4-class.md)|Representa un vector corto con 4 valores de `unorm`.|  
|[sampler \(Clase\)](../../../parallel/amp/reference/sampler-class.md)|Representa la configuración de muestra utilizada para el muestreo de textura.|  
|[short\_vector \(Estructura\)](../../../parallel/amp/reference/short-vector-structure.md)|Proporciona una implementación básica de un vector de valores cortos.|  
|[short\_vector\_traits \(Estructura\)](../../../parallel/amp/reference/short-vector-traits-structure.md)|Permite la recuperación de la longitud y el tipo de un vector corto.|  
|[texture\_view \(Clase\)](../../../parallel/amp/reference/texture-view-class.md)|Proporciona acceso de lectura y de escritura a una textura.|  
  
### Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[copy \(Función\)](../Topic/copy%20Function.md)|Sobrecargado.  Copia el contenido del origen de la textura en el búfer de hosts de destino.|  
|[copy\_async \(Función\)](../Topic/copy_async%20Function.md)|Sobrecargado.  De forma asincrónica, copia el contenido de la textura de origen en el búfer del host de destino.|  
  
## Requisitos  
 **Encabezado:** amp\_graphics.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)