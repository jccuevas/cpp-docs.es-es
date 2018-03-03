---
title: Methodreleasenotifier (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 113ea9179292606461a8fe67ff161f63e58161da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier (Clase)
Invoca un controlador de eventos cuando se libera el último objeto en el módulo actual. El controlador de eventos se especifica mediante un objeto y su miembro de puntero a un método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<  
   typename T  
>  
class MethodReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo del objeto cuya función miembro es el controlador de eventos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::MethodReleaseNotifier (constructor)](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|Inicializa una nueva instancia de la clase methodreleasenotifier.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::Invoke (método)](../windows/module-methodreleasenotifier-invoke-method.md)|Llama al controlador de eventos asociado con el objeto de methodreleasenotifier actual.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::method_ (miembro de datos)](../windows/module-methodreleasenotifier-method-data-member.md)|Contiene un puntero al controlador de eventos para el objeto de methodreleasenotifier actual.|  
|[Module::MethodReleaseNotifier::object_ (miembro de datos)](../windows/module-methodreleasenotifier-object-data-member.md)|Contiene un puntero al objeto cuya función miembro es el controlador de eventos para el objeto de methodreleasenotifier actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)