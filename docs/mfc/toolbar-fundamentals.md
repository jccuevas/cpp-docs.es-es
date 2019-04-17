---
title: Fundamentos de las barras de herramientas
ms.date: 11/04/2016
f1_keywords:
- RT_TOOLBAR
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
ms.openlocfilehash: 9c784db2e1a482b313147e6837d6bbbd16d0ecb4
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775496"
---
# <a name="toolbar-fundamentals"></a>Fundamentos de las barras de herramientas

En este artículo se describe la implementación de MFC fundamental que le permite agregar una barra de herramientas predeterminada a la aplicación seleccionando una opción en el Asistente para la aplicación. Los temas tratados se incluyen:

- [La opción de barra de herramientas del Asistente para aplicaciones](#_core_the_appwizard_toolbar_option)

- [La barra de herramientas en el código](#_core_the_toolbar_in_code)

- [Editar el recurso de la barra de herramientas](#_core_editing_the_toolbar_resource)

- [Varias barras de herramientas](#_core_multiple_toolbars)

##  <a name="_core_the_appwizard_toolbar_option"></a> La opción de barra de herramientas del Asistente de aplicación

Para obtener una sola barra de herramientas con botones predeterminados, seleccione la opción de barra de herramientas estándar de acoplamiento en la página características de la interfaz de usuario con la etiqueta. Esto agrega código a la aplicación que:

- Crea el objeto de barra de herramientas.

- Administra la barra de herramientas, incluida su capacidad para acoplar o flotante.

##  <a name="_core_the_toolbar_in_code"></a> La barra de herramientas en el código

La barra de herramientas es una [CToolBar](../mfc/reference/ctoolbar-class.md) objeto declarado como un miembro de datos de la aplicación `CMainFrame` clase. En otras palabras, el objeto de barra de herramientas está incrustado en el objeto de ventana de marco principal. Esto significa que MFC crea la barra de herramientas cuando se crea la ventana de marco y destruye la barra de herramientas cuando se destruye la ventana de marco. La siguiente declaración de clase parcial, para una aplicación de múltiples documentos (MDI) de la interfaz, muestra a los miembros de datos de una barra de herramientas incrustada y una barra de estado incrustada. También se muestra la invalidación de la `OnCreate` función miembro.

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

Creación de la barra de herramientas se produce en `CMainFrame::OnCreate`. Las llamadas MFC [OnCreate](../mfc/reference/cwnd-class.md#oncreate) después de crear la ventana del marco, pero antes de que esté visible. El valor predeterminado `OnCreate` que genera el Asistente para la aplicación realiza las siguientes tareas de la barra de herramientas:

1. Llama a la `CToolBar` del objeto [crear](../mfc/reference/ctoolbar-class.md#create) función miembro para crear subyacente [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objeto.

1. Las llamadas [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) para cargar la información de recursos de la barra de herramientas.

1. Llama a las funciones para habilitar el acoplamiento, flotante e información sobre herramientas. Para obtener más información acerca de estas llamadas, vea el artículo [acoplamiento y barras de herramientas flotante](../mfc/docking-and-floating-toolbars.md).

> [!NOTE]
>  El ejemplo General de MFC [DOCKTOOL](../overview/visual-cpp-samples.md) incluye las ilustraciones de barras de herramientas MFC antiguos y nuevos. Las barras de herramientas que usan `COldToolbar` requieren llamadas en el paso 2 para `LoadBitmap` (en lugar de `LoadToolBar`) y a `SetButtons`. Las barras de herramientas nueva requieren llamadas a `LoadToolBar`.

El acoplamiento, flotante y llamadas de herramienta sugerencias son opcionales. Puede quitar las líneas del `OnCreate` si lo prefiere. El resultado es una barra de herramientas que permanece fijo, no se puede float o volver a acoplarse y no se puede mostrar información sobre herramientas.

##  <a name="_core_editing_the_toolbar_resource"></a> Editar el recurso de la barra de herramientas

La barra de herramientas predeterminada que obtiene con el Asistente para la aplicación se basa en un **RT_TOOLBAR** recursos personalizados, introducido en la versión 4.0 de MFC. Puede editar este recurso con el [editor de la barra de herramientas](../windows/toolbar-editor.md). El editor permite agregar, eliminar y reorganizar botones con facilidad. Contiene un editor gráfico para los botones que es muy similares al editor de gráficos generales de Visual C++. Si edita las barras de herramientas en versiones anteriores de Visual C++, encontrará la tarea mucho más fácil ahora.

Para conectar un botón de barra de herramientas a un comando, se le da al botón un identificador de comando, como `ID_MYCOMMAND`. Especifique el identificador de comando en la página de propiedades del botón en el editor de la barra de herramientas. A continuación, cree una función de controlador para el comando (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para obtener más información).

Nuevo [CToolBar](../mfc/reference/ctoolbar-class.md) trabajan las funciones miembro con el **RT_TOOLBAR** recursos. [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) ahora ocupa el lugar de [LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap) para cargar el mapa de bits de las imágenes de botón de barra de herramientas, y [SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons) para establecer los estilos de botón y conectar botones con imágenes de mapa de bits.

Para obtener más información sobre cómo usar el editor de la barra de herramientas, consulte [barra de herramientas del Editor](../windows/toolbar-editor.md).

##  <a name="_core_multiple_toolbars"></a> Varias barras de herramientas

El Asistente para aplicaciones le proporcionará la barra de herramientas de un valor predeterminado. Si necesita más de una barra de herramientas en la aplicación, puede modelar el código de barras de herramientas adicionales en función del código generado por el Asistente para la barra de herramientas predeterminada.

Si desea mostrar una barra de herramientas como el resultado de un comando, deberá:

- Crear un nuevo recurso de barra de herramientas con la barra de herramientas del editor y cargarlo en `OnCreate` con el [LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) función miembro.

- Insertar un nuevo [CToolBar](../mfc/reference/ctoolbar-class.md) objeto en la clase de ventana de marco principal.

- Asegúrese que se llama la función apropiada en `OnCreate` para acoplar o float de la barra de herramientas, definir sus estilos y así sucesivamente.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Implementación de la barra de herramientas de MFC (información general sobre las barras de herramientas)](../mfc/mfc-toolbar-implementation.md)

- [Acoplar y desacoplar las barras de herramientas](../mfc/docking-and-floating-toolbars.md)

- [Información sobre herramientas de barra de herramientas](../mfc/toolbar-tool-tips.md)

- El [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) clases

- [Trabajar con el control de barra de herramientas](../mfc/working-with-the-toolbar-control.md)

- [Uso de las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Vea también

[Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)
