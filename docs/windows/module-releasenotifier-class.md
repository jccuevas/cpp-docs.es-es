---
title: Releasenotifier (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97c998f7e0814c5acae55dd3e9b747faed0242e1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016228"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier (Clase)
Invoca un controlador de eventos cuando se libera el último objeto de un módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::ReleaseNotifier::~ReleaseNotifier (destructor)](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Desinicializa la instancia actual de la **releasenotifier** clase.|  
|[Module::ReleaseNotifier::ReleaseNotifier (constructor)](../windows/module-releasenotifier-releasenotifier-constructor.md)|Inicializa una nueva instancia de la **releasenotifier** clase.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke (método)](../windows/module-releasenotifier-invoke-method.md)|Cuando se implementa, llama a un controlador de eventos cuando se libera el último objeto de un módulo.|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|Elimina la actual **releasenotifier** objeto si el objeto se construyó con un parámetro de **true**.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)