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
ms.openlocfilehash: 9fb3cd0a4c180073499ec1bdde1ea4703ffbf9e8
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207857"
---
# <a name="comptrrefoperator-void-operator"></a>Comptrref:: operator void\* \* operador
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
operator void**() const;  
```  
  
## <a name="remarks"></a>Comentarios  
 Elimina el objeto ComPtrRef actual, convierte el puntero a la interfaz que se ha representado por el objeto ComPtrRef como un puntero-a-puntero-to `void`y, a continuación, devuelve el puntero de conversión.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [ComPtrRef (clase)](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)
