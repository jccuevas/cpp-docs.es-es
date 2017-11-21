---
title: "Método deferrableeventargs:: Getdeferral | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4d43aa6d82f44965e8defda2af3e6455e86cba38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="deferrableeventargsgetdeferral-method"></a>Método DeferrableEventArgs::GetDeferral
Obtiene una referencia a la [aplazamiento](http://go.microsoft.com/fwlink/?LinkId=526520) el objeto que representa un evento diferido.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `result`  
 Un puntero que hará referencia a la [aplazamiento](http://go.microsoft.com/fwlink/?LinkId=526520) objeto cuando se complete la llamada.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo de código, vea [clase DeferrableEventArgs](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [DeferrableEventArgs (clase)](../windows/deferrableeventargs-class.md)