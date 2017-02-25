---
title: "Module::GenericReleaseNotifier (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::GenericReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GenericReleaseNotifier (clase)"
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Module::GenericReleaseNotifier (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica en una expresión lambda, un functor o un puntero a función.  
  
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Genericreleasenotifier (Constructor)](../Topic/Module::GenericReleaseNotifier::GenericReleaseNotifier%20Constructor.md)|Inicializa una nueva instancia de la clase genericreleasenotifier.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Genericreleasenotifier:: Invoke (método)](../windows/module-genericreleasenotifier-invoke-method.md)|Llama al controlador de eventos asociado con el objeto de genericreleasenotifier actual.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Miembro de datos callback_](../windows/module-genericreleasenotifier-callback-data-member.md)|Contiene la expresión lambda, un functor o un controlador de eventos de puntero a función asociado con el objeto de genericreleasenotifier actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)