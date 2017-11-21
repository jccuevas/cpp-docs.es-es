---
title: MutexTraits (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
dev_langs: C++
helpviewer_keywords: MutexTraits structure
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eebe8ffefedbc28be1f16a0d02a195d4af4ac0c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="mutextraits-structure"></a>MutexTraits (estructura)
Define las características comunes de la [exclusión mutua](../windows/mutex-class1.md) clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct MutexTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[MutexTraits::Unlock (método)](../windows/mutextraits-unlock-method.md)|Devuelve el control exclusivo de un recurso compartido.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `HANDLENullTraits`  
  
 `MutexTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::HandleTraits (espacio de nombres)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)