---
title: "COleMessageFilter Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleMessageFilter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones [OLE], managing interactions"
  - "COleMessageFilter class"
  - "message filters [C++]"
  - "mensajes [C++], OLE"
  - "OLE [C++], managing concurrency"
  - "aplicaciones OLE [C++], managing interactions"
  - "OLE messages"
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleMessageFilter Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

administra la simultaneidad requerida por la interacción de aplicaciones OLE.  
  
## Sintaxis  
  
```  
class COleMessageFilter : public CCmdTarget  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleMessageFilter::COleMessageFilter](../Topic/COleMessageFilter::COleMessageFilter.md)|Crea un objeto `COleMessageFilter`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleMessageFilter::BeginBusyState](../Topic/COleMessageFilter::BeginBusyState.md)|Coloca la aplicación en estado No disponible.|  
|[COleMessageFilter::EnableBusyDialog](../Topic/COleMessageFilter::EnableBusyDialog.md)|Habilita y deshabilita el cuadro de diálogo que aparece cuando una aplicación denominada No está disponible.|  
|[COleMessageFilter::EnableNotRespondingDialog](../Topic/COleMessageFilter::EnableNotRespondingDialog.md)|habilita y deshabilita el cuadro de diálogo que aparece cuando no está respondiendo una aplicación denominada.|  
|[COleMessageFilter::EndBusyState](../Topic/COleMessageFilter::EndBusyState.md)|Finaliza el estado No disponible de la aplicación.|  
|[COleMessageFilter::OnMessagePending](../Topic/COleMessageFilter::OnMessagePending.md)|Llamado por el marco para procesar los mensajes mientras una llamada OLE está en curso.|  
|[COleMessageFilter::Register](../Topic/COleMessageFilter::Register.md)|Registra el filtro de mensajes con los archivos DLL de OLE del sistema.|  
|[COleMessageFilter::Revoke](../Topic/COleMessageFilter::Revoke.md)|Revoca el registro de filtro de mensajes con los archivos DLL de OLE del sistema.|  
|[COleMessageFilter::SetBusyReply](../Topic/COleMessageFilter::SetBusyReply.md)|Determina la respuesta No disponible de la aplicación a una llamada OLE.|  
|[COleMessageFilter::SetMessagePendingDelay](../Topic/COleMessageFilter::SetMessagePendingDelay.md)|Determina cuánto tiempo la aplicación espera una respuesta a una llamada OLE.|  
|[COleMessageFilter::SetRetryReply](../Topic/COleMessageFilter::SetRetryReply.md)|Determina la respuesta de la aplicación de llamada a una aplicación No disponible.|  
  
## Comentarios  
 La clase de `COleMessageFilter` es útil en servidor visual y aplicaciones contenedoras de edición, así como aplicaciones de automatización OLE.  Para las aplicaciones de servidor se invocan que, esta clase se puede utilizar para crear la aplicación “No disponible” para cancelar o se reintenten llamadas entrantes de otras aplicaciones contenedoras más adelante.  Esta clase también se puede utilizar para determinar la acción que se realizarán en una aplicación de llamada cuando la aplicación denominada No está disponible.  
  
 El uso común es que una aplicación de servidor llame a [BeginBusyState](../Topic/COleMessageFilter::BeginBusyState.md) y [EndBusyState](../Topic/COleMessageFilter::EndBusyState.md) cuando se peligroso para que el documento u otro objeto accesible OLE se destruirá.  Estas llamadas se realizan en [CWinApp:: OnIdle](../Topic/CWinApp::OnIdle.md) durante las actualizaciones de la interfaz de usuario.  
  
 De forma predeterminada, se asigna un objeto de `COleMessageFilter` cuando se inicializa la aplicación.  Puede recuperar con [AfxOleGetMessageFilter](../Topic/AfxOleGetMessageFilter.md).  
  
 Esta es una clase avanzada; casi nunca se necesita trabajar con ella directamente.  
  
 Para obtener más información, vea el artículo [Servidores: Implementar en un Servidor](../../mfc/servers-implementing-a-server.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)