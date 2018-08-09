---
title: Constructor Synclockwithstatust | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 21ce2054cabf257594cb3fa376236b9a1e504a59
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647760"
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT (Constructor)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SyncLockWithStatusT(  
   _Inout_ SyncLockWithStatusT&& other  
);  
  
explicit SyncLockWithStatusT(  
   typename SyncTraits::Type sync,  
   DWORD status  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *other*  
 Una referencia rvalue a otro **SyncLockWithStatusT** objeto.  
  
 *sync*  
 Una referencia a otro **SyncLockWithStatusT** objeto.  
  
 *status*  
 El valor de la [status_](../windows/synclockwithstatust-status-data-member.md) miembro de datos de la *otros* parámetro o el *sincronización* parámetro.  
  
## <a name="remarks"></a>Comentarios  
 Inicializa una nueva instancia de la **SyncLockWithStatusT** clase.  
  
 El primer constructor inicializa actual **SyncLockWithStatusT** objeto desde otro **SyncLockWithStatusT** especificado por el parámetro *otros*y, a continuación, invalida el otro **SyncLockWithStatusT** objeto. Es el segundo constructor **protegido**e inicializa actual **SyncLockWithStatusT** objeto a un estado no válido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [SyncLockWithStatusT (clase)](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus (método)](../windows/synclockwithstatust-getstatus-method.md)