---
title: Constructor Mutex | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb7782e44fc8598ca3b806ef922f8d0840765e28
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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