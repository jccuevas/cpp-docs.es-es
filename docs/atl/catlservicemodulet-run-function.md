---
title: "CAtlServiceModuleT::Run Function | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule::Run"
  - "CServiceModule.Run"
  - "CSecurityDescriptor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "servicios ATL, seguridad"
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# CAtlServiceModuleT::Run Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Ejecutar** contiene las llamadas a `PreMessageLoop`, a `RunMessageLoop`, y a `PostMessageLoop`.  Después de llamar a, `PreMessageLoop` primero almacena el identificador de subproceso de servicio  El servicio utilizará este id. para cerrarse enviando un mensaje de **WM\_QUIT** mediante la función de la API Win32, [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946).  
  
 `PreMessageLoop` llama `InitializeSecurity`.  De forma predeterminada, `InitializeSecurity` llama [CoInitializeSecurity](http://msdn.microsoft.com/library/windows/desktop/ms693736) con el descriptor de seguridad establecido en NULL, lo que significa que cualquier usuario tiene acceso al objeto.  
  
 Si no desea que el servicio para especificar su propia seguridad, reemplazo `PreMessageLoop` y no llama a `InitializeSecurity`, y COM a determinará la configuración de seguridad del registro.  Una manera cómoda de configurar valores de registro se con la utilidad de [DCOMCNFG](../atl/dcomcnfg.md) analizada más adelante en esta sección.  
  
 Una vez que se especifica la seguridad, el objeto se registra con COM para que los nuevos clientes puedan conectar el programa.  Finalmente, el programa indica el administrador de control de servicios \(SCM\) que ejecute y el programa escribe un bucle de mensajes.  El programa permanece ejecutándose hasta que envíe un mensaje salido sobre el cierre del servicio.  
  
## Vea también  
 [Servicios](../atl/atl-services.md)   
 [CSecurityDesc Class](../atl/reference/csecuritydesc-class.md)   
 [CSid Class](../atl/reference/csid-class.md)   
 [CDacl Class](../atl/reference/cdacl-class.md)   
 [CAtlServiceModuleT::Run](../Topic/CAtlServiceModuleT::Run.md)