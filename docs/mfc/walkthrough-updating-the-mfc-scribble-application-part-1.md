---
title: "Tutorial: Actualizar la aplicaci&#243;n Scribble de MFC (Parte 1) | Microsoft Docs"
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
  - "ejemplos [C++], actualizar aplicaciones existentes"
  - "MFC Feature Pack, actualizar aplicaciones existentes"
  - "Office Fluent UI, trasladar"
  - "interfaz de usuario de la cinta, trasladar"
  - "ejemplos [C++], actualizar aplicaciones existentes"
  - "tutoriales [C++], actualizar aplicaciones existentes"
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
caps.latest.revision: 54
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 50
---
# Tutorial: Actualizar la aplicaci&#243;n Scribble de MFC (Parte 1)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tutorial muestra cómo modificar una aplicación MFC existente para utilizar la interfaz de usuario de la cinta de opciones.  Visual Studio admite la cinta de Office 2007 y la cinta de Windows 7 Scenic.  Para obtener más información sobre la interfaz de usuario de la cinta, vea [Cintas](http://go.microsoft.com/fwlink/?LinkId=129233) en el sitio web de MSDN.  
  
 En este tutorial se ha modificado el ejemplo clásico de MFC Scribble 1.0 que permite utilizar el mouse para crear dibujos lineales.  En esta parte del tutorial se muestra cómo modificar el ejemplo Scribble de modo que muestre una barra de cinta.  En la [parte 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) se agregan más botones a la barra de cinta.  
  
## Requisitos previos  
 [Ejemplos de Visual C\+\+](../top/visual-cpp-samples.md)  
  
 [Ejemplos de Visual C\+\+](../top/visual-cpp-samples.md)  
  
##  <a name="top"></a> Secciones  
 Esta parte del tutorial tiene las secciones siguientes:  
  
