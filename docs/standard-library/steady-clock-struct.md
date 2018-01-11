---
title: steady_clock (Struct) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: chrono/std::chrono::steady_clock
dev_langs: C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5cd10ebcb9a068e78109c1a232b04c6beff9ebac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="steadyclock-struct"></a>Struct steady_clock
Representa un reloj `steady`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct steady_clock;  
```  
  
## <a name="remarks"></a>Comentarios  
 En Windows, steady_clock ajusta la función QueryPerformanceCounter.  
  
 Un reloj es *monotónico* si el valor devuelto por la primera llamada a `now()` siempre es menor o igual que el valor devuelto por una llamada posterior a `now()`.  
  
 Un reloj es *constante* si es *monotónico* y si el tiempo entre los ciclos de reloj es constante.  
  
 High_resolution_clock es un elemento typdef para steady_clock.  
  
## <a name="public-functions"></a>Funciones públicas  
  
|Función|Descripción|  
|--------------|-----------------|  
|now|Devuelve la hora actual como un valor time_point.|  
  
## <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|`system_clock::is_steady`|Contiene `true`. `steady_clock` es *constante*.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<chrono >  
  
 **Espacio de nombres:** std::chrono  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)   
 [system_clock (Estructura)](../standard-library/system-clock-structure.md)
