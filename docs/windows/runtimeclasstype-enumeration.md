---
title: RuntimeClassType (enumeración) | Documentos de Microsoft
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
ms.openlocfilehash: 43ab0a738af4c6bc92d42c0884827b574946d2ea
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892408"
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