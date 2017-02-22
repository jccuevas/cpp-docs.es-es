---
title: "IAxWinAmbientDispatch Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IAxWinAmbientDispatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinAmbientDispatch interface"
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# IAxWinAmbientDispatch Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta interfaz proporciona métodos para especificar características de control o contenedor hospedado.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
interface IAxWinAmbientDispatch : IDispatch  
  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[get\_AllowContextMenu](../Topic/IAxWinAmbientDispatch::get_AllowContextMenu.md)|La propiedad de **AllowContextMenu** especifica si el control hospedado se permite mostrar su propio menú contextual.|  
|[get\_AllowShowUI](../Topic/IAxWinAmbientDispatch::get_AllowShowUI.md)|La propiedad de **AllowShowUI** especifica si el control hospedado se permite mostrar su propia interfaz de usuario.|  
|[get\_AllowWindowlessActivation](../Topic/IAxWinAmbientDispatch::get_AllowWindowlessActivation.md)|la propiedad de **AllowWindowlessActivation** especifica si el contenedor permitirá la activación sin ventana.|  
|[get\_BackColor](../Topic/IAxWinAmbientDispatch::get_BackColor.md)|La propiedad de `BackColor` especifica el color de fondo ambiente del contenedor.|  
|[get\_DisplayAsDefault](../Topic/IAxWinAmbientDispatch::get_DisplayAsDefault.md)|**DisplayAsDefault** es una propiedad de ambiente que permite que un control averigüe si el control predeterminado.|  
|[get\_DocHostDoubleClickFlags](../Topic/IAxWinAmbientDispatch::get_DocHostDoubleClickFlags.md)|La propiedad de **DocHostDoubleClickFlags** especifica la operación que debe aplicarse en respuesta a un doble clic.|  
|[get\_DocHostFlags](../Topic/IAxWinAmbientDispatch::get_DocHostFlags.md)|La propiedad de **DocHostFlags** especifica las funciones de la interfaz de usuario del objeto host.|  
|[get\_Font](../Topic/IAxWinAmbientDispatch::get_Font.md)|La propiedad de **Fuente** especifica la fuente ambiente del contenedor.|  
|[get\_ForeColor](../Topic/IAxWinAmbientDispatch::get_ForeColor.md)|La propiedad de `ForeColor` especifica el color de primer plano ambiente del contenedor.|  
|[get\_LocaleID](../Topic/IAxWinAmbientDispatch::get_LocaleID.md)|La propiedad de **LocaleID** especifica el identificador de configuración regional de ambiente del contenedor.|  
|[get\_MessageReflect](../Topic/IAxWinAmbientDispatch::get_MessageReflect.md)|La propiedad de ambiente de **MessageReflect** especifica si el contenedor reflejará mensajes al control hospedado.|  
|[get\_OptionKeyPath](../Topic/IAxWinAmbientDispatch::get_OptionKeyPath.md)|La propiedad de **OptionKeyPath** especifica la ruta de la clave del Registro a la configuración de usuario.|  
|[get\_ShowGrabHandles](../Topic/IAxWinAmbientDispatch::get_ShowGrabHandles.md)|La propiedad de ambiente de **ShowGrabHandles** permite que el control averigüe si se dibuja con los controladores de arrastre.|  
|[el get\_ShowHatching](../Topic/IAxWinAmbientDispatch::get_ShowHatching.md)|La propiedad de ambiente de **ShowHatching** permite que el control averigüe si se dibuja tramó.|  
|[get\_UserMode](../Topic/IAxWinAmbientDispatch::get_UserMode.md)|La propiedad de **UserMode** especifica el modo usuario ambiente del contenedor.|  
|[put\_AllowContextMenu](../Topic/IAxWinAmbientDispatch::put_AllowContextMenu.md)|La propiedad de **AllowContextMenu** especifica si el control hospedado se permite mostrar su propio menú contextual.|  
|[put\_AllowShowUI](../Topic/IAxWinAmbientDispatch::put_AllowShowUI.md)|La propiedad de **AllowShowUI** especifica si el control hospedado se permite mostrar su propia interfaz de usuario.|  
|[put\_AllowWindowlessActivation](../Topic/IAxWinAmbientDispatch::put_AllowWindowlessActivation.md)|la propiedad de **AllowWindowlessActivation** especifica si el contenedor permitirá la activación sin ventana.|  
|[put\_BackColor](../Topic/IAxWinAmbientDispatch::put_BackColor.md)|La propiedad de `BackColor` especifica el color de fondo ambiente del contenedor.|  
|[put\_DisplayAsDefault](../Topic/IAxWinAmbientDispatch::put_DisplayAsDefault.md)|**DisplayAsDefault** es una propiedad de ambiente que permite que un control averigüe si el control predeterminado.|  
|[put\_DocHostDoubleClickFlags](../Topic/IAxWinAmbientDispatch::put_DocHostDoubleClickFlags.md)|La propiedad de **DocHostDoubleClickFlags** especifica la operación que debe aplicarse en respuesta a un doble clic.|  
|[put\_DocHostFlags](../Topic/IAxWinAmbientDispatch::put_DocHostFlags.md)|La propiedad de **DocHostFlags** especifica las funciones de la interfaz de usuario del objeto host.|  
|[put\_Font](../Topic/IAxWinAmbientDispatch::put_Font.md)|La propiedad de **Fuente** especifica la fuente ambiente del contenedor.|  
|[put\_ForeColor](../Topic/IAxWinAmbientDispatch::put_ForeColor.md)|La propiedad de `ForeColor` especifica el color de primer plano ambiente del contenedor.|  
|[put\_LocaleID](../Topic/IAxWinAmbientDispatch::put_LocaleID.md)|La propiedad de **LocaleID** especifica el identificador de configuración regional de ambiente del contenedor.|  
|[put\_MessageReflect](../Topic/IAxWinAmbientDispatch::put_MessageReflect.md)|La propiedad de ambiente de **MessageReflect** especifica si el contenedor reflejará mensajes al control hospedado.|  
|[put\_OptionKeyPath](../Topic/IAxWinAmbientDispatch::put_OptionKeyPath.md)|La propiedad de **OptionKeyPath** especifica la ruta de la clave del Registro a la configuración de usuario.|  
|[put\_UserMode](../Topic/IAxWinAmbientDispatch::put_UserMode.md)|La propiedad de **UserMode** especifica el modo usuario ambiente del contenedor.|  
  
