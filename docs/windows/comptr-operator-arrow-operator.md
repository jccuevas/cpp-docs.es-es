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
ms.openlocfilehash: 1530f7998f2597aeb2fe46dba09f4844b471cd93
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644835"
---
# <a name="comptroperator-gt-operator"></a>Comptr:: operator -&gt; operador
Recupera un puntero al tipo especificado por el parámetro de plantilla actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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