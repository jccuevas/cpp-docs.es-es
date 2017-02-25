---
title: "Windows Support Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.windows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, ventanas"
  - "windows [C++], ATL"
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Windows Support Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases siguientes proporcionan compatibilidad para las ventanas:  
  
-   [\_U\_MENUorID](../atl/reference/u-menuorid-class.md) Proporciona contenedores para **CreateWindow** y **CreateWindowEx**.  
  
-   Métodos de[CWindow](../atl/reference/cwindow-class.md) Contains para manipular una ventana.  `CWindow` es la clase base para `CWindowImpl`, `CDialogImpl` y `CContainedWindow`.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) implementa una ventana basada en una nueva clase de ventana.  También permite crear subclases o que utiliza la ventana.  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) implementa un cuadro de diálogo.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) implementa un cuadro de diálogo \(modal o no modal\) que los controles ActiveX de hospeda.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) implementa un cuadro de diálogo \(modal o no modal\) con funcionalidad básica.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) Manipulates una ventana que hospeda un control ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) proporciona los métodos para manipular una ventana que hospeda un control ActiveX y también tiene compatibilidad para hospedar controles ActiveX con licencia.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) implementa una ventana contenida dentro de otro objeto.  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) administra la información de una nueva clase de ventana.  
  
-   Encadenamiento dinámico de la de[CDynamicChain](../atl/reference/cdynamicchain-class.md) de los mapas de mensajes.  
  
-   [CMessageMap](../atl/reference/cmessagemap-class.md) Permitir un objeto exponer el mensaje asigna a otros objetos.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) proporciona un método simple de normalizar los rasgos de un objeto en la ventana de ATL.  
  
-   [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) proporciona valores predeterminados para los estilos de ventana y estilos extendidos utilizados para crear una ventana.  Estos valores se agregan, mediante el operador lógico OR, los valores proporcionados durante la creación de una ventana.  
  
## artículos relacionados  
 [Clases de ventana ATL](../atl/atl-window-classes.md)  
  
 [tutorial de ATL](../atl/active-template-library-atl-tutorial.md)  
  
## Vea también  
 [Class Overview](../atl/atl-class-overview.md)   
 [Message Map Macros](../atl/reference/message-map-macros-atl.md)   
 [Window Class Macros](../atl/reference/window-class-macros.md)