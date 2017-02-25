---
title: "Concurrency::direct3d (Espacio de nombres) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::direct3d"
  - "amprt/Concurrency::direct3d"
  - "amp_short_vectors/Concurrency::direct3d"
  - "amp_graphics/Concurrency::direct3d"
  - "amp_math/Concurrency::direct3d"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "direct3d (espacio de nombres)"
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# Concurrency::direct3d (Espacio de nombres)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

El espacio de nombres `direct3d` proporciona funciones que admiten interoperabilidad de D3D.  Permite utilizar sin problemas los recursos de D3D para calcular en código AMP así como permite también el uso de los recursos creados en AMP con código D3D, sin crear copias intermedias redundantes.  Puede acelerar incrementalmente las secciones de cálculo intensivo de las aplicaciones DirectX mediante C\+\+ AMP y utilizar la API D3D en los datos producidos por los cálculos de AMP.  
  
## Sintaxis  
  
```  
namespace direct3d;  
```  
  
## Miembros  
  
### Clases  
  
|Name|Descripción|  
|----------|-----------------|  
|[scoped\_d3d\_access\_lock \(Clase\)](../../../parallel/amp/reference/scoped-d3d-access-lock-class.md)|Un contenedor RAII para un bloqueo de acceso de D3D en un objeto `accelerator_view` .|  
  
### Estructuras  
  
|Name|Descripción|  
|----------|-----------------|  
|[adopt\_d3d\_access\_lock\_t \(Estructura\)](../../../parallel/amp/reference/adopt-d3d-access-lock-t-structure.md)|Tipo de etiqueta para indicar que el bloqueo de acceso de D3D se debe adoptar en lugar de adquirir.|  
  
### Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[abs \(Función\)](../Topic/abs%20Function.md)|Devuelve el valor absoluto del argumento|  
|[clamp \(Función\)](../Topic/clamp%20Function.md)|Sobrecargado.  Ajusta \_X al intervalo \_Min y \_Max especificado|  
|[countbits \(Función\)](../Topic/countbits%20Function.md)|Cuenta el número de bits establecidos en \_X|  
|[create\_accelerator\_view \(Función\)](../Topic/create_accelerator_view%20Function.md)|Crea [accelerator\_view \(Clase\)](../../../parallel/amp/reference/accelerator-view-class.md) a partir de un puntero a una interfaz de dispositivo Direct3D|  
|[d3d\_access\_lock \(Función\)](../Topic/d3d_access_lock%20Function.md)|Adquiere un bloqueo en un accelerator\_view para realizar operaciones D3D con seguridad en recursos compartidos con el accelerator\_view.|  
|[d3d\_access\_try\_lock \(Función\)](../Topic/d3d_access_try_lock%20Function.md)|Intente bloquear el acceso de D3D en accelerator\_view sin bloquearse.|  
|[d3d\_access\_unlock \(Función\)](../Topic/d3d_access_unlock%20Function.md)|Libere el bloqueo de acceso de D3D en el objeto accelerator\_view especificado.|  
|[firstbithigh \(Función\)](../Topic/firstbithigh%20Function.md)|Consigue la ubicación del primer bit establecido en \_X, comenzando desde el bit de mayor peso y en orden descendente|  
|[firstbitlow \(Función\)](../Topic/firstbitlow%20Function.md)|Consigue la ubicación del primer bit establecido en \_X, desde el bit de menor peso en orden ascendente|  
|[get\_buffer \(Función\)](../Topic/get_buffer%20Function.md)|Consiga la interfaz del búfer D3D subyacente a un array.|  
|[imax \(Función\)](../Topic/imax%20Function.md)|Compara dos valores, devolviendo el valor que sea mayor.|  
|[imin \(Función\)](../Topic/imin%20Function.md)|Compara dos valores, devolviendo el valor que sea menor.|  
|[is\_timeout\_disabled \(Función\)](../Topic/is_timeout_disabled%20Function.md)|Devuelve un indicador booleano que indica si el tiempo de espera está deshabilitado para el objeto accelerator\_view especificado.|  
|[mad \(Función\)](../Topic/mad%20Function.md)|Sobrecargado.  Realiza una operación aritmética de multiplicación y suma con tres argumentos: \_X \* \_Y \+ \_Z|  
|[make\_array \(Función\)](../Topic/make_array%20Function.md)|Cree un array de un puntero de la interfaz del búfer D3D.|  
|[noise \(Función\)](../Topic/noise%20Function.md)|Genera un valor aleatorio mediante el algoritmo de ruido de Perlin|  
|[radians \(Función\)](../Topic/radians%20Function.md)|Convierte \_X de grados a radianes|  
|[rcp \(Función\)](../Topic/rcp%20Function.md)|Calcula un recíproco rápido, aproximado del argumento|  
|[reversebits \(Función\)](../Topic/reversebits%20Function.md)|Invierte el orden de los bits en \_X|  
|[saturate \(Función\)](../Topic/saturate%20Function.md)|Ajusta \_X dentro del intervalo de 0 a 1|  
|[sign \(Función\)](../Topic/sign%20Function.md)|Sobrecargado.  Devuelve el signo del argumento|  
|[smoothstep \(Función\)](../Topic/smoothstep%20Function.md)|Devuelve una interpolación suavizada de Hermite entre 0 y 1, si \_X está en el intervalo de \[\_Min, \_Max\].|  
|[step \(Función\)](../Topic/step%20Function.md)|Compara dos valores, devolviendo 0 ó 1 en función del valor que es mayor|  
|[umax \(Función\)](../Topic/umax%20Function.md)|Compara dos valores sin signo, devolviendo el valor que sea mayor.|  
|[umin \(Función\)](../Topic/umin%20Function.md)|Compara dos valores sin signo, devolviendo el valor que sea menor.|  
  
## Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)