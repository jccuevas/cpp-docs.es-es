---
title: "Tipo de aplicaci&#243;n, Asistente para aplicaciones MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.apptype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bibliotecas estáticas, MFC"
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Tipo de aplicaci&#243;n, Asistente para aplicaciones MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice esta página del [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md) para diseñar y agregar características básicas a una nueva aplicación MFC.  
  
 **Tipo de aplicación**  
 Especifica el tipo de compatibilidad con documentos que desea crear en la aplicación.  El tipo de aplicación que seleccione determina las opciones de interfaz de usuario disponibles para la aplicación.  Para obtener más información, vea [Características de la interfaz de usuario, Asistente para aplicaciones MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md).  
  
 Para obtener más información acerca de los tipos de documentos, vea:  
  
-   [SDI y MDI](../../mfc/sdi-and-mdi.md)  
  
-   [Ventanas de marco](../../mfc/frame-windows.md)  
  
-   [Clases de ventana de marco](../../mfc/frame-window-classes.md)  
  
-   [Documentos, vistas y el marco](../../mfc/documents-views-and-the-framework.md)  
  
-   [Cuadros de diálogo](../../mfc/dialog-boxes.md)  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Documento único**|Crea una arquitectura de interfaz de un único documento para la aplicación, con una clase de vista basada en [CView Class](../../mfc/reference/cview-class.md).  Puede cambiar la clase base de la vista en la página [Clases generadas, Asistente para aplicaciones MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) del asistente.  Para crear una aplicación basada en formularios, por ejemplo, utilice [CFormView Class](../../mfc/reference/cformview-class.md) como clase de vista.<br /><br /> En este tipo de aplicación, la ventana de marco del documento sólo puede contener un documento.|  
|**Múltiples documentos**|Crea una arquitectura de interfaz de múltiples documentos para la aplicación, con una clase de vista basada en `CView`.  Puede cambiar la clase base para la vista en la página **Clases generadas** del asistente.  Para crear una aplicación basada en formularios, por ejemplo, utilice `CFormView` como clase de vista.<br /><br /> En este tipo de aplicación, la ventana de marco del documento puede contener varias ventanas secundarias.|  
|**Organización por fichas**|Coloca cada documento en una ficha distinta.|  
|**Basada en cuadros de diálogo**|Crea una arquitectura basada en cuadros de diálogo para la aplicación, con una clase de cuadro de diálogo basada en `CDialog`. Para crear un cuadro de diálogo HTML, active la casilla **Utilizar cuadro de diálogo HTML**.|  
|**Usar cuadro de diálogo HTML**|Sólo se utiliza para aplicaciones basadas en un cuadro de diálogo.  Deriva la clase de cuadro de diálogo de [CDHtmlDialog Class](../../mfc/reference/cdhtmldialog-class.md) en lugar de [CDialog Class](../../mfc/reference/cdialog-class.md).  Si activa esta casilla, aparecerá `CDHtmlDialog` en el cuadro **Clase base** de la página [Clases generadas, Asistente para aplicaciones MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) del asistente.<br /><br /> Un cuadro de diálogo derivado de `CDHtmlDialog` muestra cuadros de diálogo basados en HTML, realiza el intercambio de datos con controles HTML y controla eventos HTML.|  
|**Múltiples documentos de nivel superior**|Crea una arquitectura de múltiples documentos de nivel superior para la aplicación, con una clase de vista basada en `CView`.<br /><br /> En este tipo de aplicación, cuando un usuario hace clic en **Nuevo** \(o en **Nuevo marco**\) en el menú **Archivo**, la aplicación crea una ventana cuya ventana primaria implícita es el escritorio.  El nuevo marco de documento aparece en la barra de tareas y no está restringido al área de cliente de la ventana de la aplicación.|  
  
 **Compatibilidad con la arquitectura documento\/vista**  
 Especifica si se va a incluir la arquitectura de documento\/vista en la aplicación mediante [CDocument Class](../../mfc/reference/cdocument-class.md) y [CView Class](../../mfc/reference/cview-class.md) \(valor predeterminado\).  Desactive esta casilla si va a adaptar una aplicación que no está basada en MFC o si desea reducir el tamaño del archivo ejecutable compilado.  De forma predeterminada, una aplicación sin la arquitectura documento\/vista se deriva de [CWinApp Class](../../mfc/reference/cwinapp-class.md) y no incluye compatibilidad con MFC para abrir un documento a partir de un archivo de disco.  
  
 **Idioma de los recursos**  
 Establece el idioma de los recursos.  La lista muestra los idiomas disponibles en el sistema, instalados por Visual Studio.  Si desea seleccionar un idioma distinto del idioma del sistema, deberá estar instalada la carpeta de plantillas correspondiente a ese idioma.  Para obtener más información sobre cómo instalar recursos de idiomas distintos de los predeterminados disponibles en la lista **Idioma de los recursos**, vea [Compatibilidad del asistente con otros idiomas](../../ide/wizard-support-for-other-languages.md).  
  
 El idioma que seleccione quedará reflejado en la opción **Cadenas traducidas** de la página [Cadenas de plantillas de documentos, Asistente para aplicaciones MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md) del asistente.  
  
 **Utilizar bibliotecas de Unicode**  
 Especifica si se utiliza una versión Unicode o distinta de Unicode de las bibliotecas MFC.  
  
 **Estilo del proyecto**  
 Indica si la aplicación tiene MFC estándar, el Explorador de archivos, Visual Studio, o arquitectura y presentación de Office.  Para obtener más información, vea [Crear una aplicación MFC estilo Explorador de archivos](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md).  
  
