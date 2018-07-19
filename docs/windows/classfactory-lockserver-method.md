---
title: 'ClassFactory:: Lockserver (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e09a795688c7e2b31771126f9e4036ddfbd8e4f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860325"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer (Método)
Incrementa o disminuye el número de subyacente de objetos que se realiza un seguimiento del objeto ClassFactory actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fLock`  
 `true` para incrementar el número de objetos con seguimiento. `false` Para reducir el número de objetos con seguimiento.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_FAIL.  
  
## <a name="remarks"></a>Comentarios  
 ClassFactory realiza un seguimiento de los objetos en una instancia subyacente de la [módulo](../windows/module-class.md) clase.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ClassFactory (clase)](../windows/classfactory-class.md)