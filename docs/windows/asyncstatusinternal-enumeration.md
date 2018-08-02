---
title: AsyncStatusInternal (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs:
- C++
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a68189c461453dc72585ff4034df5ba69bb41bd5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464881"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal (enumeración)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Comentarios  
 Especifica una asignación entre enumeraciones internas para el estado de las operaciones asincrónicas y la `Windows::Foundation::AsyncStatus` enumeración.  
  
## <a name="members"></a>Miembros  
 *_Creado*  
 Equivalente a:: Windows::Foundation::AsyncStatus:: creado  
  
 *_Started*  
 Equivalente a:: Windows::Foundation::AsyncStatus:: a  
  
 *_Completed*  
 Equivalente a:: Windows::Foundation::AsyncStatus:: completado  
  
 *_Cancelled*  
 Equivalente a:: Windows::Foundation::AsyncStatus:: cancelada  
  
 *_Error*  
 Equivalente a:: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)