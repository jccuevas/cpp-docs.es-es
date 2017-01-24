---
title: "Enlace de datos con controles ActiveX en Visual C++ | Microsoft Docs"
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
  - "controles ActiveX [C++], enlace de datos"
  - "controles enlazados [C++], ActiveX"
  - "controles [C++], enlace de datos"
  - "enlace de datos [C++], controles ActiveX"
  - "controles enlazados a datos [C++], ActiveX"
ms.assetid: afe11d2b-eefe-43ce-958d-82d3d4dee158
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Enlace de datos con controles ActiveX en Visual C++
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El enlace de datos se implementa a través de dos tipos de controles ActiveX: controles de datos y controles enlazados a datos.  
  
 **Controles de datos**  
 Los controles de datos tienen la misión de encapsular una consulta de base de datos y el conjunto de filas obtenido.  Los controles de datos de Microsoft proporcionan una interfaz compuesta por una serie de botones que permiten recorrer los datos.  Visual C\+\+ ofrece dos tecnologías de acceso a datos para los controles de datos: [ADO y RDO](../../data/ado-rdo/data-access-ado-and-rdo.md).  
  
> [!IMPORTANT]
>  Los controles de datos ADO y RDO son una tecnología antigua incluida en una versión anterior de Visual Studio; puede que no estén disponibles en la versión actual.  Para utilizar la información de esta sección, quizás tenga que obtener una versión anterior para adquirir el control adecuado.  
  
 **Controles enlazados a datos**  
 Un control enlazado a datos tiene la misión de presentar los datos.  Los controles enlazados a datos se conectan a controles de datos para recibir datos y presentarlos a través de varias interfaces de usuario.  Una aplicación de Visual C\+\+ también puede enlazar variables a valores de datos establecidos en los controles enlazados a datos; vea [CWnd::BindProperty](../Topic/CWnd::BindProperty.md).  
  
 Para obtener más información sobre el enlace de datos, vea:  
  
-   [Controles ActiveX de MFC: utilizar enlace de datos en un control ActiveX](../../mfc/mfc-activex-controls-using-data-binding-in-an-activex-control.md)  
  
-   [Acceso a datos: ADO y RDO](../../data/ado-rdo/data-access-ado-and-rdo.md)  
  
-   [Enlace de datos ADO](../../data/ado-rdo/ado-databinding.md)  
  
-   [Enlace de datos RDO](../../data/ado-rdo/rdo-databinding.md)  
  
-   [Clases contenedoras](../../data/ado-rdo/wrapper-classes.md)  
  
-   [Establecer controladores de eventos en controles ActiveX](../../data/ado-rdo/setting-event-handlers-on-activex-controls.md)  
  
-   [Interceptación de errores](../../data/ado-rdo/error-trapping.md)  
  
-   [Limitaciones del enlace de datos](../../data/ado-rdo/limitations-of-databinding.md)  
  
## Vea también  
 [Controles enlazados a datos \(ADO y RDO\)](../../data/ado-rdo/data-bound-controls-ado-and-rdo.md)