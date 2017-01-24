---
title: "Adding Controls to a Dialog Causes the Dialog to No Longer Function | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "controls [C++], troubleshooting"
  - "common controls, troubleshooting"
  - "troubleshooting controls"
  - "dialog boxes, troubleshooting"
  - "dialog box controls, troubleshooting"
  - "InitCommonControls"
ms.assetid: b2dd4574-ea59-4343-8d65-b387cead5da6
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Controls to a Dialog Causes the Dialog to No Longer Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tras agregar un control común o un control Rich Edit a un cuadro de diálogo, el control deja de aparecer cuando se comprueba el cuadro de diálogo o ni siquiera aparece el propio cuadro de diálogo.  
  
 **Ejemplo del problema**  
  
1.  Cree un proyecto Win32 y modifique la configuración de la aplicación para crear una aplicación para Windows \(no de consola\).  
  
2.  En la [Vista de recursos](../windows/resource-view-window.md), haga doble clic en el archivo .rc.  
  
3.  En la opción del cuadro de diálogo, haga doble clic en el cuadro **Acerca de**.  
  
4.  Agregue un **IP Address Control** al cuadro de diálogo.  
  
5.  Guarde y **recompile todo**.  
  
6.  Ejecute el programa.  
  
7.  En el menú **Ayuda** del cuadro de diálogo, haga clic en el comando **Acerca de**; no se abrirá ningún cuadro de diálogo.  
  
 **Causa**  
  
 Actualmente, el Editor de cuadros de diálogo no agrega un código al proyecto de forma automática cuando se arrastran y colocan los siguientes controles comunes o controles Rich Edit en un cuadro de diálogo.  Visual Studio tampoco muestra un error o una advertencia cuando ocurre este problema.  Deberá agregar el código al control manualmente.  
  
||||  
|-|-|-|  
|Slider Control|Tree Control|Date Time Picker|  
|Spin Control|Tab Control|Month Calendar|  
|Progress Control|Animation Control|IP Address Control|  
|Hot Key|Rich Edit Control|Extended Combo Box|  
|List Control|Rich Edit 2.0 Control|Control personalizado|  
  
## Corrección para los controles comunes  
 Para usar controles comunes en un cuadro de diálogo, llame a [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) o **AFXInitCommonControls** antes de crear el cuadro de diálogo.  
  
## Corrección para controles RichEdit  
 Llame a **LoadLibrary** para los controles Rich Edit.  Para obtener más información, vea [Utilizar el control RichEdit 1.0 con MFC](../mfc/using-the-richedit-1-0-control-with-mfc.md), [Acerca de los controles Rich Edit](http://msdn.microsoft.com/library/windows/desktop/bb787873) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)], e [Información general sobre el control Rich Edit](../mfc/overview-of-the-rich-edit-control.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Troubleshooting the Dialog Editor](../mfc/troubleshooting-the-dialog-editor.md)   
 [Dialog Editor](../mfc/dialog-editor.md)