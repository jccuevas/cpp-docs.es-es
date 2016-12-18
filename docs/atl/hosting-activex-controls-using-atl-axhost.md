---
title: "Hosting ActiveX Controls Using ATL AXHost | Microsoft Docs"
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
  - "controles ActiveX [C++], hosting"
  - "AXHost method"
  - "Calendar control (ActiveX)"
  - "Calendar control (ActiveX), hosting with ATL AXHost"
  - "CAxWindow2T class"
  - "hospedar controles ActiveX"
ms.assetid: 2c1200ec-effb-4814-820a-509519699468
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Hosting ActiveX Controls Using ATL AXHost
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El ejemplo de este tema se muestra cómo crear AXHost y cómo hospedar un control ActiveX mediante diferente ATL funciona.  También muestra cómo tener acceso a los eventos del control y el receptor \(mediante [IDispEventImpl](../atl/reference/idispeventimpl-class.md)\) del control se hospeda que.  El ejemplo hospeda el control Calendar en una ventana principal o en una ventana secundaria.  
  
 Observe la definición del símbolo de `USE_METHOD` .  Puede cambiar el valor de este símbolo para variar entre 1 y 8.  El valor del símbolo determina cómo el control se creará:  
  
-   Por valores pares de `USE_METHOD`, la llamada para crear el host crea una subclase de una ventana y la convierte en un host del control.  Por valores con números impares, el código crea una ventana secundaria que actúa como host.  
  
-   Para los valores de `USE_METHOD` entre 1 y 4, el acceso al control y la recepción de eventos se realizan en la llamada que también crea el host.  Los valores entre 5 y 8 vea el host para las interfaces y enlace el receptor.  
  
 A continuación se ofrece un resumen:  
  
|USE\_METHOD|Host|Acceso de Control y contraer de eventos|Función demostrada|  
|-----------------|----------|---------------------------------------------|------------------------|  
|1|Ventana secundaria|Un paso|CreateControlLicEx|  
|2|Ventana principal|Un paso|AtlAxCreateControlLicEx|  
|3|Ventana secundaria|Un paso|CreateControlEx|  
|4|Ventana principal|Un paso|AtlAxCreateControlEx|  
|5|Ventana secundaria|Varios pasos|CreateControlLic|  
|6|Ventana principal|Varios pasos|AtlAxCreateControlLic|  
|7|Ventana secundaria|Varios pasos|CreateControl|  
|8|Ventana principal|Varios pasos|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/CPP/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## Vea también  
 [Preguntas más frecuentes sobre contención de controles](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](../Topic/AtlAxCreateControl.md)   
 [AtlAxCreateControlEx](../Topic/AtlAxCreateControlEx.md)   
 [AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)   
 [AtlAxCreateControlLicEx](../Topic/AtlAxCreateControlLicEx.md)   
 [CAxWindow2T Class](../atl/reference/caxwindow2t-class.md)   
 [IAxWinHostWindowLic Interface](../atl/reference/iaxwinhostwindowlic-interface.md)