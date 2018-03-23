---
title: AsWeak (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 75d732758bac53edc40aeac50e0184d80145890d
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="asweak-function"></a>AsWeak (función)
Recupera una referencia débil a una instancia especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Un puntero al tipo de parámetro `p`.  
  
 `p`  
 Una instancia de un tipo.  
  
 `pWeak`  
 Cuando se completa esta operación, un puntero a una referencia débil al parámetro `p`.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si esta operación se realiza correctamente; en caso contrario, un error HRESULT que indica la causa del error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)