-   [Reemplazar las clases base](#replaceClass)  
  
-   [Agregar mapas de bits al proyecto](#addBitmap)  
  
-   [Agregar un recurso de cinta al proyecto](#addRibbon)  
  
-   [Crear una instancia de la barra de cinta](#createInstance)  
  
-   [Agregar una categoría de cinta](#addCategory)  
  
-   [Configurar la apariencia de la aplicación](#setLook)  
  
##  <a name="replaceClass"></a> Reemplazar las clases base  
 Para convertir una aplicación que admite un menú en una aplicación que admite una cinta, la aplicación, la ventana marco y las clases de barra de herramientas deben derivarse de clases base actualizadas. \(Sugerimos no modificar el ejemplo original Scribble; en su lugar, limpie el proyecto Scribble, cópielo a otro directorio y, a continuación, modifique la copia\).  
  
#### Para reemplazar las clases base de la aplicación Scribble  
  
1.  En scribble.cpp, compruebe que `CScribbleApp::InitInstance` incluya una llamada a [AfxOleInit](../Topic/AfxOleInit.md).  
  
2.  Agregue el siguiente código al archivo stdafx.h.  
  
    ```  
    #include <afxcontrolbars.h>  
    ```  
  
3.  En scribble.h, modifique la definición de la clase `CScribbleApp` para derivarla de [CWinAppEx Class](../mfc/reference/cwinappex-class.md).  
  
    ```  
    class CScribbleApp: public CWinAppEx  
    ```  
  
4.  Scribble 1.0 se escribió cuando las aplicaciones Windows utilizaban un archivo de inicialización \(.ini\) para guardar los datos de preferencias del usuario.  En lugar de usar un archivo de inicialización, modifique Scribble para almacenar las preferencias del usuario en el Registro.  Para establecer la clave del Registro y la base, escriba el código siguiente en `CScribbleApp::InitInstance` después de la instrucción `LoadStdProfileSettings()`.  
  
    ```  
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));  
    SetRegistryBase(_T("Settings"));  
    ```  
  
5.  El marco principal de una aplicación de interfaz de múltiples documentos \(MDI\) ya no se deriva de la clase `CMDIFrameWnd`.  En su lugar, se deriva de la clase [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md).  
  
     En los archivos mainfrm.h y mainfrm.cpp, reemplace todas las referencias a `CMDIFrameWnd` por `CMDIFrameWndEx`.  
  
6.  En los archivos childfrm.h y childfrm.cpp, reemplace `CMDIChildWnd` por `CMDIChildWndEx`.  
  
     En el archivo childfrm.h, reemplace `CSplitterWnd` por `CSplitterWndEx`.  
  
7.  Modifique las barras de herramientas y las barras de estado para utilizar las nuevas clases MFC.  
  
     En el archivo mainfrm.h:  
  
    1.  Reemplace `CToolBar` por `CMFCToolBar`.  
  
    2.  Reemplace `CStatusBar` por `CMFCStatusBar`.  
  
8.  En el archivo mainfrm.cpp:  
  
    1.  Reemplace `m_wndToolBar.SetBarStyle` por `m_wndToolBar.SetPaneStyle`.  
  
    2.  Reemplace `m_wndToolBar.GetBarStyle` por `m_wndToolBar.GetPaneStyle`.  
  
    3.  Reemplace `DockControlBar(&m_wndToolBar)` por `DockPane(&m_wndToolBar)`.  
  
9. En el archivo ipframe.cpp, marque como comentario las tres líneas de código siguientes.  
  
    ```  
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);  
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);  
    pWndFrame->DockPane(&m_wndToolBar);  
    ```  
  
10. Si piensa vincular la aplicación estáticamente, agregue el código siguiente al principio del archivo de recursos del proyecto \(.rc\).  
  
    ```  
    #include "afxribbon.rc"  
    ```  
  
     El archivo afxribbon.rc contiene los recursos necesarios en tiempo de ejecución.  El [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) incluye este archivo automáticamente al crear una aplicación.  
  
11. Guarde los cambios y, a continuación, compile y ejecute la aplicación.  
  
 \[[Secciones](#top)\]  
  
##  <a name="addBitmap"></a> Agregar mapas de bits al proyecto  
 Los siguientes cuatro pasos de este tutorial requieren recursos de mapa de bits.  Puede obtener los mapas de bits adecuados de varias maneras:  
  
-   Utilice los [Resource Editors](../mfc/resource-editors.md) para inventar sus propios mapas de bits.  O bien, utilice los editores de recursos para ensamblar mapas de bits a partir de las imágenes PNG \(Portable Network Graphics\) que se incluyen con [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  Estas imágenes se encuentran en el directorio `VS2008ImageLibrary`.  
  
     Sin embargo, la interfaz de usuario de cinta requiere que ciertos mapas de bits admitan imágenes transparentes.  Los mapas de bits transparentes utilizan píxeles de 32 bits, donde 24 bits especifican los componentes rojo, verde y azul del color, y 8 bits definen un *canal alfa* que especifica la transparencia del color.  Los editores de recursos actuales pueden ver, pero no modificar los mapas de bits con píxeles de 32 bits.  Por consiguiente, utilice un editor de imágenes externo en lugar de los editores de recursos para manipular los mapas de bits transparentes.  
  
-   Copie un archivo de recursos adecuado de otra aplicación al proyecto y, a continuación, importe los mapas de bits de ese archivo.  
  
 En este tutorial, los archivos de recursos se copian de una aplicación en el directorio de ejemplos.  
  
#### Para agregar mapas de bits al proyecto  
  
1.  Utilice el Explorador de archivos para copiar los siguientes archivos .bmp del directorio recursos \(`res`\) del ejemplo RibbonGadgets:  
  
    1.  Copie main.bmp al proyecto Scribble.  
  
    2.  Copie filesmall.bmp y filelarge.bmp al proyecto Scribble.  
  
    3.  Haga nuevas copias de los archivos filelarge.bmp y filesmall.bmp, pero guarde las copias en el ejemplo RibbonGadgets.  Cambie los nombres de las copias a homesmall.bmp y homelarge.bmp, y después mueva las copias al proyecto Scribble.  
  
    4.  Haga una copia del archivo toolbar.bmp, pero guarde la copia en el ejemplo RibbonGadgets.  Cambie el nombre de la copia a panelicons.bmp y después mueva la copia al proyecto Scribble.  
  
2.  Importe el mapa de bits para una aplicación MFC.  En la **Vista de recursos**, haga doble clic en el nodo **scribble.rc**, haga doble clic en el nodo **Mapa de bits** y haga clic en **Agregar recurso**.  En el cuadro de diálogo que aparece, haga clic en **Importar**.  Vaya al directorio `res`, seleccione el archivo main.bmp y haga clic en **Abrir**.  
  
     El mapa de bits main.bmp contiene una imagen de 26x26.  Cambie el identificador del mapa de bits a IDB\_RIBBON\_MAIN.  
  
3.  Importe los mapas de bits para el menú Archivo asociado al botón Aplicación.  
  
    1.  Importe el archivo filesmall.bmp, que contiene diez imágenes de 16x16 \(16x160\).  Dado que necesitamos solo ocho imágenes de 16x16 \(16x128\), utilice la **Vista de recursos** para cambiar el ancho del mapa de bits de 160 a 128.  Cambie el identificador del mapa de bits a IDB\_RIBBON\_FILESMALL.  
  
    2.  Importe filelarge.bmp, que contiene ocho imágenes de 32x32 \(32x256\).  Cambie el identificador del mapa de bits a IDB\_RIBBON\_FILELARGE.  
  
4.  Importe los mapas de bits de las categorías y los paneles de la cinta.  Cada pestaña de la barra de cinta es una categoría y consta de una etiqueta de texto y una imagen opcional.  
  
    1.  Importe el mapa de bits homesmall.bmp, que contiene ocho imágenes de 16x16 para los mapas de bits de botón pequeño.  Cambie el identificador del mapa de bits a IDB\_RIBBON\_HOMESMALL.  
  
    2.  Importe el mapa de bits homelarge.bmp, que contiene ocho imágenes de 32x32 para los mapas de bits de botón grande.  Cambie el identificador del mapa de bits a IDB\_RIBBON\_HOMELARGE.  
  
5.  Importe los mapas de bits de los paneles de cinta con el cambio de tamaño.  Estos mapas de bits, o iconos de panel, se utilizan después de una operación de cambio de tamaño si la cinta es demasiado pequeña para mostrar todo el panel.  
  
    1.  Importe el mapa de bits panelicons.bmp, que contiene ocho imágenes de 16x16.  En la ventana **Propiedades** del **Editor de mapas de bits**, ajuste el ancho del mapa de bits a 64 \(16x64\).  Cambie el identificador del mapa de bits a IDB\_PANEL\_ICONS.  
  
 \[[Secciones](#top)\]  
  
##  <a name="addRibbon"></a> Agregar un recurso de cinta al proyecto  
 Al convertir una aplicación que utiliza los menús de una aplicación que tiene una cinta, no es necesario quitar o deshabilitar los menús existentes.  En su lugar, cree un recurso de cinta, agregue los botones de la cinta y, a continuación, asocie los nuevos botones con los elementos de menú existentes.  Aunque los menús no estén visibles, los mensajes de la barra de cinta se enrutan a través de los menús.  Además, los accesos directos de menú siguen funcionando.  
  
 Una cinta consta del botón Aplicación, que es el botón grande del lado superior izquierdo de la cinta, y una o varias pestañas de categoría.  Cada pestaña de categoría contiene uno o varios paneles que actúan como contenedores para los botones y los controles de la cinta.  En el procedimiento siguiente se muestra cómo crear un recurso de cinta y, después, personalizar el botón Aplicación.  
  
#### Para agregar un recurso de cinta al proyecto  
  
1.  En el menú **Proyecto**, haga clic en **Agregar recurso**.  
  
2.  En el cuadro de diálogo **Agregar recurso**, seleccione **Cinta** y, a continuación, haga clic en **Nueva**.  
  
     Visual Studio crea un recurso de cinta y lo abre en la vista Diseño.  El identificador de recurso de cinta es IDR\_RIBBON1, que se muestra en la **Vista de recursos**.  La cinta contiene una categoría y un panel.  
  
3.  Puede personalizar el botón Aplicación si modifica sus propiedades.  Los identificadores de mensaje que se utilizan en este código ya están definidos en el menú para Scribble 1.0.  
  
4.  En la vista Diseño, haga clic en el botón Aplicación para mostrar sus propiedades.  Cambie los valores de propiedad de la forma siguiente: **Image** a `IDB_RIBBON_MAIN`, **Prompt** a `Archivo`, **Keys** a `f`, **Large Images** a `IDB_RIBBON_FILELARGE` y **Small Images** a `IDB_RIBBON_FILESMALL`.  
  
5.  Las modificaciones siguientes crean el menú que aparece cuando el usuario hace clic en el botón Aplicación.  Haga clic en los puntos suspensivos \(**...**\) que se encuentran junto a **Main Items** para abrir el **Editor de elementos**.  
  
    1.  Haga clic en **Agregar** para agregar un botón.  Cambie **Caption** a `&Nuevo`, **ID** a `ID_FILE_NEW`, **Image** a `0`, **Image Large** a `0`.  
  
    2.  Haga clic en **Agregar** para agregar un segundo botón.  Cambie **Caption** a `&Guardar`, **ID** a `ID_FILE_SAVE`, **Image** a `2` e **Image Large** a `2`.  
  
    3.  Haga clic en **Agregar** para agregar un tercer botón.  Cambie **Caption** a `Guardar &como`, **ID** a `ID_FILE_SAVE_AS`, **Image** a `3` e **Image Large** a `3`.  
  
    4.  Haga clic en **Agregar** para agregar un cuarto botón.  Cambie **Caption** a `&Imprimir`, **ID** a `ID_FILE_PRINT`, **Image** a `4` e **Image Large** a `4`.  
  
    5.  Cambie el tipo **Elemento** a **Separator** y haga clic en **Agregar**.  
  
    6.  Cambie el tipo **Elemento** tipo a **Button**.  Haga clic en **Agregar** para agregar un quinto botón.  Cambie **Caption** a `&Cerrar`, **ID.** a `ID_FILE_CLOSE`, **Image** a `5` e **Image Large** a `5`.  
  
6.  Las modificaciones siguientes crean un submenú del botón Imprimir que creó en el paso anterior.  
  
    1.  Haga clic en el botón **Imprimir**, cambie el tipo **Elemento** a **Label** y, a continuación, haga clic en **Insertar**.  Cambie **Caption** a `Ver vista previa e imprimir el documento`.  
  
    2.  Haga clic en el botón **Imprimir**, cambie el tipo **Elemento** a **Button** y, a continuación, haga clic en **Insertar**.  Cambie **Caption** a `&Imprimir`, **ID** a `ID_FILE_PRINT`, **Image** a `4` e **Image Large** a `4`.  
  
    3.  Haga clic en el botón **Imprimir** y haga clic en **Insertar** para agregar un botón.  Cambie **Caption** a `Impresión &rápida`, **ID** a `ID_FILE_PRINT_DIRECT`, **Image** a `7` e **Image Large** a `7`.  
  
    4.  Haga clic en el botón **Imprimir** y haga clic en **Insertar** para agregar otro botón.  Cambie **Caption** a `&Vista previa de impresión`, **ID** a `ID_FILE_PRINT_PREVIEW`, **Image** a `6` e **Image Large** a`6`.  
  
    5.  Ha modificado los elementos primarios \(**Main Items**\).  Haga clic en **Cerrar** para salir del **Editor de elementos**.  
  
7.  La modificación siguiente crea un botón Salir que aparece en la parte inferior del menú del botón Aplicación.  
  
    1.  En la ventana **Propiedades**, haga clic en el botón de puntos suspensivos \(**...**\) que se encuentra junto a **Button** para abrir el **Editor de elementos**.  
  
    2.  Haga clic en **Agregar** para agregar un botón.  Cambie **Caption** a `&Salir`, **ID** a `ID_APP_EXIT`, **Image** a`8`.  
  
 \[[Secciones](#top)\]  
  
##  <a name="createInstance"></a> Crear una instancia de la barra de cinta  
 En los pasos siguientes se muestra cómo crear una instancia de la barra de cinta cuando se inicia la aplicación.  Para agregar una barra de cinta a una aplicación, declare la barra de cinta en el archivo mainfrm.h.  A continuación, en el archivo mainfrm.cpp, escriba código para cargar el recurso de cinta.  
  
#### Para crear una instancia de la barra de cinta  
  
1.  En el archivo mainfrm.h, agregue un miembro de datos a la sección protegida de `CMainFrame`, la definición de clase del marco principal.  Este miembro representa la barra de cinta.  
  
    ```  
    // Ribbon bar for the application  
    CMFCRibbonBar  m_wndRibbonBar;  
    ```  
  
2.  En el archivo mainfrm.cpp, agregue el código siguiente antes de la última instrucción `return` al final de la función `CMainFrame::OnCreate`.  De esta forma se crea una instancia de la barra de cinta.  
  
    ```  
    // Create the ribbon bar  
    if (!m_wndRibbonBar.Create(this))  
    {  
    return -1;   //Failed to create ribbon bar  
    }  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);  
    ```  
  
 \[[Secciones](#top)\]  
  
##  <a name="addCategory"></a> Personalizar el recurso de cinta  
 Ahora que ha creado el botón Aplicación, puede agregar elementos a la cinta.  
  
> [!NOTE]
>  En este tutorial se utiliza el mismo icono de panel para todos los paneles.  Sin embargo, puede utilizar otros índices de la lista de imágenes para mostrar otros iconos.  
  
#### Para agregar una categoría Inicio y un panel Edición  
  
1.  El programa Scribble solo requiere una categoría.  En la vista Diseño, haga clic en **Categoría** para mostrar sus propiedades.  Cambie los valores de propiedad de la forma siguiente: **Caption** a `&Inicio`, **Large Images** a `IDB_RIBBON_HOMELARGE`, **Small Images** a `IDB_RIBBON_HOMESMALL`.  
  
2.  Cada categoría de la cinta está organizada en paneles con nombre.  Cada panel contiene un conjunto de controles que realizan operaciones relacionadas.  Esta categoría tiene un panel.  Haga clic en **Panel** y cambie **Caption** a `Edición` e **Image Index** a `0`.  
  
3.  En el panel **Edición**, agregue un botón que será responsable de borrar el contenido del documento.  El identificador de mensaje para este botón se ha definido en el recurso de menú IDR\_SCRIBBTYPE.  Especifique `Borrar todo` como texto del botón y el índice del mapa de bits que decora el botón.  Abra el **Cuadro de herramientas** y luego arrastre **Button** al panel **Edición**.  Haga clic en el botón y, a continuación, cambie **Caption** a `Borrar todo`, **ID** a `ID_EDIT_CLEAR_ALL`, **Image Index** a `0`, **Large Image Index** a `0`.  
  
4.  Guarde los cambios y, a continuación, compile y ejecute la aplicación.  La aplicación Scribble debería mostrarse y debe tener una barra de cinta en la parte superior de la ventana en lugar de una barra de menús.  La barra de cinta debe tener una categoría, **Inicio**, e **Inicio** debe tener un panel, **Edición**.  Los botones de la cinta que agregó deben estar asociados a los controladores de eventos existentes y los botones **Abrir**, **Cerrar**, **Guardar**, **Imprimir** y **Borrar todo** deben funcionar como se espera.  
  
 \[[Secciones](#top)\]  
  
##  <a name="setLook"></a> Configurar la apariencia de la aplicación  
 Un *administrador visual* es un objeto global que controla todos los dibujos de una aplicación.  Dado que la aplicación original Scribble utiliza el estilo de la interfaz de usuario de Office 2000, la aplicación puede parecer antigua.  Puede restablecer la aplicación para utilizar el administrador visual de Office 2007 de modo sea similar a una aplicación de Office 2007.  
  
#### Para establecer la apariencia de la aplicación  
  
1.  En la función `CMainFrame::OnCreate`, escriba el código siguiente para cambiar el administrador visual y el estilo predeterminados.  
  
    ```  
    // Set the default manager to Office 2007   
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));  
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);  
    ```  
  
2.  Guarde los cambios y, a continuación, compile y ejecute la aplicación.  La interfaz de usuario de la aplicación debe ser similar a la de Office 2007.  
  
 \[[Secciones](#top)\]  
  
## Pasos siguientes  
 Ha modificado el ejemplo clásico Scribble de MFC 1.0 para utilizar el diseñador de la cinta de opciones.  Ahora vaya a la [parte 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).  
  
## Vea también  
 [Tutoriales](../mfc/walkthroughs-mfc.md)   
 [Tutorial: Actualizar la aplicación Scribble de MFC \(Parte 2\)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)