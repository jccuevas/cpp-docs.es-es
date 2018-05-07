---
title: Archivos de encabezado y código fuente de controles o programas MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ab1ed04b9890fbed8de8b59354ab36d7be063e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-program-or-control-source-and-header-files"></a>Archivos de encabezado y código fuente de controles o programas MFC
Los siguientes archivos se crean al crear un proyecto MFC en Visual Studio, dependiendo de las opciones que seleccione para el proyecto que cree. Por ejemplo, el proyecto contiene *Nombre_proyecto*dlg.cpp y *Nombre_proyecto*dlg.h archivos solo si crea un proyecto basado en el cuadro de diálogo o una clase.  
  
 Todos estos archivos se encuentran en el *Nombre_proyecto* directorio y en la carpeta Header Files (archivos. h) o la carpeta Source Files (archivos .cpp) en el Explorador de soluciones.  
  
|Nombre del archivo|Descripción|  
|---------------|-----------------|  
|*Nombre_proyecto*. h|El archivo de inclusión principal para el programa o DLL. Contiene todos los símbolos globales y `#include` directivas para otros archivos de encabezado. Deriva el `CPrjnameApp` clase `CWinApp` y declara un `InitInstance` función miembro. Para un control, el `CPrjnameApp` clase se deriva de `COleControlModule`.|  
|*Nombre_proyecto*.cpp|El archivo de origen principal del programa. Crea un objeto de la clase `CPrjnameApp`, que se deriva de `CWinApp`e invalida el `InitInstance` función miembro.<br /><br /> Para archivos ejecutables, `CPrjnameApp::InitInstance` realiza varias tareas. Registra las plantillas de documento, que sirven como conexión entre documentos y vistas; crea una ventana de marco principal; y crea un documento vacío (o abre un documento si se especifica como un argumento de línea de comandos para la aplicación).<br /><br /> Para controles ActiveX (anteriormente OLE) y archivos DLL, `CProjNameApp::InitInstance` registra el generador de objetos del control con OLE mediante una llamada a `COleObjectFactory::RegisterAll` y realiza una llamada a `AfxOLEInit`. Además, la función miembro `CProjNameApp::ExitInstance` se utiliza para descargar el control de la memoria con una llamada a **AfxOleTerm**.<br /><br /> Este archivo también registra y anula el registro de control en la base de datos de registro de Windows mediante la implementación de la `DllRegisterServer` y `DllUnregisterServer` funciones.|  
|*Nombre_proyecto*ctrl.h, *Nombre_proyecto*ctrl.cpp|Declare e implemente la `CProjnameCtrl` clase. `CProjnameCtrl` se deriva de `COleControl`, y se definen las implementaciones esqueletos de algunas funciones miembro que inicializan, dibujar y serializan (cargan y guardan) el control. También se definen mensajes, eventos y mapas de envío.|  
|*Nombre_proyecto*dlg.cpp, *Nombre_proyecto*dlg.h|Se crea si elige una aplicación basada en el cuadro de diálogo. Los archivos derivan e implementan la clase de cuadro de diálogo, denominada `CProjnameDlg`e incluyen funciones miembro esqueleto para inicializar un cuadro de diálogo y realizar intercambio de datos de cuadros de diálogo (DDX). También se coloca la clase del cuadro de diálogo acerca de estos archivos en lugar de en *Nombre_proyecto*. cpp.|  
|Dlgproxy.cpp, Dlgproxy.h|En un cuadro de diálogo programa, la implementación y el encabezado archivos para la clase de proxy de automatización del proyecto para el cuadro de diálogo principal. Solo se utiliza si ha elegido compatibilidad de la automatización.|  
|*Nombre_proyecto*doc.cpp, *Nombre_proyecto*doc.h|Derivan e implementan la clase de documento, denominada `CProjnameDoc`e incluyen funciones miembro esqueleto para inicializar un documento, serializar (Guardar y cargar) un documento e implementar diagnósticos de depuración.|  
|*Nombre_proyecto*set.h/.cpp|Se crea si crea un programa que admite una base de datos y contiene la clase de conjunto de registros.|  
|*Nombre_proyecto*view.cpp, *Nombre_proyecto*view.h|Derivan e implementan la clase de vista, denominada `CProjnameView`, que se usa para mostrar e imprimir los datos del documento. La `CProjnameView` clase se deriva de una de las siguientes clases MFC:<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)<br />-   [CTreeView](../mfc/reference/ctreeview-class.md)<br />-   [CListView](../mfc/reference/clistview-class.md)<br />-   [CRichEditView](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [CView](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> Clase de vista del proyecto contiene funciones miembro esqueleto para dibujar la vista e implementar diagnósticos de depuración. Si ha habilitado la compatibilidad con la impresión, a continuación, las entradas de mapa de mensajes se agregan para el programa de instalación de impresión, imprimir y mensajes de comando de vista previa de impresión. Estas entradas de llamar a las funciones de miembro correspondiente en la clase de vista base.|  
|*Nombre_proyecto*PropPage.h, *Nombre_proyecto*PropPage.cpp|Declare e implemente la `CProjnamePropPage` clase. `CProjnamePropPage` se deriva de `COlePropertyPage` y una función miembro esqueleto, `DoDataExchange`, se proporciona para implementar el intercambio de datos y validación.|  
|IPframe.cpp, IPframe.h|Se crea si se selecciona la opción de miniservidor o servidor completo en el Asistente de aplicación **opciones de automatización** página (paso 3 de 6). Los archivos derivan e implementan la clase de ventana de marco en contexto, denominada **CInPlaceFrame**, usa cuando el servidor está en su lugar un programa contenedor activada.|  
|MainFrm.cpp, Mainfrm.h|Derivar la **CMainFrame** clase desde [CFrameWnd](../mfc/reference/cframewnd-class.md) (para aplicaciones SDI) o [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) (para aplicaciones MDI). El **CMainFrame** clase controla la creación de botones de barra de herramientas y la barra de estado, si se seleccionan las opciones correspondientes en el Asistente de aplicación **opciones de la aplicación** página (paso 4 de 6). Para obtener información sobre el uso de **CMainFrame**, consulte [clases de ventana de marco que crea el Asistente para aplicaciones](../mfc/frame-window-classes-created-by-the-application-wizard.md).|  
|ChildFrm.cpp, Childfrm.h|Derivar la **CChildFrame** clase [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md). El **CChildFrame** clase se utiliza para ventanas de marco de documento MDI. Estos archivos se crean siempre si selecciona la opción de MDI.|  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Archivos de encabezado y código fuente de controles o programas ATL](../ide/atl-program-or-control-source-and-header-files.md)   
 [Proyectos de CLR](../ide/files-created-for-clr-projects.md)