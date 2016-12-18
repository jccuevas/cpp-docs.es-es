---
title: "IPointerInactiveImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPointerInactiveImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inactive objects"
  - "IPointerInactive ATL implementation"
  - "IPointerInactiveImpl class"
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IPointerInactiveImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa **IUnknown** y los métodos de interfaz de [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template< class   
      T  
      >  
class IPointerInactiveImpl  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IPointerInactiveImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPointerInactiveImpl::GetActivationPolicy](../Topic/IPointerInactiveImpl::GetActivationPolicy.md)|Recupera la directiva actual de activación para el objeto.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IPointerInactiveImpl::OnInactiveMouseMove](../Topic/IPointerInactiveImpl::OnInactiveMouseMove.md)|Notifica al objeto que el puntero del mouse ha desplazado sobre él, que indica que el objeto puede desencadenar eventos del mouse.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IPointerInactiveImpl::OnInactiveSetCursor](../Topic/IPointerInactiveImpl::OnInactiveSetCursor.md)|Establece el puntero del mouse para el objeto inactivo.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
  
## Comentarios  
 Un objeto inactivo es uno que se carga simplemente o su ejecución.  A diferencia de un objeto activo, un objeto inactivo no puede recibir mensajes del teclado y de mouse de Windows.  Así, los objetos inactivos utilizan menos recursos y suelen ser más eficaces.  
  
 La interfaz de [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) permite que un objeto admite un nivel mínimo de interacción con el mouse mientras permanece inactivo.  Esta funcionalidad es especialmente útil para los controles.  
  
 La clase `IPointerInactiveImpl` implementa los métodos de `IPointerInactive` simplemente devuelve **E\_NOTIMPL**.  Sin embargo, implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)