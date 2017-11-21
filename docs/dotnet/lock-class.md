---
title: lock (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs: C++
helpviewer_keywords: lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2c9e21612c227081e3558a8f7f3161f922711c20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="lock-class"></a>lock (Clase)
Esta clase automatiza tomar un bloqueo para sincronizar el acceso a un objeto desde varios subprocesos.  Al construir adquiere el bloqueo y cuando se destruye versiones el bloqueo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>Comentarios  
 `lock`solo está disponible para objetos CLR y solo puede usarse en código CLR.  
  
 Internamente, los usos de la clase de bloqueo <xref:System.Threading.Monitor> para sincronizar el acceso. Vea este tema para obtener más información acerca de la sincronización.  
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Vea también  
 [bloqueo](../dotnet/lock.md)   
 [lock (Miembros)](../dotnet/lock-members.md)