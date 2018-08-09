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
ms.openlocfilehash: b64f44e2188848a25e607c53171e25aa721e9bc4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641371"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock (Método)
Se especializa un `CriticalSection` plantilla, por lo que admite liberar la propiedad del objeto especificado de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *CS*  
 Un puntero a un objeto de sección crítica.  
  
## <a name="remarks"></a>Comentarios  
 El `Type` modificador se define como `typedef CRITICAL_SECTION* Type;`.  
  
 Para obtener más información, consulte **LeaveCriticalSection función** en el **funciones de sincronización** sección de la documentación de API de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [CriticalSectionTraits (estructura)](../windows/criticalsectiontraits-structure.md)