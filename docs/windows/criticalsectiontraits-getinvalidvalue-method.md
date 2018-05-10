---
title: 'Criticalsectiontraits:: Getinvalidvalue (método) | Documentos de Microsoft'
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
ms.openlocfilehash: d72c9dce0765029ee31e079315baec72afd16a46
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue (Método)
Una plantilla CriticalSection se especializa para que la plantilla no siempre es válida.  
  
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