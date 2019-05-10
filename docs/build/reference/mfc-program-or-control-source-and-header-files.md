---
title: Archivos de encabezado y código fuente de controles o programas MFC
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
ms.openlocfilehash: 89e02054b72946c4b1b773ce79b1c380da6ef01a
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446258"
---
# <a name="mfc-program-or-control-source-and-header-files"></a>Archivos de encabezado y código fuente de controles o programas MFC

Los archivos siguientes se crean al crear un proyecto MFC en Visual Studio, en función de las opciones que se seleccionen para el proyecto que se crea. Por ejemplo, el proyecto contiene los archivos *Nombre_proyecto*dlg.cpp y *Nombre_proyecto*dlg.h solo si se crea un proyecto o una clase basado en un cuadro de diálogo.

Todos estos archivos se encuentran en el directorio *Nombre_proyecto* y en las carpetas Archivos de encabezado (archivos .h) o Archivos de código fuente (archivos .cpp) del Explorador de soluciones.

|Nombre del archivo|Descripción|
|---------------|-----------------|
|*Nombre_proyecto*.h|El archivo de inclusión principal para el programa o archivo DLL. Contiene todos los símbolos globales y directivas `#include` para otros archivos de encabezado. Deriva la clase `CPrjnameApp` de `CWinApp` y declara una función miembro `InitInstance`. Para un control, la clase `CPrjnameApp` se deriva de `COleControlModule`.|
|*Nombre_proyecto*.cpp|El archivo de código fuente principal del programa. Crea un objeto de la clase `CPrjnameApp`, que se deriva de `CWinApp`, e invalida la función miembro `InitInstance`.<br /><br /> Para los archivos ejecutables, `CPrjnameApp::InitInstance` realiza varias tareas. Registra las plantillas de documento, que sirven como conexión entre los documentos y las vistas; crea una ventana de marco principal y un documento vacío (o abre un documento si se especifica uno como un argumento de la línea de comandos para la aplicación).<br /><br /> Para los archivos DLL y los controles ActiveX (anteriormente OLE), `CProjNameApp::InitInstance` registra el generador de objetos del control con OLE mediante una llamada a `COleObjectFactory::RegisterAll` y realiza una llamada a `AfxOLEInit`. Además, se usa la función miembro `CProjNameApp::ExitInstance` para descargar el control de la memoria con una llamada a **AfxOleTerm**.<br /><br /> Este archivo también registra y anula el registro del control en la base de datos de registro de Windows mediante la implementación de las funciones `DllRegisterServer` y `DllUnregisterServer`.|
|*Nombre_proyecto*ctrl.h, *Nombre_proyecto*ctrl.cpp|Declaran e implementan la clase `CProjnameCtrl`. `CProjnameCtrl` se deriva de `COleControl`, y se definen las implementaciones de esqueleto de algunas funciones miembro que inicializan, dibujan y serializan (cargan y guardan) el control. También se definen mapas de mensajes, eventos y envío.|
|*Nombre_proyecto*dlg.cpp, *Nombre_proyecto*dlg.h|Se crean si se selecciona una aplicación basada en cuadros de diálogo. Los archivos derivan e implementan la clase de cuadro de diálogo, denominada `CProjnameDlg`, e incluyen funciones miembro de esqueleto para inicializar un cuadro de diálogo y realizar intercambio de datos de cuadros de diálogo (DDX). La clase de cuadro de diálogo Acerca de también se coloca en estos archivos en lugar de en *Nombre_proyecto*.cpp.|
|Dlgproxy.cpp, Dlgproxy.h|En un programa basado en cuadros de diálogo, la implementación y el archivo de encabezado para la clase de proxy de automatización del proyecto para el cuadro de diálogo principal. Solo se usa si ha seleccionado compatibilidad con Automation.|
|*Nombre_proyecto*doc.cpp, *Nombre_proyecto*doc.h|Derivan e implementan la clase de documento, denominada `CProjnameDoc`, e incluyen funciones miembro de esqueleto para inicializar un documento, serializarlo (guardar y cargar) e implementar la depuración y el diagnóstico.|
|*Nombre_proyecto*set.h/.cpp|Se crea si se crea un programa que admite una base de datos y contiene la clase de conjunto de registros.|
|*Nombre_proyecto*view.cpp, *Nombre_proyecto*view.h|Derivan e implementan la clase de vista, denominada `CProjnameView`, que se usa para mostrar e imprimir los datos del documento. La clase `CProjnameView` se deriva de una de las clases MFC siguientes:<br /><br />- [CEditView](../../mfc/reference/ceditview-class.md)<br />- [CFormView](../../mfc/reference/cformview-class.md)<br />- [CRecordView](../../mfc/reference/crecordview-class.md)<br />- [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)<br />- [CTreeView](../../mfc/reference/ctreeview-class.md)<br />- [CListView](../../mfc/reference/clistview-class.md)<br />- [CRichEditView](../../mfc/reference/cricheditview-class.md)<br />- [CScrollView](../../mfc/reference/cscrollview-class.md)<br />- [CView](../../mfc/reference/cview-class.md)<br />- [CHTMLView](../../mfc/reference/chtmlview-class.md)<br />- [CHTMLEditView](../../mfc/reference/chtmleditview-class.md)<br /><br /> La clase de vista del proyecto contiene funciones miembro de esqueleto para dibujar la vista e implementar la depuración y el diagnóstico. Si se ha habilitado la compatibilidad con la impresión, las entradas de mapa de mensajes se agregan para los mensajes de comando imprimir, configurar impresión y vista previa de impresión. Estas entradas llaman a las funciones miembro correspondientes en la clase de vista base.|
|*Nombre_proyecto*PropPage.h, *Nombre_proyecto*PropPage.cpp|Declaran e implementan la clase `CProjnamePropPage`. `CProjnamePropPage` se deriva de `COlePropertyPage` y se proporciona una función miembro de esqueleto, `DoDataExchange`, para implementar el intercambio y la validación de datos.|
|IPframe.cpp, IPframe.h|Se crea si se selecciona la opción Miniservidor o Servidor completo en la página **Opciones de Automation** del Asistente para aplicaciones (paso 3 de 6). Los archivos derivan e implementan la clase de ventana de marco en contexto, denominada **CInPlaceFrame**, que se usa cuando un programa contenedor activa el servidor en contexto.|
|Mainfrm.cpp, Mainfrm.h|Derivan la clase **CMainFrame** de [CFrameWnd](../../mfc/reference/cframewnd-class.md) (para las aplicaciones SDI) o [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md) (para las aplicaciones MDI). La clase **CMainFrame** controla la creación de botones de barra de herramientas y la barra de estado, si se seleccionan las opciones correspondientes en la página **Opciones de la aplicación** del Asistente para aplicaciones (paso 4 de 6). Para obtener información sobre el uso de **CMainFrame**, vea [Clases de ventana de marco creadas por el Asistente para aplicaciones](../../mfc/frame-window-classes-created-by-the-application-wizard.md).|
|Childfrm.cpp, Childfrm.h|Derivan la clase **CChildFrame** de [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md). La clase **CChildFrame** se usa para las ventanas de marco de documento de MDI. Estos archivos se crean siempre si se selecciona la opción MDI.|

## <a name="see-also"></a>Vea también

[Tipos de archivos creados para Visual C++ proyectos](file-types-created-for-visual-cpp-projects.md)<br>
[Archivos de encabezado y código fuente de controles o programas ATL](atl-program-or-control-source-and-header-files.md)<br>
[Proyectos de CLR](files-created-for-clr-projects.md)
