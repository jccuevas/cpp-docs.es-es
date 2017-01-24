---
title: "Which ATL Classes Facilitate ActiveX Control Containment? | Microsoft Docs"
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
  - "contenedores de controles ActiveX [C++], ATL control hosting"
  - "hosting controls using ATL"
ms.assetid: 803a4605-7f4c-4139-8638-49d8783d31b0
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Which ATL Classes Facilitate ActiveX Control Containment?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El código que hospeda ATL no requiere utilizar ninguna clase ATL; puede crear simplemente una ventana de **“AtlAxWin80”** y utilizar API que hospeda en caso necesario \(para obtener más información, vea [¿Cuál es el ATL API que Hospeda?](../atl/what-is-the-atl-control-hosting-api-q.md)\).  Sin embargo, las clases siguientes crean las características de contención más fáciles de utilizar.  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[CAxWindow](../atl/reference/caxwindow-class.md)|Incluye una ventana de **“AtlAxWin80”** , proporcionando métodos para crear la ventana, crear un control o adjuntar un control en la ventana, y recuperar punteros de interfaz en el objeto host.|  
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Incluye una ventana de **“AtlAxWinLic80”** , proporcionando métodos para crear la ventana, crear un control o adjuntar un control con licencia en la ventana, y recuperar punteros de interfaz en el objeto host.|  
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Actúa como clase base para las clases de control ActiveX basadas en un recurso de cuadro de diálogo.  Tales controles pueden contener otros controles ActiveX.|  
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Actúa como clase base para las clases de diálogo basadas en un recurso de cuadro de diálogo.  Tales diálogos pueden contener controles ActiveX.|  
|[CWindow](../atl/reference/cwindow-class.md)|Proporciona un método, [GetDlgControl](../Topic/CWindow::GetDlgControl.md), que devolverá un puntero de interfaz en un control, dado el identificador de la ventana host.  Además, los contenedores de la API de Windows expuestos por `CWindow` normalmente crean la administración de ventanas.|  
  
## Vea también  
 [Preguntas más frecuentes sobre contención de controles](../atl/atl-control-containment-faq.md)