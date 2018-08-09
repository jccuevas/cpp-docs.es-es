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
ms.openlocfilehash: eee563a52a24d2b78157b640ae6e84217c03af64
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651283"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= (Operador)
Mueve el identificador especificado de un **semáforo** el objeto actual **semáforo** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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