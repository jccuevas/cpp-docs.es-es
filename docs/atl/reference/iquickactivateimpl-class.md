---
title: "IQuickActivateImpl Class | Microsoft Docs"
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
  - "ATL::IQuickActivateImpl"
  - "ATL::IQuickActivateImpl<T>"
  - "ATL.IQuickActivateImpl"
  - "ATL.IQuickActivateImpl<T>"
  - "IQuickActivateImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activating ATL controls"
  - "controles [ATL], activar"
  - "IQuickActivate ATL implementation"
  - "IQuickActivateImpl class"
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IQuickActivateImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase combina la inicialización del control de contenedores en una única llamada.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template<   
class T   
>  
class ATL_NO_VTABLE IQuickActivateImpl :  
public IQuickActivate  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IQuickActivateImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](../Topic/IQuickActivateImpl::GetContentExtent.md)|Recupera el tamaño actual de presentación para un control actual.|  
|[IQuickActivateImpl::QuickActivate](../Topic/IQuickActivateImpl::QuickActivate.md)|Realiza la inicialización rápida de los controles que se cargan.|  
|[IQuickActivateImpl::SetContentExtent](../Topic/IQuickActivateImpl::SetContentExtent.md)|Informa al control cuánto espacio de pantalla le ha asignado el contenedor.|  
  
## Comentarios  
 Los contenedores de la interfaz de [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146) evitar retrasos a los controles de carga combinando la inicialización en una única llamada.  El método de `QuickActivate` permite que el contenedor pase un puntero a una estructura de [QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630) que contiene punteros a todas las interfaces que el control necesita.  Al volver, el control pasa la devuelve un puntero a una estructura de [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) que contiene punteros a sus propias interfaces, utilizadas por el contenedor.  La clase `IQuickActivateImpl` proporciona una implementación predeterminada de **IQuickActivate** e implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)