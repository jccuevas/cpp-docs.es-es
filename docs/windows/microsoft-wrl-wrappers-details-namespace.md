---
title: Wrappers Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
dev_langs:
- C++
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f74f8fe3e5b637869af7b03bb2eaf5e13df9550
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020172"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details (Espacio de nombres)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
namespace Microsoft::WRL::Wrappers::Details;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="classes"></a>Clases  
  
|Name|Descripción|  
|----------|-----------------|  
|[SyncLockT (clase)](../windows/synclockt-class.md)|Representa un tipo que puede tardar exclusivo o propiedad compartida de un recurso.|  
|[SyncLockWithStatusT (clase)](../windows/synclockwithstatust-class.md)|Representa un tipo que puede tardar exclusivo o propiedad compartida de un recurso.|  
  
### <a name="methods"></a>Métodos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CompareStringOrdinal (método)](../windows/comparestringordinal-method.md)|Compara dos especificado `HSTRING` objetos y devuelve un entero que indica su posición relativa en un criterio de ordenación.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)