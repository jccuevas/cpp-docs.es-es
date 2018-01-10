---
title: "Constantes de montón| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
dev_langs: C++
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e2e1a15b371aa4f2997d453e2543123b279ac0df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="heap-constants"></a>Constantes de montón
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <malloc.h>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas constantes proporcionan el valor devuelto mediante la indicación del estado del montón.  
  
|Constante|Significado|  
|--------------|-------------|  
|`_HEAPBADBEGIN`|La información de encabezado inicial no se encontró o no era válida.|  
|`_HEAPBADNODE`|Se encontró un nodo incorrecto o el montón está dañado.|  
|`_HEAPBADPTR`|El campo **_pentry** de la estructura **_HEAPINFO** no contiene un puntero válido en el montón (solo la rutina `_heapwalk`).|  
|`_HEAPEMPTY`|No se ha inicializado el montón.|  
|`_HEAPEND`|Se ha llegado al final del montón correctamente (solo la rutina `_heapwalk`).|  
|`_HEAPOK`|El montón es coherente (solo las rutinas `_heapset` y `_heapchk`). Ningún error hasta el momento; la estructura **_HEAPINFO** contiene información sobre la próxima entrada (solo la rutina `_heapwalk`).|  
  
## <a name="see-also"></a>Vea también  
 [_heapchk](../c-runtime-library/reference/heapchk.md)   
 [_heapset](../c-runtime-library/heapset.md)   
 [_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)