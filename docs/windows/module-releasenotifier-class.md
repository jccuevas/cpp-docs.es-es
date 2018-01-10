---
title: Releasenotifier (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs: C++
helpviewer_keywords: ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb640f146109363a8025818b3ec560c250029914
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier (Clase)
Invoca un controlador de eventos cuando se libera el último objeto en un módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::ReleaseNotifier::~ReleaseNotifier (destructor)](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Desinicializa la instancia actual de la clase releasenotifier.|  
|[Module::ReleaseNotifier::ReleaseNotifier (constructor)](../windows/module-releasenotifier-releasenotifier-constructor.md)|Inicializa una nueva instancia de la clase releasenotifier.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke (método)](../windows/module-releasenotifier-invoke-method.md)|Cuando se implementa, llama a un controlador de eventos cuando se libera el último objeto en un módulo.|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|Elimina el objeto de releasenotifier actual si el objeto se construyó con un parámetro de `true`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)