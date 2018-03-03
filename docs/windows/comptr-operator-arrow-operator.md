---
title: 'Comptr:: operator -&gt; operador | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c70c37523132d06bfb04c86cf6f737109da43e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comptroperator-gt-operator"></a>Comptr:: operator -&gt; (operador)
Recupera un puntero al tipo especificado por el parámetro de plantilla actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Puntero al tipo especificado por el nombre de tipo de plantilla actual.  
  
## <a name="remarks"></a>Comentarios  
 Esta función auxiliar quita provocada cuando se usa la macro STDMETHOD una sobrecarga innecesaria. Esta función realiza IUnknown tipos privado a virtual.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)