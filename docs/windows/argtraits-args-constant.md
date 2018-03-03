---
title: Argtraits (constante) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits::args
dev_langs:
- C++
helpviewer_keywords:
- args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: baf5f0fa0e95498f677615802b250b56fd94afec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="argtraitsargs-constant"></a>ArgTraits::args (Constante)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static const int args = -1; ;  
```  
  
## <a name="remarks"></a>Comentarios  
 Mantiene el recuento del número de parámetros en el método de invocación de una interfaz de delegado.  
  
## <a name="remarks"></a>Comentarios  
 Cuando `args` es igual a -1 indica que no puede haber ninguna coincidencia para la firma del método Invoke.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [ArgTraits (estructura)](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)