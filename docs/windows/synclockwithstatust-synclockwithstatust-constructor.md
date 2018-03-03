---
title: Constructor de Synclockwithstatust | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc5be4a37182cb23b47a2511d2e7d5eb0ffa558a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT (Constructor)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `other`  
 Una referencia a valor r a otro objeto de SyncLockWithStatusT.  
  
 `sync`  
 Una referencia a otro objeto de SyncLockWithStatusT.  
  
 `status`  
 El valor de la [status_](../windows/synclockwithstatust-status-data-member.md) miembro de datos de la `other` parámetro o el `sync` parámetro.  
  
## <a name="remarks"></a>Comentarios  
 Inicializa una nueva instancia de la clase de SyncLockWithStatusT.  
  
 El primer constructor inicializa el objeto de SyncLockWithStatusT actual de SyncLockWithStatusT otro especificado por el parámetro `other`y, a continuación, se invalidan el otro objeto de SyncLockWithStatusT. El segundo constructor es `protected`y se inicializa el objeto de SyncLockWithStatusT actual en un estado no válido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [SyncLockWithStatusT (clase)](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus (método)](../windows/synclockwithstatust-getstatus-method.md)