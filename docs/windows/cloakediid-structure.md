---
title: CloakedIid (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
dev_langs:
- C++
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e0155006987165f5b192aac73bb31991081a231
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461228"
---
# <a name="cloakediid-structure"></a>CloakedIid (estructura)
Indica a la `RuntimeClass`, `Implements` y `ChainInterfaces` plantillas que la interfaz especificada no es accesible en la lista IID.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T>  
struct CloakedIid : T;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 La interfaz que está oculto (escondida).  
  
## <a name="remarks"></a>Comentarios  
 El siguiente es un ejemplo de cómo `CloakedIid` sirve: `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `T`  
  
 `CloakedIid`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)