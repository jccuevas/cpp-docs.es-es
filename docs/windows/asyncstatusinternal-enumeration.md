---
title: AsyncStatusInternal (enumeración) | Documentos de Microsoft
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
ms.openlocfilehash: 150169442aa68395b4dc8a4f4c74951e877f18f5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal (enumeración)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Comentarios  
 Especifica una asignación entre enumeraciones internas para el estado de operaciones asincrónicas y el **Windows::Foundation::AsyncStatus** enumeración.  
  
## <a name="members"></a>Miembros  
 `_Created`  
 Equivalente a:: Windows::Foundation::AsyncStatus:: creado  
  
 `_Started`  
 Equivalente a:: Windows::Foundation::AsyncStatus:: iniciado  
  
 `_Completed`  
 Equivalente a:: Windows::Foundation::AsyncStatus:: completado  
  
 `_Cancelled`  
 Equivalente a:: Windows::Foundation::AsyncStatus:: cancelada  
  
 `_Error`  
 Equivalente a:: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)