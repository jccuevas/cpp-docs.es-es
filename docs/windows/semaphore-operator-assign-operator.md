---
title: 'Semaphore:: operator = (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49405cda5ff7a9d3313ebafbda35b5fb6182febe
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015512"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= (Operador)
Mueve el identificador especificado de un **semáforo** el objeto actual **semáforo** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
Semaphore& operator=(  
   _Inout_ Semaphore&& h  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *h*  
 Referencia de valor r a un **semáforo** objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Una referencia a la actual **semáforo** objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers
 
 ## <a name="see-also"></a>Vea también
 [Semaphore (clase)](../windows/semaphore-class.md)