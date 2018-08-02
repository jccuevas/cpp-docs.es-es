---
title: 'Comptr:: operator -&gt; operador | Microsoft Docs'
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
ms.openlocfilehash: 0ff18dee2b8d951ab9233e92478eb967e4a02eb9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464303"
---
# <a name="comptroperator-gt-operator"></a>Comptr:: operator -&gt; operador
Recupera un puntero al tipo especificado por el parámetro de plantilla actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Puntero al tipo especificado por el nombre de tipo de plantilla actual.  
  
## <a name="remarks"></a>Comentarios  
 Esta función auxiliar quita deberse al uso de la macro STDMETHOD una sobrecarga innecesaria. Esta función realiza `IUnknown` tipos **privada** en lugar de **virtual**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)