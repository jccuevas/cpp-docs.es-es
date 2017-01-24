---
title: "What Is a Host Object? | Microsoft Docs"
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
  - "host objects"
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# What Is a Host Object?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un objeto host es un objeto COM que representa el contenedor de controles ActiveX proporcionado por ATL para una ventana determinada.  El host que el objeto crea una subclase de la ventana contenedora para poder reflejar mensajes al control, proporciona las interfaces necesarias de contenedor que usará el control, y expone las interfaces de [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) y de [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) para permitir que configure el entorno de control.  
  
 Puede utilizar el objeto host para establecer las propiedades de ambiente del contenedor.  
  
## Vea también  
 [Preguntas más frecuentes sobre contención de controles](../atl/atl-control-containment-faq.md)