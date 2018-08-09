---
title: AsWeak (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0f4645a6008b954833bf282971a0d3912e1d598
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653149"
---
# <a name="asweak-function"></a>AsWeak (función)
Recupera una referencia débil a una instancia especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template<typename T>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 Un puntero al tipo de parámetro *p*.  
  
 *p*  
 Una instancia de un tipo.  
  
 *pWeak*  
 Cuando finalice esta operación, un puntero a una referencia débil al parámetro *p*.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si esta operación se realiza correctamente; en caso contrario, un error HRESULT que indica la causa del error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)