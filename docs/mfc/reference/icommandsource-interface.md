---
title: "ICommandSource Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ICommandSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandSource interface"
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# ICommandSource Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Administra los comandos enviados de un objeto de origen de comando a un control de usuario.  
  
## Sintaxis  
  
```  
interface class ICommandSource  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ICommandSource::AddCommandHandler](../Topic/ICommandSource::AddCommandHandler.md)|Agrega un controlador de comandos a un objeto de origen de comando.|  
|[ICommandSource::AddCommandRangeHandler](../Topic/ICommandSource::AddCommandRangeHandler.md)|Agrega un grupo de controladores de comandos a un objeto de origen de comando.|  
|[ICommandSource::AddCommandRangeUIHandler](../Topic/ICommandSource::AddCommandRangeUIHandler.md)|Agrega un grupo de controladores de mensajes de comando de la interfaz de usuario a un objeto de origen de comando.|  
|[ICommandSource::AddCommandUIHandler](../Topic/ICommandSource::AddCommandUIHandler.md)|Agrega un controlador de mensajes de comando de la interfaz de usuario a un objeto de origen de comando.|  
|[ICommandSource::PostCommand](../Topic/ICommandSource::PostCommand.md)|Elementos para exponer un mensaje sin esperar a que se procese.|  
|[ICommandSource::RemoveCommandHandler](../Topic/ICommandSource::RemoveCommandHandler.md)|Quita un controlador de comandos de un objeto de origen de comando.|  
|[ICommandSource::RemoveCommandRangeHandler](../Topic/ICommandSource::RemoveCommandRangeHandler.md)|Quita un grupo de controladores de comandos de un objeto de origen de comando.|  
|[ICommandSource::RemoveCommandRangeUIHandler](../Topic/ICommandSource::RemoveCommandRangeUIHandler.md)|Quita un grupo de controladores de mensajes de comando de la interfaz de usuario de un objeto de origen de comando.|  
|[ICommandSource::RemoveCommandUIHandler](../Topic/ICommandSource::RemoveCommandUIHandler.md)|Quita un controlador de mensajes de comando de la interfaz de usuario de un objeto de origen de comando.|  
|[ICommandSource::SendCommand](../Topic/ICommandSource::SendCommand.md)|Envía un mensaje y espera que se procese antes de volver.|  
  
## Comentarios  
 Al hospedar un control de usuario en una vista MFC, [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md) enruta comandos y los mensajes de la interfaz de usuario de comandos de actualización al control de usuario para que pueda controlar los comandos MFC \(por ejemplo, elementos de menú de cuadro y botones de la barra de herramientas\).  Implementar [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md), se proporciona al control de usuario una referencia al objeto de `ICommandSource` .  
  
 Vea [Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo utilizar `ICommandTarget`.  
  
 Para obtener más información sobre cómo utilizar los formularios Windows Forms, vea [Utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## Requisitos  
 **encabezado:** afxwinforms.h \(definido en el atlmfc \\ biblioteca \\ mfcmifc80.dll de ensamblado\)  
  
## Vea también  
 [Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md)