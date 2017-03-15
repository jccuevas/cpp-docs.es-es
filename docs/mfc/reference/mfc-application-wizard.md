---
title: "Asistente para aplicaciones MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos ejecutables, crear"
  - "Asistente para aplicaciones MFC"
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Asistente para aplicaciones MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El Asistente para aplicaciones MFC genera una aplicación que, al compilarse, implementa las características básicas de una aplicación ejecutable para Windows \(.exe\).  La aplicación MFC inicial incluye archivos de código fuente de C\+\+ \(.cpp\), archivos de recursos \(.rc\), archivos de encabezado \(.h\) y un archivo de proyecto \(.vcxproj\).  El código generado en estos archivos iniciales se basa en MFC.  
  
> [!NOTE]
>  El asistente creará archivos adicionales para el proyecto en función de las opciones que seleccione.  Por ejemplo, si selecciona **Ayuda contextual** en la página [Características avanzadas](../../mfc/reference/advanced-features-mfc-application-wizard.md), el asistente crea los archivos necesarios para compilar los archivos de Ayuda del proyecto.  Para obtener más información sobre los archivos que crea el asistente, vea [Tipos de archivos creados para proyectos de Visual C\+\+](../../ide/file-types-created-for-visual-cpp-projects.md) y el archivo Readme.txt del proyecto.  
  
## Información general  
 En esta página del asistente se describe la configuración actual para la aplicación MFC que va a crear.  De forma predeterminada, el asistente crea un proyecto de la manera siguiente:  
  
-   [Tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md)  
  
    -   El proyecto se crea con compatibilidad con la interfaz de múltiples documentos \(MDI\) organizada por pestañas.  Para obtener más información, vea [SDI y MDI](../../mfc/sdi-and-mdi.md).  
  
    -   El proyecto utiliza la [Arquitectura documento\/vista](../../mfc/document-view-architecture.md).  
  
    -   El proyecto utiliza las bibliotecas de Unicode.  
  
    -   El proyecto se crea utilizando el estilo de proyecto de Visual Studio y permite el cambio de estilos visuales.  
  
    -   El proyecto utiliza MFC en un archivo DLL compartido.  Para obtener más información, vea [Archivos DLL en Visual C\+\+](../../build/dlls-in-visual-cpp.md).  
  
-   [Compatibilidad con documentos compuestos, Asistente para aplicaciones MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)  
  
    -   El proyecto no proporciona compatibilidad con documentos compuestos.  
  
-   [Cadenas de plantillas de documentos, Asistente para aplicaciones MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)  
  
    -   El proyecto utiliza su nombre para las cadenas de plantillas de documentos predeterminadas.  
  
-   [Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md)  
  
    -   El proyecto no proporciona compatibilidad con bases de datos.  
  
-   [Características de la interfaz de usuario, Asistente para aplicaciones MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)  
  
    -   El proyecto implementa las características estándar de las interfaces de usuario de Windows, como un menú de sistema, una barra de estado, cuadros para maximizar y minimizar, un cuadro **Acerca de**, una barra de menús y una barra de acoplamiento estándar y marcos secundarios.  
  
-   [Características avanzadas, Asistente para aplicaciones MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)  
  
    -   El proyecto ofrece compatibilidad con la impresión y la vista previa de impresión.  
  
    -   El proyecto admite controles ActiveX.  Para obtener más información, vea [Secuencia de operaciones para crear controles ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).  
  
    -   El proyecto no ofrece compatibilidad con [automatización](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets](../../mfc/windows-sockets-in-mfc.md) ni Active Accessibility.  
  
    -   El proyecto admite un panel acoplable **Explorador**, un panel acoplable **Resultados** y un panel acoplable **Propiedades**.  
  
-   [Clases generadas, Asistente para aplicaciones MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)  
  
    -   La clase de vista del proyecto se deriva de [CView Class](../../mfc/reference/cview-class.md).  
  
    -   La clase de aplicación del proyecto se deriva de [CWinAppEx Class](../../mfc/reference/cwinappex-class.md).  
  
    -   La clase de documento del proyecto se deriva de [CDocument Class](../../mfc/reference/cdocument-class.md).  
  
    -   La clase de marco principal del proyecto se deriva de [CMDIFrameWndEx \(Clase\)](../../mfc/reference/cmdiframewndex-class.md).  
  
    -   La clase de marco secundario del proyecto se deriva de [Clase CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md).  
  
 Para cambiar esta configuración predeterminada, haga clic en el título de la pestaña correspondiente en la columna izquierda del asistente y realice las modificaciones en la página que aparece.  
  
 Una vez creado el proyecto de aplicación MFC, puede agregar objetos o controles al proyecto mediante los [asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md) de Visual C\+\+.  
  
## Vea también  
 [Crear una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md)   
 [Aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md)   
 [Usar las clases para escribir aplicaciones para Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)