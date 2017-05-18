---
title: steady_clock (Struct) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: 14
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 332008ed313eeae7f04f39165424a9280c2aed8c
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|`system_clock::is_steady`|Contiene `true`. `steady_clock` es *constante*.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<chrono >  
  
 **Espacio de nombres:** std::chrono  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)   
 [system_clock (Estructura)](../standard-library/system-clock-structure.md)

