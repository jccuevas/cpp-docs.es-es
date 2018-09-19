---
title: 'Tutorial: Actualizar la aplicación Scribble MFC (parte 1) | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce50d2c70107b4c88f223e32fdd8cc083df38840
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685550"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Tutorial: Actualizar la aplicación Scribble MFC (parte 1)

Este tutorial muestra cómo modificar una aplicación MFC existente para utilizar la interfaz de usuario de la cinta de opciones. Visual Studio admite la cinta de Office 2007 y la cinta de Windows 7 Scenic. Para obtener más información acerca de la interfaz de usuario de cinta de opciones, consulte [cintas](/windows/desktop/uxguide/cmd-ribbons).

En este tutorial se ha modificado el ejemplo clásico de MFC Scribble 1.0 que permite utilizar el mouse para crear dibujos lineales. En esta parte del tutorial se muestra cómo modificar el ejemplo Scribble de modo que muestre una barra de cinta. [Parte 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) agregan más botones a la barra de cinta.

## <a name="prerequisites"></a>Requisitos previos

[Ejemplos de Visual C++](../visual-cpp-samples.md)

[Ejemplos de Visual C++](../visual-cpp-samples.md)

##  <a name="top"></a> Secciones

Esta parte del tutorial tiene las secciones siguientes:

