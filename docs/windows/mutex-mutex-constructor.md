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
ms.openlocfilehash: d87c07f7fa4f1dfa6cbb34545d74d75e8a867583
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017089"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex (Constructor)
Inicializa una nueva instancia de la **Mutex** clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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