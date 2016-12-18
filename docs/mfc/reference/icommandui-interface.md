---
title: "ICommandUI Interface | Microsoft Docs"
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
  - "ICommandUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandUI interface"
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
caps.latest.revision: 24
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandUI Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Administra comandos de la interfaz de usuario.  
  
## Sintaxis  
  
```  
interface class ICommandUI  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ICommandUI::Check](../Topic/ICommandUI::Check.md)|Establece el elemento de la interfaz de usuario para este comando el estado adecuada de comprobación.|  
|[ICommandUI::ContinueRouting](../Topic/ICommandUI::ContinueRouting.md)|Indica al mecanismo de comando\- enrutamiento que continúe distribuyendo el mensaje actual bajar la cadena de controladores.|  
|[ICommandUI::Enabled](../Topic/ICommandUI::Enabled.md)|Habilita o deshabilita el elemento de la interfaz de usuario para este comando.|  
|[ICommandUI::ID](../Topic/ICommandUI::ID.md)|Obtiene el id. de objeto de la interfaz de usuario representado por el objeto de `ICommandUI` .|  
|[ICommandUI::Index](../Topic/ICommandUI::Index.md)|Obtiene el índice del objeto de interfaz de usuario representado por el objeto de `ICommandUI` .|  
|[ICommandUI::Radio](../Topic/ICommandUI::Radio.md)|Establece el elemento de la interfaz de usuario para este comando el estado adecuada de comprobación.|  
|[ICommandUI::Text](../Topic/ICommandUI::Text.md)|Establece el texto del elemento de la interfaz de usuario para este comando.|  
  
## Comentarios  
 Esta interfaz proporciona métodos y propiedades que administran comandos de la interfaz de usuario.  `ICommandUI` es similar a [CCmdUI Class](../../mfc/reference/ccmdui-class.md), salvo que `ICommandUI` se utiliza para las aplicaciones MFC que interactúan con componentes.NET.  
  
 `ICommandUI` se utiliza dentro de un controlador en [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)\- clase derivada de `ON_UPDATE_COMMAND_UI` .  Cuando un usuario de una aplicación activa \(activa o los clics\) un menú, cada elemento de menú se genera como habilitado o deshabilitado.  El destino de cada comando de menú proporciona esta información implementar un controlador de `ON_UPDATE_COMMAND_UI` .  Para cada uno de los objetos de la interfaz de usuario de comandos en la aplicación, use la ventana Propiedades para crear un prototipo de entrada y la función de mensaje\- mapa para cada controlador.  
  
 Para obtener más información sobre cómo la interfaz de `ICommandUI` se utiliza en el enrutamiento de comandos, vea [Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Para obtener más información sobre cómo utilizar los formularios Windows Forms, vea [Utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Para obtener más información sobre cómo administrar los comandos de la interfaz de usuario en MFC, vea [CCmdUI Class](../../mfc/reference/ccmdui-class.md).  
  
## Requisitos  
 **encabezado:** afxwinforms.h \(definido en el atlmfc \\ biblioteca \\ mfcmifc80.dll de ensamblado\)  
  
## Vea también  
 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)