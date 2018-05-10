---
title: 'Asyncbase:: Fireprogress (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireProgress
dev_langs:
- C++
helpviewer_keywords:
- FireProgress method
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c2c5aab609b597c3a9ff464b868ba831889deed
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="asyncbasefireprogress-method"></a>AsyncBase::FireProgress (Método)
Se invoca el controlador de eventos de progreso actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `arg`  
 Método de controlador de eventos que se va a invocar.  
  
## <a name="remarks"></a>Comentarios  
 `ProgressTraits` se deriva de [ArgTraitsHelper (estructura)](../windows/argtraitshelper-structure.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)