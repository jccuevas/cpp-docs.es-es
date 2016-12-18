---
title: "Adding Functionality to the Composite Control | Microsoft Docs"
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
  - "controles ActiveX [C++], eventos"
  - "controles compuestos, controlar eventos"
  - "event handlers [C++], controles ActiveX"
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Functionality to the Composite Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una vez que ha insertado cualquier control necesario en el control compuesto, el paso siguiente consiste en agregar de nueva funcionalidad.  Esta nueva funcionalidad entra normalmente en dos categorías:  
  
-   Compatibilidad de interfaces adicionales y personalizar el comportamiento del control compuesto con características adicionales, concretas.  
  
-   Controlar eventos de controles ActiveX contenido \(o controles\).  
  
 Para el propósito y el ámbito de este artículo, el resto de esta sección se centra únicamente en administrar eventos de controles ActiveX.  
  
> [!NOTE]
>  Si necesita controlar mensajes de controles de Windows, vea [implementar una ventana](../atl/implementing-a-window.md) para obtener más información sobre el control de mensajes en ATL.  
  
 Después de insertar un control ActiveX en el control y haga clic **Agregar controlador de eventos**de diálogo el recurso, haga clic con el botón secundario.  Seleccione el evento que desea administrar y haga clic en **Agregar y editar**.  El código de controlador de eventos se agregará al archivo de .h del control.  
  
 Los puntos de conexión para los controles ActiveX del control compuesto automáticamente están conectados y desconectados mediante llamadas a [CComCompositeControl:: AdviseSinkMap](../Topic/CComCompositeControl::AdviseSinkMap.md).  
  
## Vea también  
 [Fundamentos de controles compuestos](../atl/atl-composite-control-fundamentals.md)