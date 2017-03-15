---
title: "Fundamentos de las barras de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RT_TOOLBAR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asistentes para aplicaciones [C++], instalar barras de herramientas de la aplicación predeterminadas"
  - "identificadores de comando, botones de la barra de herramientas"
  - "CToolBar (clase), barras de herramientas predeterminadas del Asistente para aplicaciones"
  - "incrustar barra de herramientas en una clase de ventana de marco"
  - "clases de ventana de marco, barra de herramientas incrustada en"
  - "LoadBitmap (método), barras de herramientas"
  - "LoadToolBar (método)"
  - "recursos [MFC], barra de herramientas"
  - "RT_TOOLBAR (recurso)"
  - "SetButtons (método)"
  - "controles de barra de herramientas [MFC], identificador de comando"
  - "controles de barra de herramientas [MFC], barras de herramientas creadas mediante el Asistente para aplicaciones"
  - "Editor de barras de herramientas, Asistente para aplicaciones"
  - "barras de herramientas [C++], agregar predeterminadas mediante el Asistente para aplicaciones"
  - "barras de herramientas [C++], crear"
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Fundamentos de las barras de herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe la implementación fundamental de MFC que permite agregar una barra de herramientas predeterminada a la aplicación seleccionando una opción en el Asistente para aplicaciones.  Entre los temas tratados, se incluyen los siguientes:  
  
