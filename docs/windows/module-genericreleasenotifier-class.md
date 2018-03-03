---
title: Genericreleasenotifier (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier class
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c87205d1d52c8273ac7eea55fcc5385810349f1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier (Clase)
Invoca un controlador de eventos cuando se libera el último objeto en el módulo actual. El controlador de eventos se especifica por en una expresión lambda, functor o puntero a función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<  
   typename T  
>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo del miembro de datos que contiene la ubicación del controlador de eventos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier (constructor)](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|Inicializa una nueva instancia de la clase genericreleasenotifier.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::Invoke (método)](../windows/module-genericreleasenotifier-invoke-method.md)|Llama al controlador de eventos asociado con el objeto de genericreleasenotifier actual.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_ (miembro de datos)](../windows/module-genericreleasenotifier-callback-data-member.md)|Contiene la expresión lambda, functor o controlador de eventos de puntero a función asociado con el objeto de genericreleasenotifier actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)