---
title: "Ejemplo: Mostrar un cuadro de di&#225;logo a trav&#233;s de un comando de men&#250; | Microsoft Docs"
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
  - "cuadros de diálogo, MFC"
  - "ejemplos [MFC], cuadros de diálogo"
  - "elementos de menú, ejemplos"
  - "cuadros de diálogo de MFC, mostrar"
  - "cuadros de diálogo de MFC, ejemplos"
  - "cuadros de diálogo modales, mostrar"
  - "cuadros de diálogo no modales, mostrar"
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ejemplo: Mostrar un cuadro de di&#225;logo a trav&#233;s de un comando de men&#250;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema contiene procedimientos:  
  
-   Muestra un cuadro de diálogo modal mediante un comando de menú.  
  
-   Muestra un cuadro de diálogo no modal mediante un comando de menú.  
  
 Ambos procedimientos de ejemplo son para las aplicaciones MFC y funcionarán en una aplicación creada con [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md).  
  
 Los procedimientos utilizan los nombres y los valores siguientes:  
  
|Elemento|Nombre o valor|  
|--------------|--------------------|  
|Aplicación|DisplayDialog|  
|Comando de menú|Comando de prueba en el menú ver; Identificador de comando \= ID\_VIEW\_TEST|  
|Cuadro de diálogo|Cuadro de diálogo de prueba; Clase \= CTestDialog; Archivo de encabezado \= TestDialog.h; Variable \= testdlg, ptestdlg|  
|Controlador de comandos|OnViewTest|  
  
### Para mostrar un cuadro de diálogo modal  
  
1.  Cree el comando de menú; vea [Crear menús o elementos de menú](../windows/creating-a-menu.md).  
  
2.  Cree el cuadro de diálogo; vea [Iniciar el editor de cuadros de diálogo](../mfc/creating-a-new-dialog-box.md).  
  
3.  Agregue una clase para el cuadro de diálogo.  Vea [Agregar una clase](../ide/adding-a-class-visual-cpp.md) para obtener más información.  
  
4.  En **vista de clases**, seleccione la clase document \(CDisplayDialogDoc\).  En la ventana de **Propiedades** , haga clic en el botón de **Eventos** .  Haga doble clic en el identificador de comando de menú \(ID\_VIEW\_TEST\) en el panel izquierdo de la ventana de **Propiedades** y de **Comando**seleccione.  En el panel derecho, haga clic en la flecha abajo y seleccione **\<Add\> OnViewTest**.  
  
     Si agregó el comando de menú a gran sistema de una aplicación MDI, seleccione la clase de aplicación \(CDisplayDialogApp\) en su lugar.  
  
5.  Agregue la siguiente instrucción de inclusión a CDisplayDialogDoc.cpp \(o a CDisplayDialogApp.cpp\) después de las instrucciones existentes de inclusión:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
6.  Agregue el código siguiente a `OnViewTest` para implementar la función:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]  
  
### Para mostrar un cuadro de diálogo no modal  
  
1.  Haga los primeros cuatro pasos para mostrar un cuadro de diálogo modal, excepto seleccione la clase de vista \(CDisplayDialogView\) en el paso 4.  
  
2.  Edición DisplayDialogView.h:  
  
    -   Declare la clase de cuadro de diálogo que precede a la primera declaración de clase:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_3.h)]  
  
    -   Declare un puntero al cuadro de diálogo después de la sección pública de atributos:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_4.h)]  
  
3.  Edición DisplayDialogView.cpp:  
  
    -   Agregue la siguiente instrucción include después de las instrucciones existentes de inclusión:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
    -   Agregue el código siguiente al constructor:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]  
  
    -   Agregue el código siguiente al destructor:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]  
  
    -   Agregue el código siguiente a `OnViewTest` para implementar la función:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]  
  
 También, vea el siguiente artículo de Knowledge Base:  
  
-   Q251059: HOWTO: Proporcione el nombre de clase de ventana Own para un cuadro de diálogo de MFC  
  
## Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Cuadros de diálogo modales y no modales](../mfc/modal-and-modeless-dialog-boxes.md)