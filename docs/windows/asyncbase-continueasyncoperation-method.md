---
title: 'Asyncbase:: Continueasyncoperation (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs:
- C++
helpviewer_keywords:
- ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: caf7cd1cbee97761c6877ec6ab3a51ea956cbfd1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859597"
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation (Método)
Determina si la operación asincrónica debe seguir procesándose o debería detenerse.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 `true` Si el estado actual de la operación asincrónica es *iniciado*, lo que significa que la operación debe continuar. En caso contrario, `false`, lo que significa que la operación debe detenerse.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)