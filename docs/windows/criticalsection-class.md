---
title: CriticalSection (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection class
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b65ded3ae56eb1d57bad771a8875cce4948d2953
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642101"
---
# <a name="criticalsection-class"></a>CriticalSection (clase)
Representa un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
class CriticalSection;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="constructor"></a>Constructor  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CriticalSection::CriticalSection (constructor)](../windows/criticalsection-criticalsection-constructor.md)|Inicializa un objeto de sincronización que es similar a un objeto de exclusión mutua, pero se puede usar solo los subprocesos de un único proceso.|  
|[CriticalSection::~CriticalSection (destructor)](../windows/criticalsection-tilde-criticalsection-destructor.md)|Desinicializa y destruye actual **CriticalSection** objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CriticalSection::TryLock (método)](../windows/criticalsection-trylock-method.md)|Intenta entrar en una sección crítica sin bloquear. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión de la sección crítica.|  
|[CriticalSection::Lock (método)](../windows/criticalsection-lock-method.md)|Espera a que la propiedad del objeto especificado de sección crítica. La función devuelve cuando el subproceso de llamada se concede la propiedad.|  
|[CriticalSection::IsValid (método)](../windows/criticalsection-isvalid-method.md)|Indica si la sección crítica actual es válida.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CriticalSection::cs_ (miembro de datos)](../windows/criticalsection-cs-data-member.md)|Declara a un miembro de datos de la sección crítica.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CriticalSection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)