---
title: "Utilizar un control de usuario de Windows Forms en MFC | Microsoft Docs"
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
  - "MFC [C++], compatibilidad con formularios Windows Forms"
  - "interoperabilidad [C++], formularios Windows Forms en MFC"
  - "interoperabilidad [C++], MFC"
  - "interoperabilidad [C++], formularios Windows Forms en MFC"
  - "interoperabilidad [C++], MFC"
  - "Soporte de Windows Forms [C++], MFC"
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar un control de usuario de Windows Forms en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Con las clases de soporte de formularios Windows Forms de MFC, puede hospedar controles de formularios Windows Forms en las aplicaciones MFC como controles ActiveX en cuadros de diálogo MFC o vistas. Además, los formularios Windows Forms se pueden hospedar como cuadros de diálogo MFC.  
  
 Las secciones siguientes describen cómo:  
  
-   Hospedar un control de formularios Windows Forms en un cuadro de diálogo MFC.  
  
-   Hospedar un control de usuario de formularios Windows Forms como vista MFC.  
  
-   Hospedar un formulario Windows Forms como un cuadro de diálogo MFC.  
  
> [!NOTE]
>  Integración de formularios Windows Forms de MFC sólo funciona en los proyectos que se vinculen dinámicamente a MFC (proyectos en el que se ha definido AFXDLL).  
  
> [!NOTE]
>  Al compilar la aplicación mediante una copia privada (modificada) de las interfaces de formularios Windows Forms de MFC DLL (mfcmifc80.dll), no se podrá instalar en la GAC, a menos que reemplace la clave de Microsoft con su propia clave de proveedor. Para obtener más información sobre la firma de ensamblados, vea [programar con ensamblados](../Topic/Programming%20with%20Assemblies.md) y [los ensamblados de nombre seguro (firma de ensamblados) (C++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).  
  
 Para aplicaciones de ejemplo utilizando formularios Windows Forms, vea [ejemplo BirthdayPicker: muestra recursos de .NET Framework con formularios Windows Forms](http://msdn.microsoft.com/es-es/ac932aed-5502-4667-be29-709bca435317), [ejemplo Calculator: calculadora de bolsillo de formularios de Windows](http://msdn.microsoft.com/es-es/2283b516-3b7e-45f2-80c4-fdcfb366ce25), y [ejemplo Scribble: aplicación de dibujo MDI](http://msdn.microsoft.com/es-es/f025da3e-659b-4222-b991-554a1b8b2358).  
  
 Para una aplicación de ejemplo que muestra formularios Windows Forms utilizados con MFC, vea [integración de Windows Forms y MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
 Si la aplicación MFC utiliza formularios Windows Forms, necesita redistribuir mfcmifc90.dll con la aplicación. Para obtener más información, consulte [redistribuir la biblioteca MFC](../ide/redistributing-the-mfc-library.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Hospedar un Control de usuario de Windows Forms en un cuadro de diálogo MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)  
  
 [Hospedar un Control de usuario de Windows Forms como vista MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)  
  
 [Hospedar un Control de usuario de Windows Forms como un cuadro de diálogo MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)  
  
## <a name="reference"></a>Referencia  
 [Clase CWinFormsControl](../mfc/reference/cwinformscontrol-class.md)  
  
 [Clase CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md)  
  
 [Clase CWinFormsView](../mfc/reference/cwinformsview-class.md)  
  
 [Interfaz de ICommandSource](../mfc/reference/icommandsource-interface.md)  
  
 [Interfaz ICommandTarget](../mfc/reference/icommandtarget-interface.md)  
  
 [Interfaz ICommandUI](../mfc/reference/icommandui-interface.md)  
  
 [Interfaz IView](../mfc/reference/iview-interface.md)  
  
 [CommandHandler](../Topic/CommandHandler%20Delegate.md)  
  
 [CommandUIHandler](../Topic/CommandUIHandler%20Delegate.md)  
  
 [DDX_ManagedControl](../Topic/DDX_ManagedControl.md)  
  
 [UICheckState](../Topic/UICheckState%20Enumeration.md)  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Formularios Windows Forms](../Topic/Windows%20Forms.md)  
  
 [Controles de Windows Forms](../Topic/Windows%20Forms%20Controls.md)  
  
 [Controles de usuario ASP.NET](../Topic/ASP.NET%20User%20Controls.md)  
  
## <a name="see-also"></a>Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [Vistas de formulario](../mfc/form-views-mfc.md)