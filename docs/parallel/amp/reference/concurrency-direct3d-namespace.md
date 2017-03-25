---
title: Namespace Concurrency::Direct3D | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
dev_langs:
- C++
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
caps.latest.revision: 15
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 94e0542910484166a01bd79beb9dfaa805aae6cd
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d (Espacio de nombres)
El `direct3d` espacio de nombres proporciona funciones que admiten interoperabilidad de D3D. Permite el uso sin problemas de recursos D3D para el cálculo en el código de AMP, así como permitir el uso de recursos creados con AMP en código D3D, sin crear copias intermedias redundantes. Incrementalmente puede acelerar las secciones de cálculo intensivo de las aplicaciones DirectX mediante C++ AMP y usar la API D3D en los datos producidos a partir de cálculos de AMP.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace direct3d;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="classes"></a>Clases  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[scoped_d3d_access_lock (clase)](scoped-d3d-access-lock-class.md)|Un contenedor RAII D3D acceso de bloqueo para una `accelerator_view` objeto.|  
  
### <a name="structures"></a>Estructuras  
  
|Name|Descripción|  
|----------|-----------------|  
|[adopt_d3d_access_lock_t (estructura)](adopt-d3d-access-lock-t-structure.md)|Tipo de etiqueta para indicar el bloqueo de acceso D3D debe se adoptado en lugar de adquirir.|  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|Devuelve el valor absoluto del argumento|  
|[Clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|Sobrecargado. Fija _X al rango especificado de _Min y _Max|  
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|Cuenta el número de bits de conjunto de _X|  
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Crea un [accelerator_view (clase)](accelerator-view-class.md) de un puntero a una interfaz de dispositivo Direct3D|  
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Adquiere un bloqueo en un accelerator_view con el fin de forma segura las operaciones de D3D en recursos compartidos con el accelerator_view|  
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Intenta adquirir el bloqueo de acceso de D3D en un accelerator_view sin bloqueo.|  
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Liberar el bloqueo de acceso de D3D en los accelerator_view determinado.|  
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Obtiene la ubicación del primer bit establecido en _X, empezando desde el bit de orden superior y continuando hacia abajo|  
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Obtiene la ubicación del primer bit establecido en _X, empezando por el bit de orden más bajo y trabajar hacia arriba|  
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Obtener la interfaz del búfer de D3D subyacente de una matriz.|  
|[iMax](concurrency-direct3d-namespace-functions-amp.md#imax)|Compara dos valores y devuelve el valor que sea mayor.|  
|[imin)](concurrency-direct3d-namespace-functions-amp.md#imin)|Compara dos valores y devuelve el valor que sea menor.|  
|[is_timeout_disabled)](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Devuelve una marca booleana que indica si el tiempo de espera está deshabilitada para el accelerator_view especificado.|  
|[MAD](concurrency-direct3d-namespace-functions-amp.md#mad)|Sobrecargado. Realiza una operación aritmética para multiplicar o agregue en tres argumentos: _X * _Y + _Z|  
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Cree una matriz de un puntero de interfaz de búfer de D3D.|  
|[ruido](concurrency-direct3d-namespace-functions-amp.md#noise)|Genera un valor aleatorio mediante el algoritmo de ruido de Perlin|  
|[radianes](concurrency-direct3d-namespace-functions-amp.md#radians)|Convierte _X de grados a radianes|  
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|Calcula un recíproco rápida y aproximado del argumento|  
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Invierte el orden de los bits de _X|  
|[saturar](concurrency-direct3d-namespace-functions-amp.md#saturate)|Fija _X dentro del intervalo de 0 a 1|  
|[inicio de sesión](concurrency-direct3d-namespace-functions-amp.md#sign)|Sobrecargado. Devuelve el signo del argumento|  
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Devuelve una interpolación Hermite suave entre 0 y 1, si _X está en el intervalo [_Min, _Max].|  
|[paso](concurrency-direct3d-namespace-functions-amp.md#step)|Compara dos valores y devuelve 0 o 1 según cuyo valor es mayor|  
|[UMAX](concurrency-direct3d-namespace-functions-amp.md#umax)|Compara dos valores sin signo, devolver el valor que sea mayor.|  
|[umin)](concurrency-direct3d-namespace-functions-amp.md#umin)|Compara dos valores sin signo, devolver el valor que sea menor.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

