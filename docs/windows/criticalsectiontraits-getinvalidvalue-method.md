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
ms.openlocfilehash: cf0d52769052a36c0b494d19204dd6c07f0b2404
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463390"
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue (Método)
Se especializa un **CriticalSection** plantilla para que la plantilla no siempre es válida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline static Type GetInvalidValue();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve un puntero a una sección crítica no válida.  
  
## <a name="remarks"></a>Comentarios  
 El *tipo* modificador se define como `typedef CRITICAL_SECTION* Type;`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [CriticalSectionTraits (estructura)](../windows/criticalsectiontraits-structure.md)