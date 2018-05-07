---
title: lock (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a860f79b740e0f34eef33b7a96e0236835f1f6b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="lock-class"></a>lock (Clase)
Esta clase automatiza tomar un bloqueo para sincronizar el acceso a un objeto desde varios subprocesos.  Al construir adquiere el bloqueo y cuando se destruye versiones el bloqueo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>Comentarios  
 `lock` solo está disponible para objetos CLR y solo puede usarse en código CLR.  
  
 Internamente, los usos de la clase de bloqueo <xref:System.Threading.Monitor> para sincronizar el acceso. Vea este tema para obtener más información acerca de la sincronización.  
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Vea también  
 [lock](../dotnet/lock.md)   
 [lock (Miembros)](../dotnet/lock-members.md)