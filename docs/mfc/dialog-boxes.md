---
title: "Cuadros de di&#225;logo | Microsoft Docs"
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
  - "CDialog (clase), cuadros de diálogo de MFC"
  - "cuadros de diálogo de MFC"
  - "MFC, cuadros de diálogo"
  - "cuadros de diálogo modales, cuadros de diálogo de MFC"
  - "cuadros de diálogo no modales, cuadros de diálogo de MFC"
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Cuadros de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Aplicaciones para Windows con frecuencia se comunican con el usuario a través de los cuadros de diálogo.  La clase [CDialog](../mfc/reference/cdialog-class.md) proporciona una interfaz para administrar los cuadros de diálogo, el editor de cuadros de diálogo de Visual C\+\+ facilita el diseño los cuadros de diálogo y crear los recursos de la diálogo\- plantilla, y los asistentes para código simplifican el proceso de inicializar y de validar los controles en un cuadro de diálogo y de recopilar los valores especificados por el usuario.  
  
 Los cuadros de diálogo contienen controles, incluidos:  
  
-   Controles comunes de Windows como cuadros de edición, pulsadores, cuadros de lista, cuadros combinados, controles de árbol, controles de lista, y indicadores de progreso.  
  
-   Controles ActiveX.  
  
-   Controles Propietario\- dibujados: controles que es responsable del gráfico en el cuadro de diálogo.  
  
 La mayoría de los cuadros de diálogo son modales, que exigen al usuario cerrar el cuadro de diálogo antes de utilizar cualquier otra parte del programa.  Pero es posible crear cuadros de diálogo no modal, que permiten a los usuarios ejecutar otras ventanas mientras el cuadro de diálogo está abierto.  MFC admite ambas clases de cuadro de diálogo con la clase `CDialog`.  Los controles se organizan y se administran mediante un recurso de la diálogo\- plantilla, mediante [editor de cuadros de diálogo](../mfc/dialog-editor.md).  
  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md), también conocido como cuadros de diálogo de la ficha, son los cuadros de diálogo que contienen las “páginas” de controles de cuadro de diálogo distintos.  Cada página tiene una carpeta archivos “tab” en la parte superior.  Hacer clic en una pestaña aporta esa página cabeza del cuadro de diálogo.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Ejemplo: Mostrar un cuadro de diálogo mediante un comando de menú](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)  
  
-   [Componentes de cuadro de diálogo en el marco](../mfc/dialog-box-components-in-the-framework.md)  
  
-   [Cuadros de diálogo modales y no modales](../mfc/modal-and-modeless-dialog-boxes.md)  
  
-   [Hojas de propiedades y páginas de propiedades](../mfc/property-sheets-and-property-pages-mfc.md) en un cuadro de diálogo  
  
-   [Crear el recurso de cuadro de diálogo](../mfc/creating-the-dialog-resource.md)  
  
-   [Crear una clase de cuadro de diálogo con los asistentes para código](../mfc/creating-a-dialog-class-with-code-wizards.md)  
  
-   [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)  
  
-   [Diálogo de intercambio de datos \(DDX\) y validación \(DDV\)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [Acceso Tipo\- seguro a los controles de un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [Mensajes de Windows a la clase](../mfc/mapping-windows-messages-to-your-class.md)  
  
-   [Funciones normalmente invalidadas miembro](../mfc/commonly-overridden-member-functions.md)  
  
-   [Funciones normalmente agregadas de miembro](../mfc/commonly-added-member-functions.md)  
  
-   [Clases comunes de diálogo](../mfc/common-dialog-classes.md)  
  
-   [Cuadros de diálogo de OLE](../mfc/dialog-boxes-in-ole.md)  
  
-   Cree una aplicación cuya interfaz de usuario es cuadro de diálogo: vea los programas de ejemplo de [CMNCTRL1](../top/visual-cpp-samples.md) o de [CMNCTRL2](../top/visual-cpp-samples.md) .  El Asistente para aplicaciones proporciona esta opción también.  
  
-   [Ejemplos](../mfc/dialog-sample-list.md)  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)