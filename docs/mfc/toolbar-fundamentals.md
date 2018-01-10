---
title: "Aspectos básicos de la barra de herramientas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RT_TOOLBAR
dev_langs: C++
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 136b9f5dd36c9e4092b8e5c15ac1738541cf71f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="toolbar-fundamentals"></a>Fundamentos de las barras de herramientas
En este artículo se describe la implementación de MFC fundamental que le permite agregar una barra de herramientas de forma predeterminada a la aplicación seleccionando una opción en el Asistente para aplicaciones. Los temas tratados son:  
  
-   [La opción de barra de herramientas del Asistente para aplicaciones](#_core_the_appwizard_toolbar_option)  
  
-   [La barra de herramientas en el código](#_core_the_toolbar_in_code)  
  
-   [Editar el recurso de barra de herramientas](#_core_editing_the_toolbar_resource)  
  
-   [Varias barras de herramientas](#_core_multiple_toolbars)  
  
##  <a name="_core_the_appwizard_toolbar_option"></a>La opción de barra de herramientas del Asistente para aplicaciones  
 Para obtener una sola barra de herramientas con botones predeterminados, seleccione la opción de barra de herramientas de acoplamiento estándar en la página características de la interfaz de usuario de la etiqueta. Esto agrega código a la aplicación que:  
  
-   Crea el objeto de barra de herramientas.  
  
-   Administra la barra de herramientas, incluida su capacidad para acoplar o flotante.  
  
##  <a name="_core_the_toolbar_in_code"></a>La barra de herramientas en el código  
 La barra de herramientas es un [CToolBar](../mfc/reference/ctoolbar-class.md) objeto declarado como un miembro de datos de la aplicación **CMainFrame** clase. En otras palabras, el objeto de barra de herramientas está incrustado en el objeto de ventana de marco principal. Esto significa que MFC crea la barra de herramientas cuando se crea la ventana de marco y se destruye la barra de herramientas cuando destruye la ventana de marco. La siguiente declaración de clase parcial, para una aplicación de múltiples documentos (MDI) de la interfaz, muestra a los miembros de datos de una barra de herramientas incrustada y una barra de estado incrustada. También muestra la invalidación de la `OnCreate` función miembro.  
  
 [!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]  
  
 Creación de la barra de herramientas se produce en **CMainFrame:: OnCreate**. Llamadas MFC [OnCreate](../mfc/reference/cwnd-class.md#oncreate) después de crear la ventana para el marco, pero antes de que sea visible. El valor predeterminado `OnCreate` que genera el Asistente para aplicaciones realiza las siguientes tareas de la barra de herramientas:  
  
1.  Llamadas a la `CToolBar` del objeto [crear](../mfc/reference/ctoolbar-class.md#create) función de miembro para crear subyacente [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objeto.  
  
2.  Llamadas [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) para cargar la información de recursos de la barra de herramientas.  
  
3.  Llama a las funciones para habilitar el acoplamiento, flotante e información sobre herramientas. Para obtener más información acerca de estas llamadas, vea el artículo [acoplar y desacoplar barras de herramientas](../mfc/docking-and-floating-toolbars.md).  
  
> [!NOTE]
>  El ejemplo General de MFC [DOCKTOOL](../visual-cpp-samples.md) incluye ilustraciones de barras de herramientas MFC antiguos y nuevos. Las barras de herramientas que usan **COldToolbar** , necesitan llamadas en el paso 2 para `LoadBitmap` (en lugar de `LoadToolBar`) y a `SetButtons`. Las barras de herramientas nuevas, necesitan llamadas a `LoadToolBar`.  
  
 El acoplamiento, flotante y llamadas de sugerencias de herramienta son opcionales. Puede quitar esas líneas de `OnCreate` si lo prefiere. El resultado es una barra de herramientas que permanece fijo, no se ha podido float o volver a acoplarse y no se puede mostrar información sobre herramientas.  
  
##  <a name="_core_editing_the_toolbar_resource"></a>Editar el recurso de barra de herramientas  
 La barra de herramientas predeterminada que se obtienen con el Asistente para aplicaciones se basa en un **RT_TOOLBAR** recurso personalizado, que se introdujo en la versión 4.0 de MFC. Puede editar este recurso con el [editor de la barra de herramientas](../windows/toolbar-editor.md). El editor permite agregar, eliminar y reorganizar botones fácilmente. Contiene un editor gráfico para los botones que es muy similares al editor de gráficos general de Visual C++. Si edita las barras de herramientas en versiones anteriores de Visual C++, encontrará la tarea mucho más fácil ahora.  
  
 Para conectar un botón de barra de herramientas a un comando, se le da al botón un identificador de comando, como `ID_MYCOMMAND`. Especifique el identificador de comando en la página de propiedades del botón en el editor de la barra de herramientas. A continuación, cree una función de controlador para el comando (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para obtener más información).  
  
 Nueva [CToolBar](../mfc/reference/ctoolbar-class.md) funciones miembro trabajar con el **RT_TOOLBAR** recursos. [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) ahora ocupa el lugar de [LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap) para cargar el mapa de bits de las imágenes de botón de barra de herramientas, y [SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons) para establecer los estilos de botón y conectar botones con imágenes de mapa de bits.  
  
 Para obtener más información acerca de cómo utilizar el editor de la barra de herramientas, consulte [barra de herramientas del Editor](../windows/toolbar-editor.md).  
  
##  <a name="_core_multiple_toolbars"></a>Varias barras de herramientas  
 El Asistente para aplicaciones proporciona una barra de herramientas de un valor predeterminado. Si necesita más de una barra de herramientas en la aplicación, puede modelar su código de barras de herramientas adicionales en función del código generado por el Asistente para la barra de herramientas predeterminada.  
  
 Si desea mostrar una barra de herramientas como el resultado de un comando, debe:  
  
-   Crear un nuevo recurso de barra de herramientas con la barra de herramientas del editor y cargarlo en `OnCreate` con el [LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) función miembro.  
  
-   Insertar un nuevo [CToolBar](../mfc/reference/ctoolbar-class.md) objeto en la clase de ventana de marco principal.  
  
-   Asegúrese que se llama a la función adecuada en `OnCreate` para acoplar o flotar la barra de herramientas, definir sus estilos y así sucesivamente.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Implementación de la barra de herramientas de MFC (información general de las barras de herramientas)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Acoplar y desacoplar las barras de herramientas](../mfc/docking-and-floating-toolbars.md)  
  
-   [Información sobre herramientas de barra de herramientas](../mfc/toolbar-tool-tips.md)  
  
-   El [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) clases  
  
-   [Trabajar con el control de barra de herramientas](../mfc/working-with-the-toolbar-control.md)  
  
-   [Uso de las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Vea también  
 [Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)

