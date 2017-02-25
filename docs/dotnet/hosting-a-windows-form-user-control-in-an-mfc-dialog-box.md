---
title: "Hospedar un control de usuario de Windows Forms en un cuadro de di&#225;logo MFC | Microsoft Docs"
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
  - "hospedar un control de formularios Windows Forms [C++]"
  - "MFC [C++], compatibilidad con formularios Windows Forms"
  - "formularios Windows Forms [C++], compatibilidad con MFC"
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Hospedar un control de usuario de Windows Forms en un cuadro de di&#225;logo MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC hospeda un control de Windows Forms como un tipo especial de control ActiveX y se comunica con él por medio de interfaces ActiveX y propiedades y métodos de la clase <xref:System.Windows.Forms.Control>.  Se recomienda usar propiedades y métodos de .NET Framework para trabajar con el control.  
  
 Para obtener una aplicación de ejemplo que muestra el uso de Windows Forms con MFC, vea [Integración de MFC y Windows Forms](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
> [!NOTE]
>  En la versión actual, un objeto `CDialogBar`  no puede hospedar controles de formularios Windows Forms.  
  
## En esta sección  
 [Cómo: Crear el control de usuario y hospedarlo en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)  
  
 [Cómo: Enlazar datos DDX\/DDV con formularios Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)  
  
 [Cómo: Recibir eventos de Windows Forms de clases nativas de C\+\+](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)  
  
## Referencia  
 [CWinFormsControl Class](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog Class](../mfc/reference/cdialog-class.md) &#124; [CWnd \(clase\)](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>  
  
## Vea también  
 [Utilizar un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Diferencias de programación entre formularios Windows Forms y MFC](../dotnet/windows-forms-mfc-programming-differences.md)   
 [Hospedar un control de usuario de Windows Forms como vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)