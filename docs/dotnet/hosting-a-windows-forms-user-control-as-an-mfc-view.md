---
title: "Hospedar un control de usuario de Windows Forms como vista de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "hospedar un control de formularios Windows Forms [C++]"
  - "MFC [C++], compatibilidad con formularios Windows Forms"
  - "controles de formularios Windows Forms [C++], hospedar como vista de MFC"
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Hospedar un control de usuario de Windows Forms como vista de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC usa la clase CWinFormsView para hospedar un control de usuario de Windows Forms en una vista MFC.  Las vistas MFC de los formularios Windows Forms son controles ActiveX.  El control de usuario se hospeda como elemento secundario de la vista nativa y ocupa toda el área de cliente de la vista nativa.  
  
 El resultado final es similar al modelo utilizado por [CFormView Class](../mfc/reference/cformview-class.md).  Esto permite aprovechar las ventajas del runtime y del Diseñador de Windows Forms para crear vistas basadas en formulario enriquecidas.  
  
 Puesto que las vistas MFC de los formularios Windows Forms son controles ActiveX, no tienen el mismo valor de `hwnd` que las vistas MFC.  Tampoco se pueden pasar como puntero a una vista [CView](../mfc/reference/cview-class.md).  En general, use métodos de .NET Framework para trabajar con vistas de Windows Forms y descarte el uso de Win32.  
  
 Para obtener una aplicación de ejemplo que muestra el uso de Windows Forms con MFC, vea [Integración de MFC y Windows Forms](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
## En esta sección  
 [Cómo: Crear el control de usuario y hospedarlo en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)  
  
 [Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)  
  
 [Cómo: Llamar a propiedades y métodos del control de formularios Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)  
  
## Vea también  
 [Utilizar un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Cómo: Crear controles compuestos](../Topic/How%20to:%20Author%20Composite%20Controls.md)