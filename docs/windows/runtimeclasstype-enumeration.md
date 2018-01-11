---
title: "RuntimeClassType (enumeración) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClassType
dev_langs: C++
helpviewer_keywords: RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26016e8c95807af76484504c491ca1e6e08f8f96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
|`Delegate`|Equivalente a **ClassicCom**.|  
|`InhibitFtmBase`|Deshabilita `FtmBase` soporte técnico al `__WRL_CONFIGURATION_LEGACY__` no está definido.|  
|`InhibitWeakReference`|Deshabilita la compatibilidad de la referencia débil.|  
|`WinRt`|Una clase en tiempo de ejecución de Windows.|  
|`WinRtClassicComMix`|Combinación de `WinRt` y `ClassicCom`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)