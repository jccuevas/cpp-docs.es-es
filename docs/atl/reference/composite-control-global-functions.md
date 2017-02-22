---
title: "Composite Control Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles compuestos, funciones globales"
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# Composite Control Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas funciones proporcionan compatibilidad para crear cuadros de diálogo, y crear, hospedar y autorizar controles ActiveX.  
  
> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[AtlAxDialogBox](../Topic/AtlAxDialogBox.md)|Crea un cuadro de diálogo modal de una plantilla de diálogo proporcionada por el usuario.  El cuadro de diálogo resultante puede contener controles ActiveX.|  
|[AtlAxCreateDialog](../Topic/AtlAxCreateDialog.md)|Crea un cuadro de diálogo no modal de una plantilla de diálogo proporcionada por el usuario.  El cuadro de diálogo resultante puede contener controles ActiveX.|  
|[AtlAxCreateControl](../Topic/AtlAxCreateControl.md)|Crea un control ActiveX, se inicializa, y los hospedarlo en la ventana especificada.|  
|[AtlAxCreateControlEx](../Topic/AtlAxCreateControlEx.md)|Crea un control ActiveX, se inicializa, lo hospeda en la ventana especificada, y recupera un puntero de interfaz \(o a punteros\) del control.|  
|[AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)|Crea un control ActiveX con licencia, se inicializa, y los hospedarlo en la ventana especificada.|  
|[AtlAxCreateControlLicEx](../Topic/AtlAxCreateControlLicEx.md)|Crea un control ActiveX con licencia, se inicializa, los hospedarlo en la ventana especificada, y recupera un puntero de interfaz \(o a punteros\) del control.|  
|[AtlAxAttachControl](../Topic/AtlAxAttachControl.md)|Asocia un control creado previamente a la ventana especificada.|  
|[AtlAxGetHost](../Topic/AtlAxGetHost.md)|Se utiliza para obtener un puntero directo de interfaz al contenedor de una ventana especificada \(si existe\), con el identificador.|  
|[AtlAxGetControl](../Topic/AtlAxGetControl.md)|Se utiliza para obtener un puntero directo de la interfaz en el interior contenido control una ventana especificada \(si existe\), según su identificador.|  
|[AtlSetChildSite](../Topic/AtlSetChildSite.md)|Inicializa **IUnknown** de sitio secundario.|  
|[AtlAxWinInit](../Topic/AtlAxWinInit.md)|Inicializa el hospedaje codificado para los objetos de AxWin.|  
|[AtlAxWinTerm](../Topic/AtlAxWinTerm.md)|Desinicializa el hospedaje codificado para los objetos de AxWin.|  
|[AtlGetObjectSourceInterface](../Topic/AtlGetObjectSourceInterface.md)|Información de retornos sobre la interfaz predeterminada del origen de un objeto.|  
  
## Vea también  
 [Funciones](../../atl/reference/atl-functions.md)   
 [Composite Control Macros](../../atl/reference/composite-control-macros.md)