---
title: "CAtlServiceModuleT::Handler Function | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule::Handler"
  - "CServiceModule.Handler"
  - "Handler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Handler method"
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# CAtlServiceModuleT::Handler Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CAtlServiceModuleT::Handler` es la rutina que el administrador de control de servicios \(SCM\) llama para recuperar el estado del servicio y proporcionar le a instrucciones diferentes \(como detener o pausar\).  SCM pasa un código de operación a `Handler` para indicar lo que debe hacer el servicio.  Un servicio ATL\-generado predeterminado controla sólo la instrucción de detenerse.  Si SCM pasa la instrucción para detener, el servicio indica a SCM que el programa esté a punto detener.  El servicio llama `PostThreadMessage` para enviar un mensaje quit a sí mismo.  Esto finalizará el bucle de mensajes y el servicio se cerrará en última instancia.  
  
 Para controlar más instrucciones, debe cambiar el miembro de datos de `m_status` inicializado en el constructor de `CAtlServiceModuleT` .  Este miembro de datos indica a SCM los botones para habilitar cuando el servicio está seleccionada en la aplicación del Panel de control de Servicios.  
  
## Vea también  
 [Servicios](../atl/atl-services.md)   
 [CAtlServiceModuleT::Handler](../Topic/CAtlServiceModuleT::Handler.md)