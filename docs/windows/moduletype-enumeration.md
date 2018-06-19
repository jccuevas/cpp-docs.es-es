---
title: ModuleType (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
dev_langs:
- C++
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d36355c9f64f9f5c827ef8c4d5b3cb6a77d17b65
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876841"
---
# <a name="moduletype-enumeration"></a>ModuleType (enumeración)
Especifica si un módulo debe admitir un servidor en proceso o un servidor fuera de proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum ModuleType;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`InProc`|Un servidor en proceso.|  
|`OutOfProc`|Un servidor fuera de proceso.|  
|`DisableCaching`|Deshabilitar el mecanismo de almacenamiento en caché en el módulo.|  
|`InProcDisableCaching`|Combinación de `InProc` y `DisableCaching`.|  
|`OutOfProcDisableCaching`|Combinación de `OutOfProc` y `DisableCaching`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)