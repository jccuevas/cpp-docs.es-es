---
title: "IRunnableObjectImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IRunnableObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores, running controls"
  - "controles [ATL], ejecutar"
  - "controles [C++], container running in ATL"
  - "IRunnableObject, implementación de ATL"
  - "IRunnableObjectImpl class"
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IRunnableObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa **IUnknown** y proporciona una implementación predeterminada de la interfaz de [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template< class   
      T  
      >  
class IRunnableObjectImpl  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IRunnableObjectImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IRunnableObjectImpl::GetRunningClass](../Topic/IRunnableObjectImpl::GetRunningClass.md)|Devuelve el CLSID del control actual.  La implementación de ATL establece CLSID en `GUID_NULL` y devuelve **E\_UNEXPECTED**.|  
|[IRunnableObjectImpl::IsRunning](../Topic/IRunnableObjectImpl::IsRunning.md)|determina si el control está ejecutando.  la implementación de ATL devuelve **TRUE**.|  
|[IRunnableObjectImpl::LockRunning](../Topic/IRunnableObjectImpl::LockRunning.md)|Bloquea el control en el estado en ejecución.  la implementación de ATL devuelve `S_OK`.|  
|[IRunnableObjectImpl::Run](../Topic/IRunnableObjectImpl::Run.md)|Fuerza el control para ejecutarse.  la implementación de ATL devuelve `S_OK`.|  
|[IRunnableObjectImpl::SetContainedObject](../Topic/IRunnableObjectImpl::SetContainedObject.md)|Indica que el control se inserta.  la implementación de ATL devuelve `S_OK`.|  
  
## Comentarios  
 La interfaz de [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) permite a un contenedor para determinar si un control se ejecuta, lo convierte en ejecutarse, o se bloquea en el estado en ejecución.  La clase `IRunnableObjectImpl` proporciona una implementación predeterminada de esta interfaz y implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)