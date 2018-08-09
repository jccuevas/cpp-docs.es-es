---
title: Constructor Synclockt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT, constructor
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ceaafd6230e6497ed2b7636ad5070141546cb8d6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648170"
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT (Constructor)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SyncLockT(  
   _Inout_ SyncLockT&& other  
);  
  
explicit SyncLockT(  
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *other*  
 Una referencia rvalue a otro **SyncLockT** objeto.  
  
 *sync*  
 Una referencia a otro `SyncLockWithStatusT` objeto.  
  
## <a name="remarks"></a>Comentarios  
 Inicializa una nueva instancia de la **SyncLockT** clase.  
  
 El primer constructor inicializa actual **SyncLockT** objeto desde otro **SyncLockT** objeto especificado por el parámetro *otros*y, a continuación, se invalidan los otros  **SyncLockT** objeto. Es el segundo constructor **protegido**e inicializa actual **SyncLockT** objeto a un estado no válido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [SyncLockT (clase)](../windows/synclockt-class.md)