---
title: RuntimeClassType (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4464d236a85e06bf907f738657a4a0707e14a5e1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603506"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType (enumeración)
Especifica el tipo de [RuntimeClass](../windows/runtimeclass-class.md) instancia que se admite.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum RuntimeClassType;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`ClassicCom`|Una clase de tiempo de ejecución COM clásica.|  
|`Delegate`|Equivalente a `ClassicCom`.|  
|`InhibitFtmBase`|Deshabilita `FtmBase` compatibilidad con mientras `__WRL_CONFIGURATION_LEGACY__` no está definido.|  
|`InhibitWeakReference`|Deshabilita la compatibilidad de la referencia débil.|  
|`WinRt`|Una clase en tiempo de ejecución de Windows.|  
|`WinRtClassicComMix`|Combinación de `WinRt` y `ClassicCom`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)