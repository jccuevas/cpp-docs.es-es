---
title: "Barras de cuadro de di&#225;logo | Microsoft Docs"
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
  - "CDialogBar (clase), barras de cuadro de diálogo"
  - "barras de control, barras de cuadro de diálogo"
  - "barras de cuadro de diálogo"
  - "barras de cuadro de diálogo, acerca de las barras de cuadro de diálogo"
  - "MFC, barras de control"
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Barras de cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una barra de cuadro diálogo es una barra de herramientas, una clase de [barra de control](../mfc/control-bars.md) que puede contener cualquier tipo de control.  Porque tiene las características de un cuadro de diálogo no modal, un objeto de [CDialogBar](../mfc/reference/cdialogbar-class.md) proporciona una barra de herramientas más eficaz.  
  
 Hay varias diferencias clave entre una barra de herramientas y un objeto de `CDialogBar` .  Un objeto de `CDialogBar` se crea de un recurso de la diálogo\- plantilla, que puede crear con el editor de cuadros de diálogo de Visual C\+\+ y que puede contener cualquier tipo de control de Windows.  El usuario puede pestaña de control al control.  Y puede especificar un estilo de alineación para alinear la barra de cuadro diálogo con cualquier parte de la ventana de marco principal o incluso para dejarlo en contexto si cambian el tamaño al elemento primario.  La ilustración siguiente se muestra una barra de cuadro diálogo con diversos controles.  
  
 ![Barra de cuadro de diálogo de VC](../mfc/media/vc378t1.png "vc378T1")  
Una barra de cuadro de diálogo  
  
 En otros aspectos, trabajar con un objeto de `CDialogBar` es como trabajar con un cuadro de diálogo no modal.  Utilice el editor de cuadros de diálogo para diseñar y crear el recurso de cuadro de diálogo.  
  
 Una de las virtudes de barras de cuadro de diálogo es que pueden incluir controles distintos de los botones.  
  
 Aunque es normal derivar dispone de clases de diálogo de `CDialog`, no deriva normalmente dispone de la clase para una barra de cuadro de diálogo.  Las barras de cuadro de diálogo son extensiones a una ventana principal y cualquier mensaje de la CONTROL\- notificación de la barra de cuadro de diálogo, como **BN\_CLICKED** o **EN\_CHANGE**, se enviará al elemento primario de la barra de cuadro de diálogo, la ventana principal.  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [Ejemplo](../top/visual-cpp-samples.md)