---
title: "Agregar controles a mano | Microsoft Docs"
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
  - "controles comunes [C++], agregar"
  - "controlar focos de entrada"
  - "controles [MFC], agregar a cuadros de diálogo"
  - "controles de cuadro de diálogo [C++], agregar a cuadros de diálogo"
  - "foco, controlar entradas"
  - "foco de control de entrada"
  - "controles comunes de Windows [C++], agregar"
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar controles a mano
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede [agregue controles a un cuadro de diálogo con el editor de cuadros de diálogo](../mfc/using-the-dialog-editor-to-add-controls.md) o agregarlos personalmente, con código.  
  
 Para crear un objeto el mismo control, se insertará normalmente el objeto de control de C\+\+ de objeto de diálogo o la cuadro\- ventana de c\+\+.  Como muchos otros objetos en el marco, los controles requieren la construcción de dos pasos.  Se debe llamar a la función miembro de **crear** de control como parte de la creación de la ventana primaria del cuadro de diálogo o el cuadro.  Para los cuadros de diálogo, esto se hace normalmente en [OnInitDialog](../Topic/CDialog::OnInitDialog.md), y para las ventanas de marco, en [OnCreate](../Topic/CWnd::OnCreate.md).  
  
 El ejemplo siguiente se muestra cómo puede declarar un objeto de `CEdit` en la declaración de clase de una clase derivada de diálogo y llame a la función miembro de **crear** en `OnInitDialog`.  Dado que el objeto de `CEdit` se declara como un objeto incrustado, automáticamente se crea cuando se construye el objeto cuadro de diálogo, pero aún debe inicializar con su propia función miembro de **crear** .  
  
 [!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/CPP/adding-controls-by-hand_1.h)]  
  
 La siguiente función de `OnInitDialog` coloque un rectángulo, llamar **crear** para crear el control de edición de Windows y para adjuntarlo al objeto sin inicializar de `CEdit` .  
  
 [!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/CPP/adding-controls-by-hand_2.cpp)]  
  
 Después de crear el objeto de edición, también puede establecer el foco al control llamando a la función miembro de `SetFocus` .  Por último, se devuelve 0 de `OnInitDialog` para mostrar que establece el foco.  Si se devuelve un valor distinto de cero, el administrador de diálogo establece el foco al primer elemento del control en la lista de elementos de cuadro de diálogo.  En la mayoría de los casos, es conveniente para agregar controles a los cuadros de diálogo con el editor de cuadros de diálogo.  
  
## Vea también  
 [Crear y usar controles](../mfc/making-and-using-controls.md)   
 [Controles](../mfc/controls-mfc.md)   
 [CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md)