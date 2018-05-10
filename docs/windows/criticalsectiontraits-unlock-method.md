---
title: 'Criticalsectiontraits:: Unlock (método) | Documentos de Microsoft'
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
ms.openlocfilehash: 35a632a6c88ed29ef5e30e942c1341246de75e71
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock (Método)
Una plantilla CriticalSection se especializa para que admita liberando propiedad del objeto de sección crítica especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cs`  
 Un puntero a un objeto de sección crítica.  
  
## <a name="remarks"></a>Comentarios  
 El *tipo* modificador se define como `typedef CRITICAL_SECTION* Type;`.  
  
 Para obtener más información, vea "LeaveCriticalSection función" en la sección "Funciones de sincronización" de la documentación de API de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [CriticalSectionTraits (estructura)](../windows/criticalsectiontraits-structure.md)