---
title: 'Comptrref:: operator void ** (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
dev_langs:
- C++
helpviewer_keywords:
- operator void** operator
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bbe9f077fd0d80a831d319660be26090ad5411f6
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463858"
---
# <a name="comptrrefoperator-void-operator"></a>Comptrref:: operator void\* \* operador
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
operator void**() const;  
```  
  
## <a name="remarks"></a>Comentarios  
 Elimina la actual **ComPtrRef** de objetos, convierte el puntero a la interfaz que se ha representado por la **ComPtrRef** objeto como un puntero-a-puntero-to **void**y, a continuación, Devuelve el puntero de conversión.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [ComPtrRef (clase)](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)