## Comentarios  
 Esta interfaz es expuesta por el control ActiveX ATL que hospeda objetos.  Llame a los métodos de esta interfaz para establecer propiedades de ambiente disponibles para el control hospedado o para especificar otros aspectos del comportamiento del contenedor.  Para complementar las propiedades proporcionado por `IAxWinAmbientDispatch`, utiliza [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).  
  
 [AXHost](https://msdn.microsoft.com/en-us/library/system.windows.forms.axhost.aspx) intentará cargar la información de tipo sobre `IAxWinAmbientDispatch` y `IAxWinAmbientDispatchEx` typelib que contiene el código.  
  
 Si está vinculando a ATL90.dll, **AXHost** cargará la información de tipo typelib de DLL.  
  
 Vea [Hospedar Controles ActiveX mediante ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) para más detalles.  
  
## Requisitos  
 La definición de esta interfaz está disponible con varios formatos, como se muestra en la siguiente tabla.  
  
|Tipo de definición|Archivo|  
|------------------------|-------------|  
|IDL|atliface.idl|  
|Biblioteca de tipos|ATL.dll|  
|C\+\+|atliface.h \(también incluido en ATLBase.h\)|  
  
## Vea también  
 [IAxWinAmbientDispatchEx Interface](../../atl/reference/iaxwinambientdispatchex-interface.md)   
 [IAxWinHostWindow Interface](../../atl/reference/iaxwinhostwindow-interface.md)   
 [CAxWindow::QueryHost](../Topic/CAxWindow::QueryHost.md)   
 [AtlAxGetHost](../Topic/AtlAxGetHost.md)