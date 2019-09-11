---
title: 'Tutorial: Actualizar la aplicación Scribble de MFC (parte 1)'
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 23ddf92514674c32e28c259c4c7aa8f742302485
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907417"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Tutorial: Actualizar la aplicación Scribble de MFC (parte 1)

Este tutorial muestra cómo modificar una aplicación MFC existente para utilizar la interfaz de usuario de la cinta de opciones. Visual Studio admite la cinta de Office 2007 y la cinta de Windows 7 Scenic. Para obtener más información acerca de la interfaz de usuario de la cinta, consulte [ribbons](/windows/win32/uxguide/cmd-ribbons).

En este tutorial se ha modificado el ejemplo clásico de MFC Scribble 1.0 que permite utilizar el mouse para crear dibujos lineales. En esta parte del tutorial se muestra cómo modificar el ejemplo Scribble de modo que muestre una barra de cinta. La [parte 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) agrega más botones a la barra de cinta.

## <a name="prerequisites"></a>Requisitos previos

El [ejemplo Scribble 1,0 MFC](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Para obtener ayuda sobre cómo convertir a Visual Studio 2017 o una [versión posterior, consulte Guía de migración: Scribble](../porting/porting-guide-mfc-scribble.md)de MFC.

##  <a name="top"></a> Secciones

Esta parte del tutorial tiene las secciones siguientes:

- [Reemplazar las clases base](#replaceclass)

- [Agregar mapas de bits al proyecto](#addbitmap)

- [Agregar un recurso de cinta de opciones al proyecto](#addribbon)

- [Crear una instancia de la barra de cinta](#createinstance)

- [Agregar una categoría de cinta de opciones](#addcategory)

- [Establecer la apariencia de la aplicación](#setlook)

##  <a name="replaceclass"></a>Reemplazar las clases base

Para convertir una aplicación que admite un menú en una aplicación que admite una cinta, la aplicación, la ventana marco y las clases de barra de herramientas deben derivarse de clases base actualizadas. (Se recomienda no modificar el ejemplo de Scribble original. En su lugar, limpie el proyecto Scribble, cópielo en otro directorio y modifique la copia).

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Para reemplazar las clases base de la aplicación Scribble

1. En Scribble. cpp, compruebe que `CScribbleApp::InitInstance` incluye una llamada a [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Agregue el código siguiente al archivo *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores):

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. En Scribble. h, modifique la definición de la `CScribbleApp` clase para que se derive de la [clase CWinAppEx](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Scribble 1.0 se escribió cuando las aplicaciones Windows utilizaban un archivo de inicialización (.ini) para guardar los datos de preferencias del usuario. En lugar de usar un archivo de inicialización, modifique Scribble para almacenar las preferencias del usuario en el Registro. Para establecer la clave del Registro y la base, escriba el código siguiente en `CScribbleApp::InitInstance` después de la instrucción `LoadStdProfileSettings()`.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. El marco principal de una aplicación de interfaz de múltiples documentos (MDI) ya no se deriva de la clase `CMDIFrameWnd`. En su lugar, se deriva de la clase [cmdiframewndex (](../mfc/reference/cmdiframewndex-class.md) .

    En los archivos mainfrm.h y mainfrm.cpp, reemplace todas las referencias a `CMDIFrameWnd` por `CMDIFrameWndEx`.

1. En los archivos childfrm.h y childfrm.cpp, reemplace `CMDIChildWnd` por `CMDIChildWndEx`.

    En childfrm. h, reemplace `CSplitterWnd` por `CSplitterWndEx`.

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

##  <a name="addbitmap"></a>Agregar mapas de bits al proyecto

Los siguientes cuatro pasos de este tutorial requieren recursos de mapa de bits. Puede obtener los mapas de bits adecuados de varias maneras:

- Use los [editores de recursos](../windows/resource-editors.md) para inventar sus propios mapas de bits. También puede usar los editores de recursos para ensamblar mapas de bits de las imágenes Portable Network Graphics (. png) que se incluyen con Visual Studio y que se pueden descargar desde la [biblioteca de imágenes de Visual Studio](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library).

    Sin embargo, la interfaz de usuario de la **cinta** de opciones requiere que determinados mapas de bits admitan imágenes transparentes. Los mapas de bits transparentes usan píxeles de 32 bits, donde 24 bits especifican los componentes rojo, verde y azul del color, y 8 bits definen un *canal alfa* que especifica la transparencia del color. Los editores de recursos actuales pueden ver, pero no modificar los mapas de bits con píxeles de 32 bits. Por consiguiente, utilice un editor de imágenes externo en lugar de los editores de recursos para manipular los mapas de bits transparentes.

- Copie un archivo de recursos adecuado de otra aplicación al proyecto y, a continuación, importe los mapas de bits de ese archivo.

En este tutorial se copian los archivos de recursos [del ejemplo creado en el tutorial: Crear una aplicación de cinta mediante MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Para agregar mapas de bits al proyecto

1. Use el explorador de archivos para copiar los siguientes archivos. bmp del directorio de`res`recursos () del ejemplo de la cinta de opciones`res`en el directorio de recursos () del proyecto Scribble:

   1. Copie main.bmp al proyecto Scribble.

   1. Copie filesmall.bmp y filelarge.bmp al proyecto Scribble.

   1. Realice nuevas copias de los archivos filelarge. bmp y filesmall. bmp, pero guarde las copias en el ejemplo de la cinta de opciones. Cambie los nombres de las copias a homesmall.bmp y homelarge.bmp, y después mueva las copias al proyecto Scribble.

   1. Realice una copia del archivo Toolbar. bmp, pero guarde la copia en el ejemplo de la cinta de opciones. Cambie el nombre de la copia a panelicons.bmp y después mueva la copia al proyecto Scribble.

1. Importe el mapa de bits para una aplicación MFC. En **vista de recursos**, haga doble clic en el nodo **Scribble. RC** , haga doble clic en el nodo **mapa de bits** y, a continuación, haga clic en **Agregar recurso**. En el cuadro de diálogo que aparece, haga clic en **importar**. Busque el `res` directorio, seleccione el archivo main. bmp y, a continuación, haga clic en **abrir**.

   El mapa de bits main.bmp contiene una imagen de 26x26. Cambie el identificador del mapa de bits `IDB_RIBBON_MAIN`a.

1. Importe los mapas de bits para el menú archivo que está asociado al botón **aplicación** .

   1. Importe el archivo filesmall. bmp, que contiene once imágenes de 16x16 (16x176). Cambie el identificador del mapa de bits `IDB_RIBBON_FILESMALL`a.

   > [!NOTE]
   > Dado que solo necesitamos las ocho primeras imágenes de 16x16 (16x128), puede recortar opcionalmente el ancho del lado derecho de este mapa de bits de 176 a 128.

   1. Importe filelarge. bmp, que contiene nueve imágenes de 32x32 (32x288). Cambie el identificador del mapa de bits `IDB_RIBBON_FILELARGE`a.

1. Importe los mapas de bits de las categorías y los paneles de la cinta. Cada pestaña de la barra de cinta es una categoría y consta de una etiqueta de texto y una imagen opcional.

   1. Importe el mapa de bits homesmall. bmp, que contiene once imágenes 16x16 para los mapas de bits de botón pequeño. Cambie el identificador del mapa de bits `IDB_RIBBON_HOMESMALL`a.

   1. Importe el mapa de bits homelarge. bmp, que contiene nueve imágenes 32x32 para los mapas de bits de botones grandes. Cambie el identificador del mapa de bits `IDB_RIBBON_HOMELARGE`a.

1. Importe los mapas de bits de los paneles de cinta con el cambio de tamaño. Estos mapas de bits, o iconos de panel, se utilizan después de una operación de cambio de tamaño si la cinta es demasiado pequeña para mostrar todo el panel.

   1. Importe el mapa de bits panelicons.bmp, que contiene ocho imágenes de 16x16. En la ventana **propiedades** del **Editor de mapas de bits**, ajuste el ancho del mapa de bits a 64 (16x64). Cambie el identificador del mapa de bits `IDB_PANEL_ICONS`a.

   > [!NOTE]
   > Dado que solo necesitamos las cuatro primeras imágenes de 16x16 (16x64), puede recortar opcionalmente el ancho del lado derecho de este mapa de bits de 128 a 64.

##  <a name="addribbon"></a>Agregar un recurso de cinta de opciones al proyecto

Cuando se convierte una aplicación que utiliza menús en una aplicación que usa una cinta de opciones, no es necesario quitar o deshabilitar los menús existentes. Solo tiene que crear un recurso de cinta, agregar botones de la cinta de opciones y, a continuación, asociar los nuevos botones a los elementos de menú existentes. Aunque los menús ya no están visibles, los mensajes de la barra de cinta se enrutan a través de los menús y los métodos abreviados de menú continúan funcionando.

Una cinta de opciones se compone del botón **aplicación** , que es el botón grande del lado superior izquierdo de la cinta de opciones y una o varias pestañas de categorías. Cada pestaña de categoría contiene uno o varios paneles que actúan como contenedores para los botones y los controles de la cinta. En el siguiente procedimiento se muestra cómo crear un recurso de cinta de opciones y, a continuación, personalizar el botón **aplicación** .

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Para agregar un recurso de cinta al proyecto

1. Con el proyecto Scribble seleccionado en **Explorador de soluciones**, en el menú **proyecto** , haga clic en **Agregar recurso**.

1. En el cuadro de diálogo **Agregar recurso** , seleccione **cinta** de opciones y, a continuación, haga clic en **nuevo**.

   Visual Studio crea un recurso de cinta y lo abre en la vista Diseño. El identificador de recurso de `IDR_RIBBON1`la cinta de opciones es, que se muestra en **vista de recursos**. La cinta contiene una categoría y un panel.

1. Puede personalizar el botón **aplicación** modificando sus propiedades. Los identificadores de mensaje que se utilizan en este código ya están definidos en el menú para Scribble 1.0.

1. En la vista de diseño, haga clic en el botón **aplicación** para mostrar sus propiedades. Cambie los valores de propiedad de la siguiente manera: **Image** to `IDB_RIBBON_MAIN`, **prompt** `IDB_RIBBON_FILESMALL` `f` `IDB_RIBBON_FILELARGE` to, Keys to, Large Images to y Small Images to. `File`

1. Las modificaciones siguientes crean el menú que aparece cuando el usuario hace clic en el botón **aplicación** . Haga clic en los puntos suspensivos ( **...** ) junto a **elementos principales** para abrir el **Editor de elementos**.

   1. Con el **botón** tipo de **elemento** seleccionado, haga clic en **Agregar** para agregar un botón. Cambie **Caption** a `&New`, **ID** to `ID_FILE_NEW`, **Image** to `0`, **Image Large** a `0`.

   1. Haga clic en **Agregar** para agregar un botón. Cambie **Caption** a `&Save`, **ID** to `ID_FILE_SAVE`, **Image** to `2`e **Image Large** to `2`.

   1. Haga clic en **Agregar** para agregar un botón. Cambie **Caption** a `Save &As`, **ID** to `ID_FILE_SAVE_AS`, **Image** to `3`e **Image Large** to `3`.

   1. Haga clic en **Agregar** para agregar un botón. Cambie **Caption** a `&Print`, **ID** to `ID_FILE_PRINT`, **Image** to `4`e **Image Large** to `4`.

   1. Cambie el tipo de **elemento** a **separador** y, a continuación, haga clic en **Agregar**.

   1. Cambie el tipo de **elemento** a **botón**. Haga clic en **Agregar** para agregar un quinto botón. Cambie **Caption** a `&Close`, **ID** to `ID_FILE_CLOSE`, **Image** to `5`e **Image Large** to `5`.

1. Las modificaciones siguientes crean un submenú debajo del botón **Imprimir** que creó en el paso anterior.

   1. Haga clic en el botón **Imprimir** , cambie el tipo de **elemento** a **etiqueta**y, a continuación, haga clic en **Insertar**. Cambie **Caption** a `Preview and print the document`.

   1. Haga clic en el botón **Imprimir** , cambie el tipo **de** **elemento** a y haga clic en **Insertar**. Cambie **Caption** a `&Print`, **ID** to `ID_FILE_PRINT`, **Image** to `4`e **Image Large** to `4`.

   1. Haga clic en el botón **Imprimir** y, a continuación, haga clic en **Insertar** para agregar un botón. Cambie **Caption** a `&Quick Print`, **ID** to `ID_FILE_PRINT_DIRECT`, **Image** to `7`e **Image Large** to `7`.

   1. Haga clic en el botón **Imprimir** y, a continuación, haga clic en **Insertar** para agregar otro botón. Cambie **Caption** a `Print Pre&view`, **ID** to `ID_FILE_PRINT_PREVIEW`, **Image** to `6`e **Image Large** to `6`.

   1. Ya ha modificado los **elementos principales**. Haga clic en **cerrar** para salir del **Editor de elementos**.

1. La siguiente modificación crea un botón salir que aparece en la parte inferior del menú del botón de la **aplicación** .

   1. Elija la pestaña **vista de recursos** en **Explorador de soluciones**.
   1. En la ventana **propiedades** , haga clic en los puntos suspensivos ( **...** ) junto a **botón** para abrir el **Editor de elementos**.

   1. Con el **botón** tipo de **elemento** seleccionado, haga clic en **Agregar** para agregar un botón. Cambie **Caption** a `E&xit`, **ID** to `ID_APP_EXIT`, **Image** to `8`.

   1. Ha modificado los **botones**. Haga clic en **cerrar** para salir del **Editor de elementos**.

##  <a name="createinstance"></a>Crear una instancia de la barra de cinta

En los pasos siguientes se muestra cómo crear una instancia de la barra de cinta cuando se inicia la aplicación. Para agregar una barra de cinta a una aplicación, declare la barra de cinta en el archivo mainfrm.h. A continuación, en el archivo mainfrm.cpp, escriba código para cargar el recurso de cinta.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Para crear una instancia de la barra de cinta

1. En el archivo mainfrm.h, agregue un miembro de datos a la sección protegida de `CMainFrame`, la definición de clase del marco principal. Este miembro es para la barra de cinta.

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

##  <a name="addcategory"></a>Personalizar el recurso de la cinta de opciones

Ahora que ha creado el botón **aplicación** , puede agregar elementos a la cinta de opciones.

> [!NOTE]
> En este tutorial se utiliza el mismo icono de panel para todos los paneles. Sin embargo, puede utilizar otros índices de la lista de imágenes para mostrar otros iconos.

### <a name="to-add-a-home-category-and-edit-panel"></a>Para agregar una categoría Inicio y un panel Edición

1. El programa Scribble solo requiere una categoría. En la vista Diseño, en el **cuadro de herramientas**, haga doble clic en **categoría** para agregar una y mostrar sus propiedades. Cambie los valores de propiedad de la siguiente manera: **Leyenda a** `IDB_RIBBON_HOMESMALL` **, imágenes grandes** a , imágenes pequeñas en `IDB_RIBBON_HOMELARGE` `&Home`.

1. Cada categoría de la cinta está organizada en paneles con nombre. Cada panel contiene un conjunto de controles que realizan operaciones relacionadas. Esta categoría tiene un panel. Haga clic en **Panel**y, a continuación `Edit`, cambie **leyenda** a.

1. En el panel de **edición** , agregue un botón responsable de borrar el contenido del documento. El ID. de mensaje de este botón ya se ha definido `IDR_SCRIBBTYPE` en el recurso de menú. Especifique `Clear All` como el texto del botón y el índice del mapa de bits que decora el botón. Abra el **cuadro de herramientas**y arrastre un **botón** hasta el panel de **edición** . Haga clic en el botón y, a `Clear All`continuación, cambie `ID_EDIT_CLEAR_ALL`el **título** a, `0` **ID** a, **Índice** de `0`imagen a, **Índice de imagen grande** a.

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. La aplicación Scribble debería mostrarse y debe tener una barra de cinta en la parte superior de la ventana en lugar de una barra de menús. La barra de cinta debe tener una categoría, **Inicio**y **Inicio** debe tener un panel, **Editar**. Los botones de la cinta de opciones que agregó deben estar asociados a los controladores de eventos existentes y los botones **abrir**, **cerrar**, **Guardar**, **Imprimir**y **Borrar todo** deberían funcionar según lo previsto.

##  <a name="setlook"></a>Establecer la apariencia de la aplicación

Un *Administrador visual* es un objeto global que controla todo el dibujo de una aplicación. Dado que la aplicación original Scribble utiliza el estilo de la interfaz de usuario de Office 2000, la aplicación puede parecer antigua. Puede restablecer la aplicación para utilizar el administrador visual de Office 2007 de modo sea similar a una aplicación de Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Para establecer la apariencia de la aplicación

1. En la `CMainFrame::OnCreate` función, escriba el código siguiente antes de `return 0;` la instrucción para cambiar el estilo y el administrador visual predeterminados.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. La interfaz de usuario de la aplicación debe ser similar a la de Office 2007.

## <a name="next-steps"></a>Pasos siguientes

Ha modificado el ejemplo clásico de MFC Scribble 1,0 para usar el **Diseñador**de la cinta de opciones. Ahora, vaya a la [parte 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)<br/>
[Tutorial: actualizar la aplicación Scribble de MFC (Parte 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
