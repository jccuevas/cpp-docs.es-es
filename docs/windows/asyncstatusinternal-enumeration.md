---
title: "AsyncStatusInternal (enumeración) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs: C++
helpviewer_keywords: AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd277fecb0bc63d5ee823af98df8aa298b285964
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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