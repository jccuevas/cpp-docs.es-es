---
title: 'Comptr:: operator -&gt; operador | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3cb3571207f328ad044ffd3f2f9b83bcebc7677e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870190"
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