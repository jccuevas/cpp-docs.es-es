---
title: Método Criticalsectiontraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 01efd9bf3941a5b19e1f0fe6c106d47f1b6e9fcf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642066"
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue (Método)
Se especializa un **CriticalSection** plantilla para que la plantilla no siempre es válida.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline static Type GetInvalidValue();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve un puntero a una sección crítica no válida.  
  
## <a name="remarks"></a>Comentarios  
 El `Type` modificador se define como `typedef CRITICAL_SECTION* Type;`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [CriticalSectionTraits (estructura)](../windows/criticalsectiontraits-structure.md)