---
title: "Archivos de encabezado y c&#243;digo fuente de controles o programas MFC | Microsoft Docs"
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
  - "tipos de archivo [C++], código fuente y encabezados de MFC"
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Archivos de encabezado y c&#243;digo fuente de controles o programas MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al crear un proyecto MFC en Visual Studio se crearán los siguientes archivos, en función de las opciones que seleccione para el proyecto que va a crear.  Por ejemplo, el proyecto sólo contendrá los archivos *Nombre\_proyecto*dlg.cpp y *Nombre\_proyecto*dlg.h si crea un proyecto o una clase basados en un cuadro de diálogo.  
  
 Todos estos archivos se encuentran en el directorio *Nombre\_proyecto* y en la carpeta Header Files \(archivos .h\) o en la carpeta Source Files \(archivos .cpp\) en el Explorador de soluciones.  
  
|Nombre de archivo|Descripción|  
|-----------------------|-----------------|  
|*Nombre\_proyecto*.h|Archivo de inclusión principal del programa o el archivo DLL.  Contiene todos los símbolos globales y directivas `#include` para los demás archivos de encabezado.  Deriva la clase `CPrjnameApp` de `CWinApp` y declara una función miembro `InitInstance`.  Para un control, la clase `CPrjnameApp` se deriva de `COleControlModule`.|  
|*Nombre\_proyecto.*cpp|Archivo de código fuente del programa principal.  Crea un objeto de la clase `CPrjnameApp`, que se deriva de `CWinApp`, y reemplaza la función miembro `InitInstance`.<br /><br /> Para archivos ejecutables, `CPrjnameApp::InitInstance` lleva a cabo varias tareas.  Registra plantillas de documento, que sirven como conexión entre documentos y vistas, crea una ventana de marco principal y crea un documento vacío \(o abre un documento si se especifica uno como argumento de línea de comandos a la aplicación\).<br /><br /> Para archivos DLL y controles ActiveX \(antes denominados controles OLE\), `CProjNameApp::InitInstance` registra el generador de objetos del control con OLE mediante una llamada a `COleObjectFactory::RegisterAll` y hace una llamada a `AfxOLEInit`.  Además, se utiliza la función miembro `CProjNameApp::ExitInstance` para descargar el control de la memoria con una llamada a **AfxOleTerm**.<br /><br /> Este archivo también registra \(y elimina del registro\) el control en la base de datos de registro de Windows implementando las funciones `DllRegisterServer` y `DllUnregisterServer`.|  
|*Nombre\_proyecto*ctrl.h, *Nombre\_proyecto*ctrl.cpp|Declara e implementa la clase `CProjnameCtrl`.  `CProjnameCtrl` se deriva de `COleControl` y se definen las implementaciones esqueleto de algunas funciones miembro que inicializan, dibujan y serializan \(cargan y guardan\) el control.  También se definen mensajes, eventos y mapas de envíos.|  
|*Nombre\_proyecto*dlg.cpp, *Nombre\_proyecto*dlg.h|Se crea si elige una aplicación basada en un cuadro de diálogo.  Los archivos derivan e implementan la clase de cuadro de diálogo, denominada `CProjnameDlg`, e incluyen funciones miembro esqueleto para inicializar un cuadro de diálogo y realizar intercambio de datos de cuadro de diálogo \(DDX\).  También se coloca en estos archivos la clase del cuadro de diálogo Acerca de, en lugar de en *Nombre\_proyecto*.cpp.|  
|Dlgproxy.cpp, Dlgproxy.h|En un programa basado en un cuadro de diálogo, el archivo de implementación y de encabezado de la clase de proxy de automatización del proyecto para el cuadro de diálogo principal.  Sólo se utiliza si eligió compatibilidad con la automatización.|  
|*Nombre\_proyecto*doc.cpp, *Nombre\_proyecto*doc.h|Deriva e implementa la clase de documento, denominada `CProjnameDoc`, e incluye funciones miembro esqueleto para inicializar un documento, serializar \(guardar y cargar\) un documento e implementar diagnósticos de depuración.|  
|*Nombre\_proyecto*set.h\/.cpp|Se crea si crea un programa compatible con bases de datos y que contenga la clase de conjunto de registros.|  
|*Nombre\_proyecto*view.cpp, *Nombre\_proyecto*view.h|Deriva e implementa la clase de vista, denominada `CProjnameView`, que se utiliza para mostrar e imprimir los datos del documento.  La clase `CProjnameView` se deriva de una de las siguientes clases MFC:<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)<br />-   [CTreeView](../mfc/reference/ctreeview-class.md)<br />-   [CListView](../mfc/reference/clistview-class.md)<br />-   [CRichEditView](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [CView](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> La clase de vista del proyecto contiene funciones miembro esqueleto para dibujar la vista e implementar diagnósticos de depuración.  Si ha habilitado la compatibilidad con la impresión, se agregarán entradas de mapa de mensajes para mensajes de comandos de impresión, configuración de la impresión y vista previa de impresión.  Estas entradas llaman a las funciones miembro correspondientes de la clase de vista base.|  
|*Nombre\_proyecto*PropPage.h, *Nombre\_proyecto*PropPage.cpp|Declara e implementa la clase `CProjnamePropPage`.  `CProjnamePropPage` se deriva de `COlePropertyPage` y se proporciona una función miembro esqueleto, `DoDataExchange`, para implementar el intercambio y la validación de datos.|  
|IPframe.cpp, IPframe.h|Se crea si se selecciona la opción de Miniservidor o Servidor completo en la página **Opciones de automatización** \(paso 3 de 6\) del asistente para aplicaciones.  Los archivos derivan e implementan la clase de ventana de marco en el contexto, denominada **CInPlaceFrame**, que se utiliza cuando un programa contenedor activa el servidor en el contexto.|  
|Mainfrm.cpp, Mainfrm.h|Deriva la clase **CMainFrame** de [CFrameWnd](../mfc/reference/cframewnd-class.md) \(para aplicaciones SDI\) o de [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) \(para aplicaciones MDI\).  La clase **CMainFrame** controla la creación de botones de barra de herramientas y la barra de estado, si se seleccionan las opciones correspondientes en la página **Opciones de la aplicación** \(paso 4 de 6\) del asistente para aplicaciones.  Para obtener información acerca del uso de **CMainFrame**, vea [Clases de ventana de marco que crea el Asistente para aplicaciones](../mfc/frame-window-classes-created-by-the-application-wizard.md).|  
|Childfrm.cpp, Childfrm.h|Deriva la clase **CChildFrame** a partir de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).  La clase **CChildFrame** se utiliza para ventanas de marco de documento MDI.  Estos archivos se crearán siempre que seleccione la opción MDI.|  
  
## Vea también  
 [Tipos de archivos creados para proyectos de Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Archivos de encabezado y código fuente de controles o programas ATL](../ide/atl-program-or-control-source-and-header-files.md)   
 [Proyectos de CLR](../ide/files-created-for-clr-projects.md)