|Opción|Descripción|  
|------------|-----------------|  
|**MFC estándar**|Proporciona una arquitectura de aplicación MFC estándar.|  
|**Explorador de archivos**|Implementar un archivo Explorador\- como la aplicación mediante una ventana divisora donde es [CTreeView Class](../../mfc/reference/ctreeview-class.md) el panel izquierdo y el panel derecho es [CListView Class](../../mfc/reference/clistview-class.md).|  
|**Visual Studio**|Implementa una aplicación de tipo Visual Studio que contiene cuatro paneles acoplables \(**Vista de archivos**, **Vista de clases**, **Propiedades** y **Resultados**\) derivados de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) y una ventana de marco principal derivada de [CMDIFrameWndEx \(Clase\)](../../mfc/reference/cmdiframewndex-class.md) \(valor predeterminado\).|  
|**Office**|Implementa una aplicación de tipo Office que contiene una cinta de opciones derivada de [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md), una barra de Outlook derivada de [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md), una barra de título derivada de [CMFCCaptionBar \(Clase\)](../../mfc/reference/cmfccaptionbar-class.md) y un marco principal derivado de [CMDIFrameWndEx \(Clase\)](../../mfc/reference/cmdiframewndex-class.md).|  
  
 **Estilo visual y colores**  
 Determina el estilo visual de la aplicación.  Están disponibles las siguientes opciones:  
  
-   **Windows nativo\/predeterminado**  
  
-   **Office 2003**  
  
-   **Visual Studio 2005**  
  
-   **Office 2007 \(tema Azul\)**  
  
-   **Office 2007 \(tema Negro\)**  
  
-   **Office 2007 \(tema Plata\)**  
  
-   **Office 2007 \(tema Aguamarina\)**  
  
 **Habilitar el cambio de estilos visuales**  
 Especifica si el usuario puede cambiar el estilo visual de la aplicación en tiempo de ejecución, normalmente seleccionando el estilo visual correspondiente de un menú o cinta de opciones.  
  
 **Uso de MFC**  
 Especifica la forma de vincular a la biblioteca MFC.  De forma predeterminada, MFC se vincula como un archivo DLL compartido.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Usar MFC en un archivo DLL compartido**|Vincula la biblioteca MFC a una aplicación como un archivo DLL compartido.  La aplicación hace llamadas a la biblioteca MFC en tiempo de ejecución.  Esta opción reduce los requisitos de memoria y disco de las aplicaciones que constan de varios archivos ejecutables que utilizan la biblioteca MFC.  Tanto las aplicaciones Win32 como las aplicaciones MFC pueden llamar a las funciones del archivo DLL \(valor predeterminado\).|  
|**Usar MFC en una biblioteca estática**|Vincula una aplicación a la biblioteca MFC en tiempo de compilación.|  
  
## Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Tipos de archivos creados para proyectos de Visual C\+\+](../../ide/file-types-created-for-visual-cpp-projects.md)