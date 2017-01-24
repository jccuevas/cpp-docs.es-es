---
title: "What Is the ATL Control-Hosting API? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "API [C++], hosting"
  - "control-hosting API"
  - "controles [ATL], API de hospedaje"
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
caps.latest.revision: 15
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# What Is the ATL Control-Hosting API?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL que hospeda API es el conjunto de funciones que permite que cualquier ventana actúa como un contenedor de controles ActiveX.  Estas funciones se pueden vincular estática o dinámicamente en el proyecto puesto que están disponibles como código fuente y expuesto por ATL90.dll.  Las funciones que hospedan se muestran en la tabla siguiente.  
  
|Función|Descripción|  
|-------------|-----------------|  
|[AtlAxAttachControl](../Topic/AtlAxAttachControl.md)|Crea un objeto host, lo conecta con la ventana proporciona, después asocia un control existente.|  
|[AtlAxCreateControl](../Topic/AtlAxCreateControl.md)|Crea un objeto host, lo conecta con la ventana proporciona, después cargar un control.|  
|[AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)|Crea un control ActiveX con licencia, se inicializa, y los hospedarlo en la ventana especificada, similar a [AtlAxCreateControl](../Topic/AtlAxCreateControl.md).|  
|[AtlAxCreateControlEx](../Topic/AtlAxCreateControlEx.md)|Crea un objeto host, lo conecta con la ventana proporciona, después cargar un control \(también permite que los receptores de eventos son configuración\).|  
|[AtlAxCreateControlLicEx](../Topic/AtlAxCreateControlLicEx.md)|Crea un control ActiveX con licencia, se inicializa, y los hospedarlo en la ventana especificada, similar a [AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md).|  
|[AtlAxCreateDialog](../Topic/AtlAxCreateDialog.md)|Crea un cuadro de diálogo no modal de un recurso de cuadro de diálogo y devuelve el identificador de ventana.|  
|[AtlAxDialogBox](../Topic/AtlAxDialogBox.md)|Crea un cuadro de diálogo modal de un recurso de cuadro de diálogo.|  
|[AtlAxGetControl](../Topic/AtlAxGetControl.md)|Devuelve el puntero de interfaz de **IUnknown** del control hospedado en una ventana.|  
|[AtlAxGetHost](../Topic/AtlAxGetHost.md)|Devuelve el puntero de interfaz de **IUnknown** de objetos host conectado a una ventana.|  
|[AtlAxWinInit](../Topic/AtlAxWinInit.md)|Inicializa el código el CONTROL\-hospedar.|  
|[AtlAxWinTerm](../Topic/AtlAxWinTerm.md)|desinicializa el código el CONTROL\-hospedar.|  
  
 Los parámetros de `HWND` en las tres primeras funciones deben ser una ventana existente \(casi\) de cualquier tipo.  Si llama a cualquiera de estas tres funciones explícitamente \(normalmente, no tiene que\), no pase un identificador de una ventana que está actuando ya como host \(si lo hace, el objeto host existente no se liberado\).  
  
 La primera llamada de siete funciones [AtlAxWinInit](../Topic/AtlAxWinInit.md) implícitamente.  
  
> [!NOTE]
>  API que hospeda forma la base de compatibilidad ATL para la contención de controles ActiveX.  Sin embargo, normalmente se poca necesidad de llamar a estas funciones directamente si aprovecha o crea de uso completo de las clases contenedoras ATL.  Para obtener más información, vea [¿Qué clases ATL facilitan la contención de controles ActiveX?](../atl/which-atl-classes-facilitate-activex-control-containment-q.md).  
  
## Vea también  
 [Preguntas más frecuentes sobre contención de controles](../atl/atl-control-containment-faq.md)