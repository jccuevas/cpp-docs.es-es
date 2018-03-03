---
title: "Asyncbase:: Close (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35b7fda0ab10ff80df0f4a27f6e79028e73574fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close (Método)
Cierra la operación asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si la operación se cierra o ya está cerrado; en caso contrario, E_ILLEGAL_STATE_CHANGE.  
  
## <a name="remarks"></a>Comentarios  
 Close() es una implementación predeterminada de IAsyncInfo::Close y no lleva a cabo ningún trabajo real. Para cerrar realmente una operación asincrónica, invalide el método virtual puro OnClose().  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)