-   [La opción de barras de herramientas del Asistente para aplicaciones](#_core_the_appwizard_toolbar_option)  
  
-   [La barra de herramientas en código](#_core_the_toolbar_in_code)  
  
-   [Editar el recurso de la barra de herramientas](#_core_editing_the_toolbar_resource)  
  
-   [Barras de herramientas varias](#_core_multiple_toolbars)  
  
##  <a name="_core_the_appwizard_toolbar_option"></a> La opción de barras de herramientas del Asistente para aplicaciones  
 Para obtener una única barra de herramientas con los botones predeterminados, seleccione la opción de barras de herramientas estándar de acoplamiento en la página denominada las características de la interfaz de usuario.  Esto agrega código a la aplicación que:  
  
-   Crea el objeto de la barra de herramientas.  
  
-   Administra la barra de herramientas, incluida su capacidad de acoplar o de flotar.  
  
##  <a name="_core_the_toolbar_in_code"></a> La barra de herramientas en código  
 La barra de herramientas es un objeto de [CToolBar](../mfc/reference/ctoolbar-class.md) declarado como miembro de datos de la clase de **CMainFrame** de la aplicación.  Es decir el objeto de la barra de herramientas se inserta en el objeto de la ventana de marco principal.  Esto significa que MFC crea la barra de herramientas cuando crea la ventana de marco y destruye la barra de herramientas cuando se destruye la ventana de marco.  La declaración de clase parcial siguiente, para una aplicación de \(MDI\) de interfaz de múltiples documentos, muestra los miembros de datos de una barra de herramientas incrustada y una barra de estado incrustada.  También se muestra la invalidación de la función miembro de `OnCreate` .  
  
 [!code-cpp[NVC_MFCListView#6](../mfc/codesnippet/CPP/toolbar-fundamentals_1.h)]  
  
 La creación de la barra de herramientas en **CMainFrame::OnCreate**.  MFC llama a [OnCreate](../Topic/CWnd::OnCreate.md) después de crear la ventana del cuadro pero antes de que esté visible.  `OnCreate` predeterminado que el Asistente para aplicaciones genera realiza las tareas siguientes de la barra de herramientas:  
  
1.  Llama a la función miembro de [crear](../Topic/CToolBar::Create.md) del objeto de `CToolBar` para crear el objeto subyacente de [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) .  
  
2.  Llama a [LoadToolBar](../Topic/CToolBar::LoadToolBar.md) para cargar la información del recurso de la barra de herramientas.  
  
3.  Las llamadas funcionan para habilitar el acoplamiento, la flotante, y la información sobre herramientas.  Para obtener más información sobre estas llamadas, vea el artículo [Acoplamiento y barras de herramientas flotante](../mfc/docking-and-floating-toolbars.md).  
  
> [!NOTE]
>  El ejemplo [DOCKTOOL](../top/visual-cpp-samples.md) MFC General incluye ilustraciones de barras de herramientas antiguas y nuevas de MFC.  Barras de herramientas que utilizan **COldToolbar** requieren llamadas en el paso 2 a `LoadBitmap` \(en lugar de `LoadToolBar`\) y a `SetButtons`.  Las nuevas barras de herramientas requieren llamadas a `LoadToolBar`.  
  
 El acoplamiento, la flotante, y las llamadas de información sobre herramientas son opcionales.  Puede quitar las líneas de `OnCreate` si prefiere.  El resultado es una barra de herramientas que permanece fija, incapaz de flotar o redock y es de mostrar información sobre herramientas.  
  
##  <a name="_core_editing_the_toolbar_resource"></a> Editar el recurso de la barra de herramientas  
 La barra de herramientas predeterminada que se obtiene con el Asistente para aplicaciones se basa en un recurso personalizado de **RT\_TOOLBAR** , mostrado en la versión 4.0 de MFC.  Puede modificar a este recurso con [editor de barras de herramientas](../mfc/toolbar-editor.md).  El editor permite agregar fácilmente, eliminar, y reorganizar los botones.  Contiene un editor gráfico para los botones que es muy similar al editor de gráficos general en Visual C\+\+.  Si editó barras de herramientas en las versiones anteriores de Visual C\+\+, ahora encontrará la tarea mucho más fácil.  
  
 Para conectar un botón de la barra de herramientas a un comando, se proporciona a botón un identificador de comando, como `ID_MYCOMMAND`.  Especifique el identificador de comando en la página de propiedades del botón en el editor de barras de herramientas.  A continuación cree una función controladora para el comando \(vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para obtener más información\).  
  
 Nuevo trabajo de las funciones miembro de [CToolBar](../mfc/reference/ctoolbar-class.md) con el recurso de **RT\_TOOLBAR** .  [LoadToolBar](../Topic/CToolBar::LoadToolBar.md) ahora sustituye a [LoadBitmap](../Topic/CToolBar::LoadBitmap.md) para cargar el mapa de bits de las imágenes de botón de la barra de herramientas, y [SetButtons](../Topic/CToolBar::SetButtons.md) para establecer estilos de botón y conectar los botones con imágenes de mapa de bits.  
  
 Para obtener más información sobre cómo utilizar el editor de barras de herramientas, vea [Editor de barras de herramientas](../mfc/toolbar-editor.md).  
  
##  <a name="_core_multiple_toolbars"></a> Barras de herramientas varias  
 El Asistente para aplicaciones le proporciona una barra de herramientas predeterminada.  Si necesita más de una barra de herramientas en la aplicación, puede modelar el código para las barras de herramientas adicionales basadas en el código asistente\- generado para la barra de herramientas predeterminada.  
  
 Si desea mostrar una barra de herramientas como resultado de un comando, necesitará:  
  
-   Cree un nuevo recurso de la barra de herramientas con el editor de barras de herramientas y cárguelo en `OnCreate` mediante la función miembro de [LoadToolbar](../Topic/CToolBar::LoadToolBar.md) .  
  
-   Inserte un nuevo objeto de [CToolBar](../mfc/reference/ctoolbar-class.md) en la clase de ventana de marco principal.  
  
-   Haga las llamadas de función adecuadas en `OnCreate` para acoplar o desacoplar la barra de herramientas, establezca sus estilos, y así sucesivamente.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Implementación de la barra de herramientas de MFC \(de información general de las barras de herramientas\)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Barras de herramientas de acoplamiento y flotantes](../mfc/docking-and-floating-toolbars.md)  
  
-   [Información sobre herramientas de la barra de herramientas](../mfc/toolbar-tool-tips.md)  
  
-   Clases [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
  
-   [Trabajar con el control de barra de herramientas](../mfc/working-with-the-toolbar-control.md)  
  
-   [Mediante las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)  
  
## Vea también  
 [Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)