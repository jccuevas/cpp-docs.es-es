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
ms.openlocfilehash: 6d4ff3393e30e72bc3378837ff11c41927249d1f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014200"
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT (Constructor)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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