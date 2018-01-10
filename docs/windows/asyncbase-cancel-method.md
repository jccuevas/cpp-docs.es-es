---
title: "Asyncbase:: Cancel (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::Cancel
dev_langs: C++
helpviewer_keywords: Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f23cae24cc3009108dd3bdadd7efc396459f0a60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel (Método)
Cancela una operación asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 De forma predeterminada, siempre devuelve S_OK.  
  
## <a name="remarks"></a>Comentarios  
 Cancel() es una implementación predeterminada de IAsyncInfo::Cancel y no lleva a cabo ningún trabajo real. Para realmente cancelar una operación asincrónica, invalide el método virtual puro OnCancel().  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)