---
title: Lockserver (método) | Microsoft Docs
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
ms.openlocfilehash: 654ef60c924a14e861971c651899c8baea0300ef
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462711"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer (Método)
Incrementa o disminuye el número de subyacentes de objetos que se realiza el seguimiento actual **ClassFactory** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *manada*  
 **True** para incrementar el número de objetos con seguimiento. **false** para reducir el número de objetos con seguimiento.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_FAIL.  
  
## <a name="remarks"></a>Comentarios  
 ClassFactory realiza un seguimiento de los objetos en una instancia subyacente de la [módulo](../windows/module-class.md) clase.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ClassFactory (clase)](../windows/classfactory-class.md)