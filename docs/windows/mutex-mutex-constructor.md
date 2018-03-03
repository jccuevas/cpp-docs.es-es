---
title: Constructor Mutex | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a07aeac0f8d139f71bdbe2473dc8eabf7e14ec2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex (Constructor)
Inicializa una nueva instancia de la clase de exclusión mutua.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `h`  
 Un identificador o una referencia de valor r a un identificador a un objeto de exclusión mutua.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor inicializa un objeto de exclusión mutua partir del identificador especificado. El segundo constructor inicializa un objeto de exclusión mutua partir del identificador especificado y, a continuación, pasa la propiedad de la exclusión mutua para el objeto actual de la exclusión mutua.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers
 
 ## <a name="see-also"></a>Vea también
 [Mutex (clase)](../windows/mutex-class1.md)