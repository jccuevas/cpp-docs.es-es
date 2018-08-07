---
title: Constructor Mutex | Microsoft Docs
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
ms.openlocfilehash: 7a7549371ba4648f8fcce03a98a021c8027c676e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605199"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex (Constructor)
Inicializa una nueva instancia de la **Mutex** clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *h*  
 Un identificador o una referencia rvalue a un identificador, para un **Mutex** objeto.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor inicializa un **Mutex** objeto a partir del identificador especificado. El segundo constructor inicializa un **Mutex** el objeto en el identificador especificado y, a continuación, mueve la propiedad del mutex actual **Mutex** objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers
 
 ## <a name="see-also"></a>Vea también
 [Mutex (clase)](../windows/mutex-class1.md)