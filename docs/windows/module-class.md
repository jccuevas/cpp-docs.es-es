---
title: "Module (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Module (clase)"
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Module (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa una colección de objetos relacionados.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `moduleType`  
 Una combinación de uno o más valores de enumeración de [ModuleType](../Topic/ModuleType%20Enumeration.md) .  
  
## Miembros  
  
### Clases protegidas  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier \(Clase\)](../windows/module-genericreleasenotifier-class.md)|Invoca un controlador de eventos cuando el objeto pasado en el módulo actual se libera.  Especifique el controlador de eventos mediante en una expresión lambda, un functor, o una puntero\-a\- función.|  
|[Module::MethodReleaseNotifier \(Clase\)](../Topic/Module::MethodReleaseNotifier%20Class.md)|Invoca un controlador de eventos cuando el objeto pasado en el módulo actual se libera.  Al miembro del puntero\-a\-uno\- método especifica el controlador de eventos recibe un objeto y.|  
|[Module::ReleaseNotifier \(Clase\)](../Topic/Module::ReleaseNotifier%20Class.md)|Invoca un controlador de eventos cuando el objeto pasado en un módulo se libera.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::~Module \(Destructor\)](../windows/module-tilde-module-destructor.md)|Desinicializa la instancia actual de la clase de módulo.|  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::Module \(Constructor\)](../windows/module-module-constructor.md)|Inicializa una nueva instancia de la clase de módulo.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::Create \(Método\)](../windows/module-create-method.md)|Crea una instancia de un módulo.|  
|[Module::DecrementObjectCount \(Método\)](../windows/module-decrementobjectcount-method.md)|Reduzca el número de objetos seguidos del módulo.|  
|[Module::GetActivationFactory \(Método\)](../windows/module-getactivationfactory-method.md)|Obtiene un generador de activación del módulo.|  
|[Module::GetClassObject \(Método\)](../windows/module-getclassobject-method.md)|Retreives caché de generadores de clases.|  
|[Module::GetModule \(Método\)](../Topic/Module::GetModule%20Method.md)|Crea una instancia de un módulo.|  
|[Module::GetObjectCount \(Método\)](../windows/module-getobjectcount-method.md)|Recupera el número de objetos administrados por este módulo.|  
|[Module::IncrementObjectCount \(Método\)](../windows/module-incrementobjectcount-method.md)|Aumenta el número de objetos seguidos del módulo.|  
|[Module::RegisterCOMObject \(Método\)](../windows/module-registercomobject-method.md)|Registra uno o más objetos COM de modo que otras aplicaciones pueden conectarse a ellos.|  
|[Module::RegisterObjects \(Método\)](../windows/module-registerobjects-method.md)|Los registros COM o los objetos de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] así que otras aplicaciones pueden conectarse a ellas.|  
|[Module::RegisterWinRTObject \(Método\)](../windows/module-registerwinrtobject-method.md)|Registra uno o más objetos de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] así que otras aplicaciones pueden conectarse a ellos.|  
|[Module::Terminate \(Método\)](../windows/module-terminate-method.md)|Hace que todas las generadores cuya instancia por módulo para cerrar.|  
|[Module::UnregisterCOMObject \(Método\)](../Topic/Module::UnregisterCOMObject%20Method.md)|Anula uno o más objetos COM, lo que evita que otras aplicaciones se conecten con ellos.|  
|[Module::UnregisterObjects \(Método\)](../windows/module-unregisterobjects-method.md)|Anula los objetos en el módulo especificado para que otras aplicaciones no pueden conectarse a ellos.|  
|[Module::UnregisterWinRTObject \(Método\)](../windows/module-unregisterwinrtobject-method.md)|Anula uno o más objetos de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] de modo que otras aplicaciones no pueden conectarse a ellos.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::Create \(Método\)](../windows/module-create-method.md)|Crea una instancia de un módulo.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Module::objectCount\_ \(Miembro de datos\)](../windows/module-objectcount-data-member.md)|Seguimiento de cuántas clases se han creado con la función de [Cree](../windows/make-function.md) .|  
|[Module::releaseNotifier\_ \(Miembro de datos\)](../windows/module-releasenotifier-data-member.md)|Contiene un puntero a un objeto de ReleaseNotifier.|  
  
### Macros  
  
|||  
|-|-|  
|[ActivatableClass](../Topic/ActivatableClass%20Macros.md)|Rellena la caché interna que contiene un generador que pueda crear una instancia de la clase especificada.  Esta macro especifica parámetros predeterminados de generador y el identificador del grupo.|  
|[ActivatableClassWithFactory](../Topic/ActivatableClass%20Macros.md)|Rellena la caché interna que contiene un generador que pueda crear una instancia de la clase especificada.  Esta macro permite especificar un parámetro determinado de generador.|  
|[ActivatableClassWithFactoryEx](../Topic/ActivatableClass%20Macros.md)|Rellena la caché interna que contiene un generador que pueda crear una instancia de la clase especificada.  Esta macro permite especificar parámetros específicos del generador y el identificador del grupo.|  
  
## Jerarquía de herencia  
 `ModuleBase`  
  
 `Module`  
  
 `Module`  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)