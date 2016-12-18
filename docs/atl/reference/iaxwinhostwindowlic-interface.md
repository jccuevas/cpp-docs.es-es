---
title: "IAxWinHostWindowLic Interface | Microsoft Docs"
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
  - "IAxWinHostWindowLic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinHostWindowLic interface"
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAxWinHostWindowLic Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta interfaz proporciona métodos para manipular un control con licencia y su objeto de host.  
  
## Sintaxis  
  
```  
  
interface IAxWinHostWindowLic : IAxWinHostWindow  
  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[CreateControlLic](../Topic/IAxWinHostWindowLic::CreateControlLic.md)|Crea un control con licencia y lo asocia al objeto host.|  
|[CreateControlLicEx](../Topic/IAxWinHostWindowLic::CreateControlLicEx.md)|Crea un control con licencia, lo asocia al objeto host, y coloca opcionalmente un controlador de eventos.|  
  
## Comentarios  
 `IAxWinHostWindowLic` hereda de [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) y agregar métodos que admiten la creación de controles con licencia.  
  
 Vea [Hospedar Controles ActiveX mediante ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que utiliza miembros de esta interfaz.  
  
## Requisitos  
 La definición de esta interfaz está disponible como IDL o C\+\+, como se muestra a continuación.  
  
|Tipo de definición|Archivo|  
|------------------------|-------------|  
|IDL|ATLIFace.idl|  
|C\+\+|ATLIFace.h \(también incluido en ATLBase.h\)|