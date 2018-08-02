---
title: Continueasyncoperation (método) | Microsoft Docs
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
ms.openlocfilehash: e7b5d2b10b571a3517beab98eaa839d5c7fd86c2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460838"
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation (Método)
Determina si la operación asincrónica, debe continuar el procesamiento o debería detenerse.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si el estado actual de la operación asincrónica es *iniciado*, lo que significa que la operación debe continuar. En caso contrario, **false**, lo que significa que la operación debe detenerse.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)