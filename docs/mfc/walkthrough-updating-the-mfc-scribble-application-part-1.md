---
title: 'Tutorial: Actualizar la aplicación Scribble MFC (parte 1)'
ms.date: 04/25/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: cba28039cb7755149b35a47ddee82b6274fe4c72
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558211"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Tutorial: Actualizar la aplicación Scribble MFC (parte 1)

Este tutorial muestra cómo modificar una aplicación MFC existente para utilizar la interfaz de usuario de la cinta de opciones. Visual Studio admite la cinta de Office 2007 y la cinta de Windows 7 Scenic. Para obtener más información acerca de la interfaz de usuario de cinta de opciones, consulte [cintas](/windows/desktop/uxguide/cmd-ribbons).

En este tutorial se ha modificado el ejemplo clásico de MFC Scribble 1.0 que permite utilizar el mouse para crear dibujos lineales. En esta parte del tutorial se muestra cómo modificar el ejemplo Scribble de modo que muestre una barra de cinta. [Parte 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) agregan más botones a la barra de cinta.

## <a name="prerequisites"></a>Requisitos previos

El [ejemplo Scribble de MFC 1.0](http://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Para obtener ayuda sobre la conversión de Visual Studio 2017 o posterior, consulte [Guía de migración: Scribble de MFC](../porting/porting-guide-mfc-scribble.md).

##  <a name="top"></a> Secciones

Esta parte del tutorial tiene las secciones siguientes:

- [Reemplazar las clases Base](#replaceclass)

- [Agregar mapas de bits al proyecto](#addbitmap)

- [Agregar un recurso de cinta al proyecto](#addribbon)

- [Crear una instancia de la barra de cinta](#createinstance)

- [Agregar una categoría de cinta de opciones](#addcategory)

- [Configurar la apariencia de la aplicación](#setlook)

##  <a name="replaceclass"></a> Reemplazar las clases Base

Para convertir una aplicación que admite un menú en una aplicación que admite una cinta, la aplicación, la ventana marco y las clases de barra de herramientas deben derivarse de clases base actualizadas. (Se recomienda que no modifique el ejemplo original Scribble. En su lugar, limpie el proyecto Scribble, cópielo en otro directorio y, a continuación, modifique la copia.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Para reemplazar las clases base de la aplicación Scribble

1. En scribble.cpp, compruebe que `CScribbleApp::InitInstance` incluye una llamada a [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Agregue el siguiente código al archivo stdafx.h.

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. En scribble.h, modifique la definición de la `CScribbleApp` para que se deriva de la clase [CWinAppEx (clase)](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Scribble 1.0 se escribió cuando las aplicaciones Windows utilizaban un archivo de inicialización (.ini) para guardar los datos de preferencias del usuario. En lugar de usar un archivo de inicialización, modifique Scribble para almacenar las preferencias del usuario en el Registro. Para establecer la clave del Registro y la base, escriba el código siguiente en `CScribbleApp::InitInstance` después de la instrucción `LoadStdProfileSettings()`.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. El marco principal de una aplicación de interfaz de múltiples documentos (MDI) ya no se deriva de la clase `CMDIFrameWnd`. En su lugar, se deriva el [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) clase.

    En los archivos mainfrm.h y mainfrm.cpp, reemplace todas las referencias a `CMDIFrameWnd` por `CMDIFrameWndEx`.

1. En los archivos childfrm.h y childfrm.cpp, reemplace `CMDIChildWnd` por `CMDIChildWndEx`.

    En childfrm. archivo h, reemplace `CSplitterWnd` con `CSplitterWndEx`.

1. Modifique las barras de herramientas y las barras de estado para utilizar las nuevas clases MFC.

    En el archivo mainfrm.h:

    1. Reemplace `CToolBar` por `CMFCToolBar`.

    1. Reemplace `CStatusBar` por `CMFCStatusBar`.

1. En el archivo mainfrm.cpp:

    1. Reemplace `m_wndToolBar.SetBarStyle` por `m_wndToolBar.SetPaneStyle`.

    1. Reemplace `m_wndToolBar.GetBarStyle` por `m_wndToolBar.GetPaneStyle`.

    1. Reemplace `DockControlBar(&m_wndToolBar)` por `DockPane(&m_wndToolBar)`.

1. En el archivo ipframe.cpp, marque como comentario las tres líneas de código siguientes.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación.

##  <a name="addbitmap"></a> Agregar mapas de bits al proyecto

Los siguientes cuatro pasos de este tutorial requieren recursos de mapa de bits. Puede obtener los mapas de bits adecuados de varias maneras:

- Use la [editores de recursos](../windows/resource-editors.md) inventar sus propios mapas de bits. O usar los editores de recursos para ensamblar mapas de bits de las imágenes de portable network graphics (PNG) que se incluyen con Visual Studio y pueden descargarse desde el [biblioteca de imágenes de Visual Studio](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library).

    Sin embargo, el **cinta** interfaz de usuario requiere que ciertos mapas de bits admitan imágenes transparentes. Mapas de bits transparentes utilizan píxeles de 32 bits, donde 24 bits especifican los componentes rojos, verde y azules del color y 8 bits definen un *canal alfa* que especifica la transparencia del color. Los editores de recursos actuales pueden ver, pero no modificar los mapas de bits con píxeles de 32 bits. Por consiguiente, utilice un editor de imágenes externo en lugar de los editores de recursos para manipular los mapas de bits transparentes.

- Copie un archivo de recursos adecuado de otra aplicación al proyecto y, a continuación, importe los mapas de bits de ese archivo.

En este tutorial copia los archivos de recursos en el ejemplo creado en [Tutorial: Crear una aplicación de cinta usando MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Para agregar mapas de bits al proyecto

1. Utilice el Explorador de archivos para copiar los siguientes archivos .bmp del directorio recursos (`res`) del ejemplo de cinta de opciones para el directorio de recursos (`res`) del proyecto Scribble:

   1. Copie main.bmp al proyecto Scribble.

   1. Copie filesmall.bmp y filelarge.bmp al proyecto Scribble.

   1. Haga nuevas copias de los archivos filelarge.bmp y filesmall.bmp, pero guardar las copias en el ejemplo de la cinta de opciones. Cambie los nombres de las copias a homesmall.bmp y homelarge.bmp, y después mueva las copias al proyecto Scribble.

   1. Realizar una copia del archivo toolbar.bmp, pero guardar la copia en el ejemplo de la cinta de opciones. Cambie el nombre de la copia a panelicons.bmp y después mueva la copia al proyecto Scribble.

1. Importe el mapa de bits para una aplicación MFC. En **vista de recursos**, haga doble clic en el **scribble.rc** nodo, haga doble clic en el **mapa de bits** nodo y, a continuación, haga clic en **Agregar recurso**. En el cuadro de diálogo que aparece, haga clic en **importación**. Vaya a la `res` directorio, seleccione el archivo main.bmp y, a continuación, haga clic en **abierto**.

   El mapa de bits main.bmp contiene una imagen de 26x26. Cambie el identificador del mapa de bits a `IDB_RIBBON_MAIN`.

1. Importe los mapas de bits para el menú archivo, que está asociado a la **aplicación** botón.

   1. Importe el archivo filesmall.bmp, que contiene 16 x 16 (16 x 176) once imágenes. Cambie el identificador del mapa de bits a `IDB_RIBBON_FILESMALL`.

   > [!NOTE]
   > Porque es necesario que las imágenes de ocho primeros 16 x 16 (16 x 128), si lo desea puede recortar el ancho de la derecha de este mapa de bits 176 128.

   1. Importe filelarge.bmp, que contiene los 32 x 32 (32 x 288) nueve imágenes. Cambie el identificador del mapa de bits a `IDB_RIBBON_FILELARGE`.

1. Importe los mapas de bits de las categorías y los paneles de la cinta. Cada pestaña de la barra de cinta es una categoría y consta de una etiqueta de texto y una imagen opcional.

   1. Importe el mapa de bits homesmall.bmp, que contiene once 16 x 16 imágenes de mapas de bits de botón pequeño. Cambie el identificador del mapa de bits a `IDB_RIBBON_HOMESMALL`.

   1. Importe el mapa de bits homelarge.bmp, que contiene nueve 32 x 32 imágenes de mapas de bits de botón grande. Cambie el identificador del mapa de bits a `IDB_RIBBON_HOMELARGE`.

1. Importe los mapas de bits de los paneles de cinta con el cambio de tamaño. Estos mapas de bits, o iconos de panel, se utilizan después de una operación de cambio de tamaño si la cinta es demasiado pequeña para mostrar todo el panel.

   1. Importe el mapa de bits panelicons.bmp, que contiene ocho imágenes de 16x16. En el **propiedades** ventana de la **Editor de mapa de bits**, ajuste el ancho del mapa de bits a 64 (16 x 64). Cambie el identificador del mapa de bits a `IDB_PANEL_ICONS`.

   > [!NOTE]
   > Porque es necesario que las imágenes de cuatro primeros 16 x 16 (16 x 64), si lo desea puede recortar el ancho de la derecha de este mapa de bits de 128 a 64.

##  <a name="addribbon"></a> Agregar un recurso de cinta al proyecto

Al convertir una aplicación que utiliza los menús de una aplicación que utiliza una cinta de opciones, no tienes que quitar o deshabilitar los menús existentes. Basta con crear un recurso de cinta, agregue botones de la cinta y, a continuación, asocie los nuevos botones con los elementos de menú existente. Aunque ya no están visibles los menús, los mensajes de la barra de cinta se enrutan a través de los menús y accesos directos del menú siguen funcionando.

Consta de una cinta de opciones de la **aplicación** botón, que es el botón grande en la parte superior izquierda de la cinta de opciones y uno o más pestañas de categorías. Cada pestaña de categoría contiene uno o varios paneles que actúan como contenedores para los botones y los controles de la cinta. El siguiente procedimiento muestra cómo crear un recurso de cinta y, a continuación, personalizar el **aplicación** botón.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Para agregar un recurso de cinta al proyecto

1. Con el proyecto Scribble seleccionado en **el Explorador de soluciones**, en el **proyecto** menú, haga clic en **Agregar recurso**.

1. En el **Agregar recurso** cuadro de diálogo, seleccione **cinta** y, a continuación, haga clic en **New**.

   Visual Studio crea un recurso de cinta y lo abre en la vista Diseño. Es el identificador de recurso de cinta de opciones `IDR_RIBBON1`, que se muestra en **vista de recursos**. La cinta contiene una categoría y un panel.

1. Puede personalizar el **aplicación** botón modificando sus propiedades. Los identificadores de mensaje que se utilizan en este código ya están definidos en el menú para Scribble 1.0.

1. En la vista Diseño, haga clic en el **aplicación** botón para mostrar sus propiedades. Cambie los valores de propiedad de la manera siguiente: **Imagen** a `IDB_RIBBON_MAIN`, **Prompt** a `File`, **claves** a `f`, **imágenes grandes** a `IDB_RIBBON_FILELARGE`y **Imágenes pequeñas** a `IDB_RIBBON_FILESMALL`.

1. Las modificaciones siguientes crean el menú que aparece cuando el usuario hace clic en el **aplicación** botón. Haga clic en el botón de puntos suspensivos (**...** ) junto a **Main Items** para abrir el **Editor de elementos**.

   1. Con el **elemento** tipo **botón** seleccionado, haga clic en **agregar** para agregar un botón. Cambio **título** a `&New`, **ID** a `ID_FILE_NEW`, **imagen** a `0`, **imagen grande** a `0`.

   1. Haga clic en **agregar** para agregar un botón. Cambio **título** a `&Save`, **ID** a `ID_FILE_SAVE`, **imagen** a `2`, y **imagen grande** a `2`.

   1. Haga clic en **agregar** para agregar un botón. Cambio **título** a `Save &As`, **ID** a `ID_FILE_SAVE_AS`, **imagen** a `3`, y **imagen grande** a `3`.

   1. Haga clic en **agregar** para agregar un botón. Cambio **título** a `&Print`, **ID** a `ID_FILE_PRINT`, **imagen** a `4`, y **imagen grande** a `4`.

   1. Cambiar el **elemento** escriba a **separador** y, a continuación, haga clic en **agregar**.

   1. Cambiar el **elemento** escriba a **botón**. Haga clic en **agregar** para agregar un quinto botón. Cambio **título** a `&Close`, **ID** a `ID_FILE_CLOSE`, **imagen** a `5`, y **imagen grande** a `5`.

1. Las modificaciones siguientes crean un submenú en el **impresión** botón que creó en el paso anterior.

   1. Haga clic en el **impresión** botón, cambie la **elemento** escriba a **etiqueta**y, a continuación, haga clic en **insertar**. Cambio **título** a `Preview and print the document`.

   1. Haga clic en el **impresión** botón, cambie la **elemento** escriba a **botón**y haga clic en **insertar**. Cambio **título** a `&Print`, **ID** a `ID_FILE_PRINT`, **imagen** a `4`, y **imagen grande** a `4`.

   1. Haga clic en el **impresión** botón y, a continuación, haga clic en **insertar** para agregar un botón. Cambio **título** a `&Quick Print`, **ID** a `ID_FILE_PRINT_DIRECT`, **imagen** a `7`, y **imagen grande** a `7`.

   1. Haga clic en el **impresión** botón y, a continuación, haga clic en **insertar** para agregar otro botón. Cambio **título** a `Print Pre&view`, **ID** a `ID_FILE_PRINT_PREVIEW`, **imagen** a `6`, y **imagen grande** a `6`.

   1. Ahora ha modificado el **Main Items**. Haga clic en **cerrar** para salir del **Editor de elementos**.

1. La modificación siguiente crea un botón Salir que aparece en la parte inferior de la **aplicación** menú del botón.

   1. En el **propiedades** ventana, haga clic en el botón de puntos suspensivos (**...** ) junto a **botón** para abrir el **Editor de elementos**.

   1. Con el **elemento** tipo **botón** seleccionado, haga clic en **agregar** para agregar un botón. Cambio **título** a `E&xit`, **ID** a `ID_APP_EXIT`, **imagen** a `8`.

   1. Ha modificado el **botones**. Haga clic en **cerrar** para salir del **Editor de elementos**.

##  <a name="createinstance"></a> Crear una instancia de la barra de cinta

En los pasos siguientes se muestra cómo crear una instancia de la barra de cinta cuando se inicia la aplicación. Para agregar una barra de cinta a una aplicación, declare la barra de cinta en el archivo mainfrm.h. A continuación, en el archivo mainfrm.cpp, escriba código para cargar el recurso de cinta.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Para crear una instancia de la barra de cinta

1. En el archivo mainfrm.h, agregue un miembro de datos a la sección protegida de `CMainFrame`, la definición de clase del marco principal. Este miembro es de la barra de cinta de opciones.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. En el archivo mainfrm.cpp, agregue el código siguiente antes de la última instrucción `return` al final de la función `CMainFrame::OnCreate`. Crea una instancia de la barra de cinta.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

##  <a name="addcategory"></a> Personalizar el recurso de cinta

Ahora que ha creado el **aplicación** botón, puede agregar elementos a la cinta de opciones.

> [!NOTE]
> En este tutorial se utiliza el mismo icono de panel para todos los paneles. Sin embargo, puede utilizar otros índices de la lista de imágenes para mostrar otros iconos.

### <a name="to-add-a-home-category-and-edit-panel"></a>Para agregar una categoría Inicio y un panel Edición

1. El programa Scribble solo requiere una categoría. En la vista Diseño, en el **cuadro de herramientas**, haga doble clic en **categoría** para agregar uno y mostrar sus propiedades. Cambie los valores de propiedad de la manera siguiente: **Título** a `&Home`, **imágenes grandes** a `IDB_RIBBON_HOMELARGE`, **imágenes pequeñas** a `IDB_RIBBON_HOMESMALL`.

1. Cada categoría de la cinta está organizada en paneles con nombre. Cada panel contiene un conjunto de controles que completar operaciones relacionadas. Esta categoría tiene un panel. Haga clic en **Panel**y, a continuación, cambie **título** a `Edit`.

1. Para el **editar** del panel, agregue un botón responsable de borrar el contenido del documento. El identificador del mensaje para este botón ya se ha definido en el `IDR_SCRIBBTYPE` recurso de menú. Especificar `Clear All` como el texto del botón y el índice del mapa de bits que decora el botón. Abra el **cuadro de herramientas**y, a continuación, arrastre un **botón** a la **editar** panel. Haga clic en el botón y, a continuación, cambie **título** a `Clear All`, **ID** a `ID_EDIT_CLEAR_ALL`, **Image Index** a `0`, **Large Image Index**  a `0`.

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. La aplicación Scribble debería mostrarse y debe tener una barra de cinta en la parte superior de la ventana en lugar de una barra de menús. La barra de cinta debe tener una categoría, **inicio**, y **inicio** debe tener un panel, **editar**. Se deben asociados con los controladores de eventos existente, los botones de la cinta de opciones que agregó y **abierto**, **cerrar**, **guardar**, **impresión**, y **Borrar todo** botones deberían funcionar según lo previsto.

##  <a name="setlook"></a> Configurar la apariencia de la aplicación

Un *Administrador visual* es un objeto global que controla todos los dibujos de una aplicación. Dado que la aplicación original Scribble utiliza el estilo de la interfaz de usuario de Office 2000, la aplicación puede parecer antigua. Puede restablecer la aplicación para utilizar el administrador visual de Office 2007 de modo sea similar a una aplicación de Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Para establecer la apariencia de la aplicación

1. En el `CMainFrame::OnCreate` de función, escriba el código siguiente antes de la `return 0;` instrucción para cambiar el administrador visual predeterminado y el estilo.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. La interfaz de usuario de la aplicación debe ser similar a la de Office 2007.

## <a name="next-steps"></a>Pasos siguientes

Ha modificado el clásico ejemplo de Scribble de MFC 1.0 para usar el **Ribbon Designer**. Ahora, vaya a [2ª](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)<br/>
[Tutorial: actualizar la aplicación Scribble de MFC (Parte 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
