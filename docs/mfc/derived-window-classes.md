---
title: "Clases de ventana derivadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++], derivadas"
  - "CWnd (clase), clases derivadas de"
  - "clases derivadas, clases de ventana"
  - "jerarquías, clases de ventana"
  - "jerarquía de clase de ventana"
  - "clases de ventana, derivadas"
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Clases de ventana derivadas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede crear ventanas directamente desde [CWnd](../mfc/reference/cwnd-class.md) o derivar las nuevas clases de ventana de `CWnd`.  De esta forma crearía normalmente sus propias ventanas personalizadas.  Sin embargo, para crear la mayoría de las ventanas de un programa marco se utilizan en su lugar las clases de ventana marco derivadas de `CWnd`, proporcionadas por MFC.  
  
## Clases de ventana marco  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 Se utiliza para las ventanas marco SDI que enmarcan un documento único y su vista.  La ventana marco es a la vez la ventana marco principal de la aplicación y la ventana marco del documento actual.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 Se utiliza como ventana marco principal para las aplicaciones MDI.  La ventana marco principal es un contenedor para todas las ventanas de documento MDI y comparte la barra de menús con ellas.  Una ventana marco MDI es una ventana de nivel superior que aparece en el escritorio.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 Se utiliza para los documentos individuales abiertos en una ventana marco principal MDI.  Una ventana marco secundaria MDI contenida en la ventana marco principal MDI enmarca cada uno de los documentos y sus vistas.  Una ventana secundaria MDI tiene una apariencia muy similar a la de una ventana marco típica, pero se incluye dentro de una ventana marco MDI en lugar de ubicarse en el escritorio.  Sin embargo, la ventana secundaria MDI no tiene su propia barra de menús y debe compartir la de la ventana marco MDI que la contiene.  
  
 Para obtener más información, vea [Ventanas marco](../mfc/frame-windows.md).  
  
## Otras clases de ventana derivadas de CWnd  
 Además de las ventanas marco, se derivan de `CWnd` otras categorías principales de ventanas:  
  
 *Vistas*  
 Las vistas se crean mediante la clase [CView](../mfc/reference/cview-class.md) derivada de `CWnd` \(o una de sus clases derivadas\).  Una vista se adjunta a un documento y actúa como intermediario entre el documento y el usuario.  Una vista es una ventana secundaria \(no un elemento secundario MDI\) que rellena normalmente el área cliente de una ventana marco SDI o de una ventana marco secundaria MDI \(o la parte del área cliente no cubierta por una barra de herramientas o una barra de estado\).  
  
 *Cuadros de diálogo*  
 Los cuadros de diálogo se crean mediante la clase [CDialog](../mfc/reference/cdialog-class.md) derivada de `CWnd`.  
  
 *Formularios*  
 Las vistas de formulario basadas en recursos de plantilla de cuadro de diálogo se crean mediante las clases [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md) o [CDaoRecordView](../mfc/reference/cdaorecordview-class.md).  
  
 *Controles*  
 Los controles como botones, cuadros de lista y cuadros combinados se crean con otras clases derivadas de `CWnd`.  Vea [Temas acerca de controles](../mfc/controls-mfc.md).  
  
 *Barras de controles*  
 Ventanas secundarias que contienen controles.  Entre los ejemplos se incluyen las barras de herramientas y las barras de estado.  Vea [Barras de controles](../mfc/control-bars.md).  
  
## Jerarquía de clases de ventana  
 Consulte el [gráfico de jerarquía de MFC](../mfc/hierarchy-chart.md) en la *Referencia de MFC*.  Las vistas se explican en [Arquitectura documento\/vista](../mfc/document-view-architecture.md).  Los cuadros de diálogo se explican en [Cuadros de diálogo](../mfc/dialog-boxes.md).  
  
## Crear sus propios tipos de ventana para un propósito especial  
 Además de las clases de ventana proporcionadas por la biblioteca de clases, puede necesitar ventanas secundarias con un propósito especial.  Para configurar este tipo de ventanas, cree su propia clase derivada de [CWnd](../mfc/reference/cwnd-class.md) y conviértala en una ventana secundaria de un marco o vista.  Tenga en cuenta que el marco administra la extensión del área cliente de una ventana marco de documento.  La mayor parte del área cliente se administra mediante una vista, pero otras ventanas, por ejemplo, las barras de control o sus propias ventanas personalizadas, pueden compartir el espacio con la vista.  Puede ser necesario interactuar con los mecanismos de las clases [CView](../mfc/reference/cview-class.md) y [CControlBar](../mfc/reference/ccontrolbar-class.md) para colocar las ventanas secundarias en el área cliente de una ventana marco.  
  
 En [Crear ventanas](../mfc/creating-windows.md) se describe la creación de objetos de ventana y cómo estos administran las ventanas.  
  
## Vea también  
 [Window \(Objetos\)](../mfc/window-objects.md)