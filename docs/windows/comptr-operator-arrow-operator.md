---
title: 'Comptr:: operator -&gt; operador | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator->
dev_langs: C++
helpviewer_keywords: operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 28ac6f7dfc4e53e6aadc4fd082e10a0325124ee0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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