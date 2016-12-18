---
title: "Contenedores de controles ActiveX: Usar controles en un contenedor sin cuadro de di&#225;logo | Microsoft Docs"
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
  - "contenedores de controles ActiveX [C++], insertar controles"
  - "contenedores de controles ActiveX [C++], contenedores sin cuadro de diálogo"
  - "controles ActiveX [C++], crear"
  - "Create (método) [C++], controles ActiveX"
  - "CreateControl (método)"
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores de controles ActiveX: Usar controles en un contenedor sin cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En algunas aplicaciones, como una aplicación SDI o MDI, deseará insertar un control en una ventana de la aplicación.  La función miembro de **crear** de la clase contenedora, inline en Visual C\+\+, puede crear una instancia del control dinámicamente, sin necesidad de un cuadro de diálogo.  
  
 La función miembro de **crear** tiene los parámetros siguientes:  
  
 `lpszWindowName`  
 Un puntero al texto que se mostrará en el texto o la propiedad caption de control \(si existe\).  
  
 `dwStyle`  
 Estilos de Windows.  Para obtener una lista completa, vea [CWnd::CreateControl](../Topic/CWnd::CreateControl.md).  
  
 `rect`  
 Especifica el tamaño y la posición del control.  
  
 `pParentWnd`  
 Especifica la ventana principal del control, normalmente `CDialog`.  No debe ser **nulo**.  
  
 `nID`  
 Especifica el identificador del control y se puede utilizar por el contenedor para hacer referencia al control.  
  
 Un ejemplo de cómo utilizar esta función para crear dinámicamente un control ActiveX estaría en una vista de formulario de una aplicación SDI.  Puede crear una instancia del control en el controlador de `WM_CREATE` de la aplicación.  
  
 Para este ejemplo, `CMyView` es la clase principal de la vista, `CCirc` es la clase contenedora, y CIRC.H es el encabezado \(. H\) archivo de clase contenedora.  
  
 Implementar esta característica es un proceso de cuatro\- paso.  
  
### Para crear dinámicamente un control ActiveX en una ventana de no diálogo  
  
1.  Inserte CIRC.H en CMYVIEW.H, justo antes de la definición de clase de `CMyView` :  
  
     [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]  
  
2.  Agregue una variable miembro \(de `CCirc`escribe\) en la sección protected de la definición de clase de `CMyView` ubicada en CMYVIEW.H:  
  
     [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]  
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]  
  
3.  Agregue un controlador de mensajes de `WM_CREATE` a la clase `CMyView`.  
  
4.  En la función de controlador, `CMyView::OnCreate`, realiza una llamada a la función de `Create` de control mediante un puntero de **this** como ventana principal:  
  
     [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]  
  
5.  Recompile el proyecto.  Un control de Circ se creará dinámicamente cada vez que se crea la vista de la aplicación.  
  
## Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)