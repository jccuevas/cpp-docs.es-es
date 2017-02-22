---
title: "Control de la aplicaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de la aplicación"
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Control de la aplicaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE requiere un control considerable sobre las aplicaciones y sus objetos.  Los archivos DLL del sistema OLE deben poder iniciar y liberar aplicaciones automáticamente, coordine la producción y modificación de objetos, etc.  Las funciones de este tema cumplen esos requisitos.  Además de ser llamado por los archivos DLL de OLE del sistema, estas funciones se deben llamar a veces por aplicaciones también.  
  
### Control de la aplicación  
  
|||  
|-|-|  
|[AfxOleCanExitApp](../Topic/AfxOleCanExitApp.md)|Indica si la aplicación puede finalizar.|  
|[AfxOleGetMessageFilter](../Topic/AfxOleGetMessageFilter.md)|Recupera el filtro de mensajes de aplicación actual.|  
|[AfxOleGetUserCtrl](../Topic/AfxOleGetUserCtrl.md)|Recupera el marcador actual de la usuario\- CONTROL.|  
|[AfxOleSetUserCtrl](../Topic/AfxOleSetUserCtrl.md)|Establece o desactive el indicador de la usuario\- CONTROL.|  
|[AfxOleLockApp](../Topic/AfxOleLockApp.md)|Aumenta el número global del marco del número de objetos activos en una aplicación.|  
|[AfxOleUnlockApp](../Topic/AfxOleUnlockApp.md)|Disminuye el recuento del marco del número de objetos activos en una aplicación.|  
|[AfxOleRegisterServerClass](../Topic/AfxOleRegisterServerClass.md)|Registra un servidor en el sistema OLE.|  
|[AfxOleSetEditMenu](../Topic/AfxOleSetEditMenu.md)|Implementa la interfaz de usuario para el comando de objeto *typename* .|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)