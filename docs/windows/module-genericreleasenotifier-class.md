---
title: Genericreleasenotifier (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier class
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e850c90ef873e64352ace64ff680cd93474a4a1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606428"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier (Clase)
Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica por en una expresión lambda, functor o puntero a función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 El tipo del miembro de datos que contiene la ubicación del controlador de eventos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier (constructor)](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|Inicializa una nueva instancia de la **genericreleasenotifier** clase.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::Invoke (método)](../windows/module-genericreleasenotifier-invoke-method.md)|Llama al controlador de eventos asociado con el actual **genericreleasenotifier** objeto.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_ (miembro de datos)](../windows/module-genericreleasenotifier-callback-data-member.md)|Contiene la lambda, functor o el controlador de eventos de puntero a función asociado con el actual **genericreleasenotifier** objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)