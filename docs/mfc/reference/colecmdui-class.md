---
title: "COleCmdUI Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleCmdUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX documents [C++], document server"
  - "COleCmdUI class"
  - "docobject server"
  - "document object server"
  - "servers [C++], ActiveX documents"
  - "servers [C++], doc objects"
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# COleCmdUI Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un método para que MFC actualizar el estado de los objetos relacionados con `IOleCommandTarget`\- características controladas de la interfaz de usuario de la aplicación.  
  
## Sintaxis  
  
```  
class COleCmdUI : public CCmdUI  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleCmdUI::COleCmdUI](../Topic/COleCmdUI::COleCmdUI.md)|Crea un objeto `COleCmdUI`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleCmdUI::Enable](../Topic/COleCmdUI::Enable.md)|Establece o desactive el marcador enabled del comando.|  
|[COleCmdUI::SetCheck](../Topic/COleCmdUI::SetCheck.md)|Establece el estado de un comando de alternancia con o.|  
|[COleCmdUI::SetText](../Topic/COleCmdUI::SetText.md)|Devuelve una cadena de nombre o de estado de texto para un comando.|  
  
## Comentarios  
 En una aplicación que no está habilitada para DocObjects, cuando el usuario ve un menú de la aplicación, MFC procesan los notifcations de **UPDATE\_COMMAND\_UI** .  Cada notificación se proporciona un objeto de [CCmdUI](../../mfc/reference/ccmdui-class.md) que se puede manipular para reflejar el estado de un comando concreto.  Sin embargo, cuando la aplicación está habilitada para DocObjects, MFC procesa las notificaciones de **UPDATE\_OLE\_COMMAND\_UI** y asigna los objetos de `COleCmdUI` .  
  
 `COleCmdUI` permite un DocObject reciba los comandos que se originan en la interfaz de usuario de su contenedor \(como FileNew, abra, imprimir, etc.\), y permite un contenedor que reciba los comandos que se originan en la interfaz de usuario de DocObject.  Aunque `IDispatch` se puede utilizar para enviar los mismos comandos, `IOleCommandTarget` proporciona una manera más sencilla de ver y ejecutar porque se basa en un conjunto estándar de comandos, normalmente sin argumentos, y ninguna información de tipo implicado.  `COleCmdUI` se puede utilizar para habilitar, actualizar, y establecer otras propiedades de los comandos de la interfaz de usuario de DocObject.  Cuando desea invocar el comando, llame a [COleServerDoc:: OnExecOleCmd](../Topic/COleServerDoc::OnExecOleCmd.md).  
  
 Para obtener más información sobre DocObjects, vea [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) y [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).  Vea también [Primeros pasos de internet: documentos activos](../../mfc/active-documents-on-the-internet.md) y [documentos activos](../../mfc/active-documents-on-the-internet.md).  
  
## Jerarquía de herencia  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## Requisitos  
 **encabezado:** afxdocobj.h  
  
## Vea también  
 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)