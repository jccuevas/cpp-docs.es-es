---
title: Método Criticalsectiontraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2f66f185692c200ea459b88363143c0cc1af9d55
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466015"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock (Método)
Se especializa en una plantilla CriticalSection para que admita liberar la propiedad del objeto especificado de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *CS*  
 Un puntero a un objeto de sección crítica.  
  
## <a name="remarks"></a>Comentarios  
 El *tipo* modificador se define como `typedef CRITICAL_SECTION* Type;`.  
  
 Para obtener más información, consulte "Function LeaveCriticalSection" en la sección "Funciones de sincronización" de la documentación de API de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [CriticalSectionTraits (estructura)](../windows/criticalsectiontraits-structure.md)