- [Reemplazar las clases Base](#replaceclass)

- [Agregar mapas de bits al proyecto](#addbitmap)

- [Agregar un recurso de cinta al proyecto](#addribbon)

- [Crear una instancia de la barra de cinta](#createinstance)

- [Agregar una categoría de cinta de opciones](#addcategory)

- [Configurar la apariencia de la aplicación](#setlook)

##  <a name="replaceclass"></a> Reemplazar las clases Base

Para convertir una aplicación que admite un menú en una aplicación que admite una cinta, la aplicación, la ventana marco y las clases de barra de herramientas deben derivarse de clases base actualizadas. (Sugerimos no modificar el ejemplo original Scribble; en su lugar, limpie el proyecto Scribble, cópielo a otro directorio y, a continuación, modifique la copia).

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Para reemplazar las clases base de la aplicación Scribble

1. En scribble.cpp, compruebe que `CScribbleApp::InitInstance` incluye una llamada a [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

2. Agregue el siguiente código al archivo stdafx.h.

    ```cpp
    #include <afxcontrolbars.h>
    ```

3. En scribble.h, modifique la definición de la `CScribbleApp` para que se deriva de la clase [CWinAppEx (clase)](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

4. Scribble 1.0 se escribió cuando las aplicaciones Windows utilizaban un archivo de inicialización (.ini) para guardar los datos de preferencias del usuario. En lugar de usar un archivo de inicialización, modifique Scribble para almacenar las preferencias del usuario en el Registro. Para establecer la clave del Registro y la base, escriba el código siguiente en `CScribbleApp::InitInstance` después de la instrucción `LoadStdProfileSettings()`.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

5. El marco principal de una aplicación de interfaz de múltiples documentos (MDI) ya no se deriva de la clase `CMDIFrameWnd`. En su lugar, se deriva el [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) clase.

     En los archivos mainfrm.h y mainfrm.cpp, reemplace todas las referencias a `CMDIFrameWnd` por `CMDIFrameWndEx`.

6. En los archivos childfrm.h y childfrm.cpp, reemplace `CMDIChildWnd` por `CMDIChildWndEx`.

     En childfrm. archivo h, reemplace `CSplitterWnd` con `CSplitterWndEx`.

7. Modifique las barras de herramientas y las barras de estado para utilizar las nuevas clases MFC.

     En el archivo mainfrm.h:

    1. Reemplace `CToolBar` por `CMFCToolBar`.

    2. Reemplace `CStatusBar` por `CMFCStatusBar`.

8. En el archivo mainfrm.cpp:

    1. Reemplace `m_wndToolBar.SetBarStyle` por `m_wndToolBar.SetPaneStyle`.

    2. Reemplace `m_wndToolBar.GetBarStyle` por `m_wndToolBar.GetPaneStyle`.

    3. Reemplace `DockControlBar(&m_wndToolBar)` por `DockPane(&m_wndToolBar)`.

9. En el archivo ipframe.cpp, marque como comentario las tres líneas de código siguientes.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

10. Si piensa vincular la aplicación estáticamente, agregue el código siguiente al principio del archivo de recursos del proyecto (.rc).

    ```cpp
    #include "afxribbon.rc"
    ```

     El archivo afxribbon.rc contiene los recursos necesarios en tiempo de ejecución. El [MFC Application Wizard](../mfc/reference/mfc-application-wizard.md) incluye este archivo automáticamente cuando se crea una aplicación.

11. Guarde los cambios y, a continuación, compile y ejecute la aplicación.

[[Secciones](#top)]

##  <a name="addbitmap"></a> Agregar mapas de bits al proyecto

Los siguientes cuatro pasos de este tutorial requieren recursos de mapa de bits. Puede obtener los mapas de bits adecuados de varias maneras:

- Use la [editores de recursos](../windows/resource-editors.md) inventar sus propios mapas de bits. O bien, usar los editores de recursos para ensamblar mapas de bits de las imágenes de portable network graphics (PNG) que se incluyen con Visual Studio. Estas imágenes se encuentran en el `VS2008ImageLibrary` directory.

     Sin embargo, la interfaz de usuario de cinta requiere que ciertos mapas de bits admitan imágenes transparentes. Mapas de bits transparentes utilizan píxeles de 32 bits, donde 24 bits especifican los componentes rojos, verde y azules del color y 8 bits definen un *canal alfa* que especifica la transparencia del color. Los editores de recursos actuales pueden ver, pero no modificar los mapas de bits con píxeles de 32 bits. Por consiguiente, utilice un editor de imágenes externo en lugar de los editores de recursos para manipular los mapas de bits transparentes.

- Copie un archivo de recursos adecuado de otra aplicación al proyecto y, a continuación, importe los mapas de bits de ese archivo.

En este tutorial, los archivos de recursos se copian de una aplicación en el directorio de ejemplos.

### <a name="to-add-bitmaps-to-the-project"></a>Para agregar mapas de bits al proyecto

1. Utilice el Explorador de archivos para copiar los siguientes archivos .bmp del directorio recursos (`res`) del ejemplo RibbonGadgets:

   1. Copie main.bmp al proyecto Scribble.

   2. Copie filesmall.bmp y filelarge.bmp al proyecto Scribble.

   3. Haga nuevas copias de los archivos filelarge.bmp y filesmall.bmp, pero guarde las copias en el ejemplo RibbonGadgets. Cambie los nombres de las copias a homesmall.bmp y homelarge.bmp, y después mueva las copias al proyecto Scribble.

   4. Haga una copia del archivo toolbar.bmp, pero guarde la copia en el ejemplo RibbonGadgets. Cambie el nombre de la copia a panelicons.bmp y después mueva la copia al proyecto Scribble.

2. Importe el mapa de bits para una aplicación MFC. En **vista de recursos**, haga doble clic en el **scribble.rc** nodo, haga doble clic en el **mapa de bits** nodo y, a continuación, haga clic en **Agregar recurso**. En el cuadro de diálogo que aparece, haga clic en **importación**. Vaya a la `res` directorio, seleccione el archivo main.bmp y, a continuación, haga clic en **abierto**.

   El mapa de bits main.bmp contiene una imagen de 26x26. Cambie el identificador del mapa de bits a IDB_RIBBON_MAIN.

3. Importe los mapas de bits para el menú Archivo asociado al botón Aplicación.

   1. Importe el archivo filesmall.bmp, que contiene diez imágenes de 16x16 (16x160). Dado que se necesitan imágenes sólo ocho 16 x 16 (16 x 128), use el **vista de recursos** para cambiar el ancho del mapa de bits de 160 a 128. Cambie el identificador del mapa de bits a IDB_RIBBON_FILESMALL.

   2. Importe filelarge.bmp, que contiene ocho imágenes de 32x32 (32x256). Cambie el identificador del mapa de bits a IDB_RIBBON_FILELARGE.

4. Importe los mapas de bits de las categorías y los paneles de la cinta. Cada pestaña de la barra de cinta es una categoría y consta de una etiqueta de texto y una imagen opcional.

   1. Importe el mapa de bits homesmall.bmp, que contiene ocho imágenes de 16x16 para los mapas de bits de botón pequeño. Cambie el identificador del mapa de bits a IDB_RIBBON_HOMESMALL.

   2. Importe el mapa de bits homelarge.bmp, que contiene ocho imágenes de 32x32 para los mapas de bits de botón grande. Cambie el identificador del mapa de bits a IDB_RIBBON_HOMELARGE.

5. Importe los mapas de bits de los paneles de cinta con el cambio de tamaño. Estos mapas de bits, o iconos de panel, se utilizan después de una operación de cambio de tamaño si la cinta es demasiado pequeña para mostrar todo el panel.

   1. Importe el mapa de bits panelicons.bmp, que contiene ocho imágenes de 16x16. En el **propiedades** ventana de la **Editor de mapa de bits**, ajuste el ancho del mapa de bits a 64 (16 x 64). Cambie el identificador del mapa de bits a IDB_PANEL_ICONS.

[[Secciones](#top)]

##  <a name="addribbon"></a> Agregar un recurso de cinta al proyecto

Al convertir una aplicación que utiliza los menús de una aplicación que tiene una cinta, no es necesario quitar o deshabilitar los menús existentes. En su lugar, cree un recurso de cinta, agregue los botones de la cinta y, a continuación, asocie los nuevos botones con los elementos de menú existentes. Aunque los menús no estén visibles, los mensajes de la barra de cinta se enrutan a través de los menús. Además, los accesos directos de menú siguen funcionando.

Una cinta consta del botón Aplicación, que es el botón grande del lado superior izquierdo de la cinta, y una o varias pestañas de categoría. Cada pestaña de categoría contiene uno o varios paneles que actúan como contenedores para los botones y los controles de la cinta. En el procedimiento siguiente se muestra cómo crear un recurso de cinta y, después, personalizar el botón Aplicación.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Para agregar un recurso de cinta al proyecto

1. En el **proyecto** menú, haga clic en **Agregar recurso**.

2. En el **Agregar recurso** cuadro de diálogo, seleccione **cinta** y, a continuación, haga clic en **New**.

   Visual Studio crea un recurso de cinta y lo abre en la vista Diseño. El identificador de recurso de cinta es IDR_RIBBON1, que se muestra en **vista de recursos**. La cinta contiene una categoría y un panel.

3. Puede personalizar el botón Aplicación si modifica sus propiedades. Los identificadores de mensaje que se utilizan en este código ya están definidos en el menú para Scribble 1.0.

4. En la vista Diseño, haga clic en el botón Aplicación para mostrar sus propiedades. Cambie los valores de propiedad como sigue: **imagen** a `IDB_RIBBON_MAIN`, **Prompt** a `File`, **claves** a `f`, **Large Images** a `IDB_RIBBON_FILELARGE`, y **imágenes pequeñas** a `IDB_RIBBON_FILESMALL`.

5. Las modificaciones siguientes crean el menú que aparece cuando el usuario hace clic en el botón Aplicación. Haga clic en el botón de puntos suspensivos (**...** ) junto a **Main Items** para abrir el **Editor de elementos**.

   1. Haga clic en **agregar** para agregar un botón. Cambio **título** a `&New`, **ID** a `ID_FILE_NEW`, **imagen** a `0`, **imagen grande** a `0`.

   2. Haga clic en **agregar** para agregar un segundo botón. Cambio **título** a `&Save`, **ID** a `ID_FILE_SAVE`, **imagen** a `2`, y **imagen grande** a `2`.

   3. Haga clic en **agregar** para agregar un tercer botón. Cambio **título** a `Save &As`, **ID** a `ID_FILE_SAVE_AS`, **imagen** a `3`, y **imagen grande** a `3`.

   4. Haga clic en **agregar** para agregar un cuarto botón. Cambio **título** a `&Print`, **ID** a `ID_FILE_PRINT`, **imagen** a `4`, y **imagen grande** a `4`.

   5. Cambiar el **elemento** escriba a **separador** y, a continuación, haga clic en **agregar**.

   6. Cambiar el **elemento** escriba a **botón**. Haga clic en **agregar** para agregar un quinto botón. Cambio **título** a `&Close`, **ID** a `ID_FILE_CLOSE`, **imagen** a `5`, y **imagen grande** a `5`.

6. Las modificaciones siguientes crean un submenú del botón Imprimir que creó en el paso anterior.

   1. Haga clic en el **impresión** botón, cambie la **elemento** escriba a **etiqueta**y, a continuación, haga clic en **insertar**. Cambio **título** a `Preview and print the document`.

   2. Haga clic en el **impresión** botón, cambie la **elemento** escriba a **botón**y haga clic en **insertar**. Cambio **título** a `&Print`, **ID** a `ID_FILE_PRINT`, **imagen** a `4`, y **imagen grande** a `4`.

   3. Haga clic en el **impresión** botón y, a continuación, haga clic en **insertar** para agregar un botón. Cambio **título** a `&Quick Print`, **ID** a `ID_FILE_PRINT_DIRECT`, **imagen** a `7`, y **imagen grande** a `7`.

   4. Haga clic en el **impresión** botón y, a continuación, haga clic en **insertar** para agregar otro botón. Cambio **título** a `Print Pre&view`, **ID** a `ID_FILE_PRINT_PREVIEW`, **imagen** a `6`, y **imagen grande** a `6`.

   5. Ha modificado el **Main Items**. Haga clic en **cerrar** para salir del **Editor de elementos**.

7. La modificación siguiente crea un botón Salir que aparece en la parte inferior del menú del botón Aplicación.

   1. En el **propiedades** ventana, haga clic en el botón de puntos suspensivos (**...** ) junto a **botón** para abrir el **Editor de elementos**.

   2. Haga clic en **agregar** para agregar un botón. Cambio **título** a `E&xit`, **ID** a `ID_APP_EXIT`, **imagen** a `8`.

[[Secciones](#top)]

##  <a name="createinstance"></a> Crear una instancia de la barra de cinta

En los pasos siguientes se muestra cómo crear una instancia de la barra de cinta cuando se inicia la aplicación. Para agregar una barra de cinta a una aplicación, declare la barra de cinta en el archivo mainfrm.h. A continuación, en el archivo mainfrm.cpp, escriba código para cargar el recurso de cinta.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Para crear una instancia de la barra de cinta

1. En el archivo mainfrm.h, agregue un miembro de datos a la sección protegida de `CMainFrame`, la definición de clase del marco principal. Este miembro representa la barra de cinta.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. En el archivo mainfrm.cpp, agregue el código siguiente antes de la última instrucción `return` al final de la función `CMainFrame::OnCreate`. De esta forma se crea una instancia de la barra de cinta.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

[[Secciones](#top)]

##  <a name="addcategory"></a> Personalizar el recurso de cinta

Ahora que ha creado el botón Aplicación, puede agregar elementos a la cinta.

> [!NOTE]
> En este tutorial se utiliza el mismo icono de panel para todos los paneles. Sin embargo, puede utilizar otros índices de la lista de imágenes para mostrar otros iconos.

### <a name="to-add-a-home-category-and-edit-panel"></a>Para agregar una categoría Inicio y un panel Edición

1. El programa Scribble solo requiere una categoría. En la vista Diseño, haga clic en **categoría** para mostrar sus propiedades. Cambie los valores de propiedad como sigue: **título** a `&Home`, **Large Images** a `IDB_RIBBON_HOMELARGE`, **imágenes pequeñas** a `IDB_RIBBON_HOMESMALL`.

2. Cada categoría de la cinta está organizada en paneles con nombre. Cada panel contiene un conjunto de controles que realizan operaciones relacionadas. Esta categoría tiene un panel. Haga clic en **Panel**y, a continuación, cambie **título** a `Edit` y **Image Index** a `0`.

3. Para el **editar** del panel, agregue un botón que se encarga de borrar el contenido del documento. El identificador de mensaje para este botón se ha definido en el recurso de menú IDR_SCRIBBTYPE. Especificar `Clear All` como el texto del botón y el índice del mapa de bits que decora el botón. Abra el **cuadro de herramientas**y, a continuación, arrastre un **botón** a la **editar** panel. Haga clic en el botón y, a continuación, cambie **título** a `Clear All`, **ID** a `ID_EDIT_CLEAR_ALL`, **Image Index** a `0`, **Large Image Index**  a `0`.

4. Guarde los cambios y, a continuación, compile y ejecute la aplicación. La aplicación Scribble debería mostrarse y debe tener una barra de cinta en la parte superior de la ventana en lugar de una barra de menús. La barra de cinta debe tener una categoría, **inicio**, y **inicio** debe tener un panel, **editar**. Se deben asociados con los controladores de eventos existente, los botones de la cinta de opciones que agregó y **abierto**, **cerrar**, **guardar**, **impresión**, y **Borrar todo** botones deberían funcionar según lo previsto.

[[Secciones](#top)]

##  <a name="setlook"></a> Configurar la apariencia de la aplicación

Un *Administrador visual* es un objeto global que controla todos los dibujos de una aplicación. Dado que la aplicación original Scribble utiliza el estilo de la interfaz de usuario de Office 2000, la aplicación puede parecer antigua. Puede restablecer la aplicación para utilizar el administrador visual de Office 2007 de modo sea similar a una aplicación de Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Para establecer la apariencia de la aplicación

1. En la función `CMainFrame::OnCreate`, escriba el código siguiente para cambiar el administrador visual y el estilo predeterminados.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

2. Guarde los cambios y, a continuación, compile y ejecute la aplicación. La interfaz de usuario de la aplicación debe ser similar a la de Office 2007.

[[Secciones](#top)]

## <a name="next-steps"></a>Pasos siguientes

Ha modificado el ejemplo clásico Scribble de MFC 1.0 para utilizar el diseñador de la cinta de opciones. Ahora, vaya a [2ª](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)  
[Tutorial: actualizar la aplicación Scribble MFC (parte 2)] (.. / mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)  
