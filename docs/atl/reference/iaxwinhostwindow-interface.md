---
title: "IAxWinHostWindow Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IAxWinHostWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinHostWindow interface"
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
caps.latest.revision: 21
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAxWinHostWindow Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta interfaz proporciona métodos para manipular un control y su objeto de host.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
interface IAxWinHostWindow : IUnknown  
  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[AttachControl](../Topic/IAxWinHostWindow::AttachControl.md)|Asocia un control existente al objeto host.|  
|[CreateControl](../Topic/IAxWinHostWindow::CreateControl.md)|Crea un control y lo asocia al objeto host.|  
|[CreateControlEx](../Topic/IAxWinHostWindow::CreateControlEx.md)|Crear un control, lo asocia al objeto host, y coloca opcionalmente un controlador de eventos.|  
|[QueryControl](../Topic/IAxWinHostWindow::QueryControl.md)|Devuelve un puntero de interfaz al control hospedado.|  
|[SetExternalDispatch](../Topic/IAxWinHostWindow::SetExternalDispatch.md)|establece la interfaz externa de `IDispatch` .|  
|[SetExternalUIHandler](../Topic/IAxWinHostWindow::SetExternalUIHandler.md)|establece la interfaz externa de `IDocHostUIHandlerDispatch` .|  
  
## Comentarios  
 Esta interfaz es expuesta por el control ActiveX ATL que hospeda objetos.  Llame a los métodos de esta interfaz para crear y\/o para asociar un control al objeto host, para obtener una interfaz de un control hospedado, o establecer el dispinterface o el controlador externo de la interfaz de usuario para el uso al hospedar el explorador web.  
  
## Requisitos  
 La definición de esta interfaz está disponible como IDL o C\+\+, como se muestra a continuación.  
  
|Tipo de definición|Archivo|  
|------------------------|-------------|  
|IDL|ATLIFace.idl|  
|C\+\+|ATLIFace.h \(también incluido en ATLBase.h\)|  
  
## Vea también  
 [IAxWinAmbientDispatch Interface](../../atl/reference/iaxwinambientdispatch-interface.md)   
 [CAxWindow::QueryHost](../Topic/CAxWindow::QueryHost.md)   
 [AtlAxGetHost](../Topic/AtlAxGetHost.md)