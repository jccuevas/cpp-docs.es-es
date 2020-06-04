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
ms.openlocfilehash: 18803d2222c80b80ac2b1fde75b442ea1e9a89bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360255"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Tutorial: Actualizar la aplicación Scribble de MFC (parte 1)

Este tutorial muestra cómo modificar una aplicación MFC existente para utilizar la interfaz de usuario de la cinta de opciones. Visual Studio admite la cinta de Office 2007 y la cinta de Windows 7 Scenic. Para obtener más información acerca de la interfaz de usuario de la cinta de opciones, vea [cintas de opciones](/windows/win32/uxguide/cmd-ribbons).

En este tutorial se ha modificado el ejemplo clásico de MFC Scribble 1.0 que permite utilizar el mouse para crear dibujos lineales. En esta parte del tutorial se muestra cómo modificar el ejemplo Scribble de modo que muestre una barra de cinta. [La Parte 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) añade más botones a la barra de la cinta de opciones.

## <a name="prerequisites"></a>Prerrequisitos

El [ejemplo MFC de Scribble 1.0](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Para obtener ayuda sobre cómo convertir a Visual Studio 2017 o posterior, vea [Guía de portabilidad: MFC Scribble](../porting/porting-guide-mfc-scribble.md).

## <a name="sections"></a><a name="top"></a>Secciones

Esta parte del tutorial tiene las secciones siguientes:

- [Reemplazar las clases base](#replaceclass)

- [Agregar mapas de bits al proyecto](#addbitmap)

- [Agregar un recurso de cinta al proyecto](#addribbon)

- [Crear una instancia de la barra de cinta](#createinstance)

- [Agregar una categoría de cinta](#addcategory)

- [Configurar la apariencia de la aplicación](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a>Sustitución de las clases de base

Para convertir una aplicación que admite un menú en una aplicación que admite una cinta, la aplicación, la ventana marco y las clases de barra de herramientas deben derivarse de clases base actualizadas. (Le sugerimos que no modifique la muestra original de Scribble. En su lugar, limpie el proyecto Scribble, cópielo en otro directorio y, a continuación, modifique la copia.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Para reemplazar las clases base de la aplicación Scribble

1. En scribble.cpp, `CScribbleApp::InitInstance` compruebe que incluye una llamada a [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Agregue el código siguiente al archivo *pch.h* (*stdafx.h* en Visual Studio 2017 y versiones anteriores):

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. En scribble.h, modifique la `CScribbleApp` definición de la clase para que se derive de [CWinAppEx (Clase).](../mfc/reference/cwinappex-class.md)

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Scribble 1.0 se escribió cuando las aplicaciones Windows utilizaban un archivo de inicialización (.ini) para guardar los datos de preferencias del usuario. En lugar de usar un archivo de inicialización, modifique Scribble para almacenar las preferencias del usuario en el Registro. Para establecer la clave del Registro y la base, escriba el código siguiente en `CScribbleApp::InitInstance` después de la instrucción `LoadStdProfileSettings()`.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. El marco principal de una aplicación de interfaz de múltiples documentos (MDI) ya no se deriva de la clase `CMDIFrameWnd`. En su lugar, se deriva de la [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) clase.

    En los archivos mainfrm.h y mainfrm.cpp, reemplace todas las referencias a `CMDIFrameWnd` por `CMDIFrameWndEx`.

1. En los archivos childfrm.h y childfrm.cpp, reemplace `CMDIChildWnd` por `CMDIChildWndEx`.

    En el niño. h archivo, `CSplitterWnd` `CSplitterWndEx`reemplace por .

1. Modifique las barras de herramientas y las barras de estado para utilizar las nuevas clases MFC.

    En el archivo mainfrm.h:

    1. Reemplace `CToolBar` por `CMFCToolBar`.

    1. Reemplace `CStatusBar` por `CMFCStatusBar`.

1. En el archivo mainfrm.cpp:

    1. Reemplazar `m_wndToolBar.SetBarStyle` con `m_wndToolBar.SetPaneStyle`

    1. Reemplazar `m_wndToolBar.GetBarStyle` con `m_wndToolBar.GetPaneStyle`

    1. Reemplazar `DockControlBar(&m_wndToolBar)` con `DockPane(&m_wndToolBar)`

1. En el archivo ipframe.cpp, marque como comentario las tres líneas de código siguientes.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación.

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a>Adición de mapas de bits al proyecto

Los siguientes cuatro pasos de este tutorial requieren recursos de mapa de bits. Puede obtener los mapas de bits adecuados de varias maneras:

- Utilice los [editores de](../windows/resource-editors.md) recursos para inventar sus propios mapas de bits. O bien, use los editores de recursos para ensamblar mapas de bits a partir de las imágenes de gráficos de red portátiles (.png) que se incluyen con Visual Studio y se pueden descargar desde la biblioteca de imágenes de [Visual Studio.](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library)

    Sin embargo, la interfaz de usuario de la **cinta** de opciones requiere que ciertos mapas de bits admitan imágenes transparentes. Los mapas de bits transparentes utilizan píxeles de 32 bits, donde 24 bits especifican los componentes rojo, verde y azul del color, y 8 bits definen un *canal alfa* que especifica la transparencia del color. Los editores de recursos actuales pueden ver, pero no modificar los mapas de bits con píxeles de 32 bits. Por consiguiente, utilice un editor de imágenes externo en lugar de los editores de recursos para manipular los mapas de bits transparentes.

- Copie un archivo de recursos adecuado de otra aplicación al proyecto y, a continuación, importe los mapas de bits de ese archivo.

Este tutorial copia los archivos de recursos del ejemplo creado en [Tutorial: Creación](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)de una aplicación de cinta de opciones mediante MFC .

### <a name="to-add-bitmaps-to-the-project"></a>Para agregar mapas de bits al proyecto

1. Utilice el Explorador de archivos para copiar los`res`siguientes archivos .bmp del`res`directorio resources ( ) del ejemplo de la cinta de opciones en el directorio de recursos ( ) del proyecto Scribble:

   1. Copie main.bmp al proyecto Scribble.

   1. Copie filesmall.bmp y filelarge.bmp al proyecto Scribble.

   1. Realice nuevas copias de los archivos filelarge.bmp y filesmall.bmp, pero guarde las copias en el ejemplo de la cinta de opciones. Cambie los nombres de las copias a homesmall.bmp y homelarge.bmp, y después mueva las copias al proyecto Scribble.

   1. Haga una copia del archivo toolbar.bmp, pero guarde la copia en el ejemplo de la cinta de opciones. Cambie el nombre de la copia a panelicons.bmp y después mueva la copia al proyecto Scribble.

1. Importe el mapa de bits para una aplicación MFC. En **la vista**de recursos , haga doble clic en el nodo **scribble.rc,** haga doble clic en el nodo Mapa de **bits** y, a continuación, haga clic en **Agregar recurso**. En el cuadro de diálogo que aparece, haga clic en **Importar**. Vaya al `res` directorio, seleccione el archivo main.bmp y, a continuación, haga clic en **Abrir**.

   El mapa de bits main.bmp contiene una imagen de 26x26. Cambie el ID del `IDB_RIBBON_MAIN`mapa de bits a .

1. Importe los mapas de bits para el menú de archivos que se adjunta al botón **Aplicación.**

   1. Importe el archivo filesmall.bmp, que contiene once imágenes de 16x16 (16x176). Cambie el ID del `IDB_RIBBON_FILESMALL`mapa de bits a .

   > [!NOTE]
   > Debido a que solo necesitamos las primeras ocho imágenes de 16x16 (16x128), puede recortar opcionalmente el ancho del lado derecho de este mapa de bits de 176 a 128.

   1. Importe el archivolarge.bmp, que contiene nueve imágenes de 32x32 (32x288). Cambie el ID del `IDB_RIBBON_FILELARGE`mapa de bits a .

1. Importe los mapas de bits de las categorías y los paneles de la cinta. Cada pestaña de la barra de cinta es una categoría y consta de una etiqueta de texto y una imagen opcional.

   1. Importe el mapa de bits homesmall.bmp, que contiene once imágenes de 16x16 para mapas de bits de botones pequeños. Cambie el ID del `IDB_RIBBON_HOMESMALL`mapa de bits a .

   1. Importe el mapa de bits homelarge.bmp, que contiene nueve imágenes de 32x32 para mapas de bits de botón grandes. Cambie el ID del `IDB_RIBBON_HOMELARGE`mapa de bits a .

1. Importe los mapas de bits de los paneles de cinta con el cambio de tamaño. Estos mapas de bits, o iconos de panel, se utilizan después de una operación de cambio de tamaño si la cinta es demasiado pequeña para mostrar todo el panel.

   1. Importe el mapa de bits panelicons.bmp, que contiene ocho imágenes de 16x16. En la ventana **Propiedades** del Editor de **mapas**de bits , ajuste el ancho del mapa de bits a 64 (16x64). Cambie el ID del `IDB_PANEL_ICONS`mapa de bits a .

   > [!NOTE]
   > Debido a que solo necesitamos las primeras cuatro imágenes de 16x16 (16x64), puede recortar opcionalmente el ancho del lado derecho de este mapa de bits de 128 a 64.

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a>Agregar un recurso de cinta de opciones al proyecto

Al convertir una aplicación que usa menús en una aplicación que usa una cinta de opciones, no es tiene que quitar ni deshabilitar los menús existentes. Simplemente cree un recurso de cinta de opciones, agregue botones de la cinta de opciones y, a continuación, asocie los nuevos botones con los elementos de menú existentes. Aunque los menús ya no están visibles, los mensajes de la barra de la cinta de opciones se enrutan a través de los menús y los accesos directos de menú siguen funcionando.

Una cinta de opciones consta del botón **Aplicación,** que es el botón grande en la parte superior izquierda de la cinta de opciones y una o varias fichas de categoría. Cada pestaña de categoría contiene uno o varios paneles que actúan como contenedores para los botones y los controles de la cinta. El siguiente procedimiento muestra cómo crear un recurso de cinta de opciones y, a continuación, personalizar el botón **Aplicación.**

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Para agregar un recurso de cinta al proyecto

1. Con el proyecto Scribble seleccionado en el **Explorador**de soluciones , en el menú **Proyecto** , haga clic en **Agregar recurso**.

1. En el cuadro de diálogo **Agregar recurso,** seleccione **Cinta de opciones** y, a continuación, haga clic en **Nuevo**.

   Visual Studio crea un recurso de cinta y lo abre en la vista Diseño. El identificador de `IDR_RIBBON1`recurso de la cinta de opciones es , que se muestra en **la vista de**recursos . La cinta contiene una categoría y un panel.

1. Puede personalizar el botón **Aplicación** modificando sus propiedades. Los identificadores de mensaje que se utilizan en este código ya están definidos en el menú para Scribble 1.0.

1. En la vista de diseño, haga clic en el botón **Aplicación** para mostrar sus propiedades. Cambie los valores de propiedad `IDB_RIBBON_MAIN`de la siguiente manera: `IDB_RIBBON_FILELARGE` **Imagen** a , **Preguntar** a `File`, **Claves** a `f`, **Imágenes grandes** a y **Imágenes pequeñas** a `IDB_RIBBON_FILESMALL`.

1. Las siguientes modificaciones crean el menú que aparece cuando el usuario hace clic en el botón **Aplicación.** Haga clic en los puntos suspensivos (**...**) situados junto a **Elementos principales** para abrir el **Editor de elementos**.

   1. Con el **botón** **Tipo** de elemento seleccionado, haga clic en **Agregar** para agregar un botón. Cambie **Caption** Subtítulo `&New`a `ID_FILE_NEW`, **ID** a , `0` **Imagen** a `0`, Imagen **grande** a .

   1. Haga clic en **Agregar** para agregar un botón. Cambie **Caption** Subtítulo `&Save`a `ID_FILE_SAVE`, **ID** a , `2` **Imagen** a `2`, e Imagen **grande** a .

   1. Haga clic en **Agregar** para agregar un botón. Cambie **Caption** Subtítulo `Save &As`a `ID_FILE_SAVE_AS`, **ID** a , `3` **Imagen** a `3`, e Imagen **grande** a .

   1. Haga clic en **Agregar** para agregar un botón. Cambie **Caption** Subtítulo `&Print`a `ID_FILE_PRINT`, **ID** a , `4` **Imagen** a `4`, e Imagen **grande** a .

   1. Cambie el tipo **de elemento** a **Separador** y, a continuación, haga clic en **Agregar**.

   1. Cambie el tipo **de elemento** a **Botón**. Haga clic en **Agregar** para agregar un quinto botón. Cambie **Caption** Subtítulo `&Close`a `ID_FILE_CLOSE`, **ID** a , `5` **Imagen** a `5`, e Imagen **grande** a .

1. Las siguientes modificaciones crean un submenú en el botón **Imprimir** que creó en el paso anterior.

   1. Haga clic en el botón **Imprimir,** cambie el Tipo **de elemento** a **Etiqueta**y, a continuación, haga clic en **Insertar**. Cambie **Caption** Subtítulo `Preview and print the document`a .

   1. Haga clic en el botón **Imprimir,** cambie el Tipo **de elemento** a **Botón**y haga clic en **Insertar**. Cambie **Caption** Subtítulo `&Print`a `ID_FILE_PRINT`, **ID** a , `4` **Imagen** a `4`, e Imagen **grande** a .

   1. Haga clic en el botón **Imprimir** y, a continuación, haga clic en **Insertar** para agregar un botón. Cambie **Caption** Subtítulo `&Quick Print`a `ID_FILE_PRINT_DIRECT`, **ID** a , `7` **Imagen** a `7`, e Imagen **grande** a .

   1. Haga clic en el botón **Imprimir** y, a continuación, haga clic en **Insertar** para agregar otro botón. Cambie **Caption** Subtítulo `Print Pre&view`a `ID_FILE_PRINT_PREVIEW`, **ID** a , `6` **Imagen** a `6`, e Imagen **grande** a .

   1. Ahora ha modificado los **elementos principales**. Haga clic en **Cerrar** para salir del **Editor de elementos**.

1. La siguiente modificación crea un botón de salida que aparece en la parte inferior del menú del botón **Aplicación.**

   1. Elija la pestaña **Vista** de recursos en el **Explorador de soluciones**.
   1. En la ventana **Propiedades,** haga clic en los puntos suspensivos (**...**) situados junto a **Botón** para abrir el **Editor de elementos**.

   1. Con el **botón** **Tipo** de elemento seleccionado, haga clic en **Agregar** para agregar un botón. Cambie **Caption** Subtítulo `E&xit`a `ID_APP_EXIT`, **ID** a , **Imagen** a `8`.

   1. Ha modificado los **botones**. Haga clic en **Cerrar** para salir del **Editor de elementos**.

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a>Creación de una instancia de la barra de cinta de opciones

En los pasos siguientes se muestra cómo crear una instancia de la barra de cinta cuando se inicia la aplicación. Para agregar una barra de cinta a una aplicación, declare la barra de cinta en el archivo mainfrm.h. A continuación, en el archivo mainfrm.cpp, escriba código para cargar el recurso de cinta.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Para crear una instancia de la barra de cinta

1. En el archivo mainfrm.h, agregue un miembro de datos a la sección protegida de `CMainFrame`, la definición de clase del marco principal. Este miembro es para la barra de la cinta de opciones.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. En el archivo mainfrm.cpp, agregue el código siguiente antes de la última instrucción `return` al final de la función `CMainFrame::OnCreate`. Crea una instancia de la barra de la cinta de opciones.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a>Personalización del recurso de la cinta de opciones

Ahora que ha creado el botón **Aplicación,** puede agregar elementos a la cinta de opciones.

> [!NOTE]
> En este tutorial se utiliza el mismo icono de panel para todos los paneles. Sin embargo, puede utilizar otros índices de la lista de imágenes para mostrar otros iconos.

### <a name="to-add-a-home-category-and-edit-panel"></a>Para agregar una categoría Inicio y un panel Edición

1. El programa Scribble solo requiere una categoría. En la vista de diseño, en el **cuadro de herramientas**, haga doble clic en **Categoría** para agregar una y mostrar sus propiedades. Cambie los valores de propiedad `&Home`de la `IDB_RIBBON_HOMELARGE`siguiente manera: **Subtítulo** a , **Imágenes grandes** a , **Imágenes pequeñas** a `IDB_RIBBON_HOMESMALL`.

1. Cada categoría de la cinta está organizada en paneles con nombre. Cada panel contiene un conjunto de controles que completan las operaciones relacionadas. Esta categoría tiene un panel. Haga clic en **Panel** `Edit`y, a continuación, cambie **Subtítulo** a .

1. En el panel **Editar,** agregue un botón responsable de borrar el contenido del documento. El identificador de mensaje para este `IDR_SCRIBBTYPE` botón ya se ha definido en el recurso de menú. Especifique `Clear All` como el texto del botón y el índice del mapa de bits que decora el botón. Abra el **cuadro de herramientas**y, a continuación, arrastre un **botón** al panel **Editar.** Haga clic en el `Clear All`botón y, a continuación, cambie **Subtítulo** a , **ID** `ID_EDIT_CLEAR_ALL`a , Índice de **imagen** a `0`, Índice de imagen **grande** a `0`.

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. La aplicación Scribble debería mostrarse y debe tener una barra de cinta en la parte superior de la ventana en lugar de una barra de menús. La barra de la cinta de opciones debe tener una categoría, **Inicio**y **Inicio** debe tener un panel, **Editar**. Los botones de la cinta de opciones que agregó deben estar asociados a los controladores de eventos existentes y los botones **Abrir**, **Cerrar**, **Guardar**, **Imprimir**y **Borrar todo** deben funcionar según lo previsto.

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a>Ajuste del aspecto de la aplicación

Un *administrador visual* es un objeto global que controla todo el dibujo de una aplicación. Dado que la aplicación original Scribble utiliza el estilo de la interfaz de usuario de Office 2000, la aplicación puede parecer antigua. Puede restablecer la aplicación para utilizar el administrador visual de Office 2007 de modo sea similar a una aplicación de Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Para establecer la apariencia de la aplicación

1. En `CMainFrame::OnCreate` la función, escriba `return 0;` el código siguiente antes de la instrucción para cambiar el administrador visual y el estilo predeterminados.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Guarde los cambios y, a continuación, compile y ejecute la aplicación. La interfaz de usuario de la aplicación debe ser similar a la de Office 2007.

## <a name="next-steps"></a>Pasos siguientes

Ha modificado el ejemplo clásico de MFC de Scribble 1.0 para usar el **Diseñador de cinta de opciones**. Ahora vaya a la [Parte 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Consulte también

[Tutoriales](../mfc/walkthroughs-mfc.md)<br/>
[Tutorial: Actualizar la aplicación Scribble de MFC (parte 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
