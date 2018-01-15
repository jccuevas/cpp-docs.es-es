---
title: Module (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module
dev_langs: C++
helpviewer_keywords: Module class
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d17e0dc79241fbd84e282b9cd8403259e34def0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="module-class"></a>Module (clase)
Representa una colección de objetos relacionados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
template<  
   ModuleType moduleType  
>  
class Module;  
  
template<>  
class Module<InProc> : public Details::ModuleBase;  
  
template<>  
class Module<OutOfProc> : public Module<InProc>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `moduleType`  
 Una combinación de uno o varios [ModuleType](../windows/moduletype-enumeration.md) valores de enumeración.  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-classes"></a>Clases protegidas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier (clase)](../windows/module-genericreleasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto en el módulo actual. El controlador de eventos se especifica por en una expresión lambda, functor o puntero a función.|  
|[Module::MethodReleaseNotifier (clase)](../windows/module-methodreleasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto en el módulo actual. El controlador de eventos se especifica mediante un objeto y su miembro de puntero a un método.|  
|[Module::ReleaseNotifier (clase)](../windows/module-releasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto en un módulo.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::~Module (destructor)](../windows/module-tilde-module-destructor.md)|Desinicializa la instancia actual de la clase de módulo.|  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::Module (constructor)](../windows/module-module-constructor.md)|Inicializa una nueva instancia de la clase de módulo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::Create (método)](../windows/module-create-method.md)|Crea una instancia de un módulo.|  
|[Module::DecrementObjectCount (método)](../windows/module-decrementobjectcount-method.md)|Disminuye el número de objetos cuyo seguimiento realiza el módulo.|  
|[Module::GetActivationFactory (método)](../windows/module-getactivationfactory-method.md)|Obtiene un generador de activación para el módulo.|  
|[Module::GetClassObject (método)](../windows/module-getclassobject-method.md)|Recupera una memoria caché de generadores de clases.|  
|[Module::GetModule (método)](../windows/module-getmodule-method.md)|Crea una instancia de un módulo.|  
|[Module::GetObjectCount (método)](../windows/module-getobjectcount-method.md)|Recupera el número de objetos administrados por este módulo.|  
|[Module::IncrementObjectCount (método)](../windows/module-incrementobjectcount-method.md)|Incrementa el número de objetos que se hace un seguimiento mediante el módulo.|  
|[Module::RegisterCOMObject (método)](../windows/module-registercomobject-method.md)|Registra uno o varios objetos COM para que otras aplicaciones puedan conectarse a ellos.|  
|[Module::RegisterObjects (método)](../windows/module-registerobjects-method.md)|Registra objetos COM o en tiempo de ejecución de Windows para que otras aplicaciones puedan conectarse a ellos.|  
|[Module::RegisterWinRTObject (método)](../windows/module-registerwinrtobject-method.md)|Registra uno o varios objetos en tiempo de ejecución de Windows para que otras aplicaciones puedan conectarse a ellos.|  
|[Module::Terminate (método)](../windows/module-terminate-method.md)|Hace que todos los generadores que crea una instancia del módulo se apague.|  
|[Module::UnregisterCOMObject (método)](../windows/module-unregistercomobject-method.md)|Anula el registro de uno o varios objetos COM, lo que impide que otras aplicaciones conectarse a ellos.|  
|[Module::UnregisterObjects (método)](../windows/module-unregisterobjects-method.md)|Anula el registro de los objetos en el módulo especificado para que otras aplicaciones no se pueden conectar a ellos.|  
|[Module::UnregisterWinRTObject (método)](../windows/module-unregisterwinrtobject-method.md)|Anula el registro de uno o varios objetos en tiempo de ejecución de Windows para que otras aplicaciones no se pueden conectar a ellos.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::Create (método)](../windows/module-create-method.md)|Crea una instancia de un módulo.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Module::objectCount_ (miembro de datos)](../windows/module-objectcount-data-member.md)|Realiza un seguimiento de cuántas clases se hayan creado con la [realizar](../windows/make-function.md) función.|  
|[Module::releaseNotifier_ (miembro de datos)](../windows/module-releasenotifier-data-member.md)|Contiene un puntero a un objeto ReleaseNotifier.|  
  
### <a name="macros"></a>Macros  
  
|||  
|-|-|  
|[ActivatableClass](../windows/activatableclass-macros.md)|Rellena una caché interna que contiene una fábrica que puede crear una instancia de la clase especificada. Esta macro especifica parámetros de identificador de generador y el grupo predeterminado.|  
|[ActivatableClassWithFactory](../windows/activatableclass-macros.md)|Rellena una caché interna que contiene una fábrica que puede crear una instancia de la clase especificada. Esta macro le permite especificar un parámetro de generador determinada.|  
|[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)|Rellena una caché interna que contiene una fábrica que puede crear una instancia de la clase especificada. Esta macro permite especificar generador determinado y parámetros de identificador de grupo.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ModuleBase`  
  
 `Module`  
  
 `Module`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)