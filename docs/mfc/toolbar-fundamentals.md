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
ms.openlocfilehash: d4e8793337beb2eed533fe04daf549ec21efc61d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373478"
---
# <a name="toolbar-fundamentals"></a>Fundamentos de las barras de herramientas

En este artículo se describe la implementación fundamental de MFC que le permite agregar una barra de herramientas predeterminada a la aplicación seleccionando una opción en el Asistente para aplicaciones. Temas cubiertos:

- [La opción de barra de herramientas del Asistente para aplicaciones](#_core_the_appwizard_toolbar_option)

- [La barra de herramientas en el código](#_core_the_toolbar_in_code)

- [Edición del recurso de la barra de herramientas](#_core_editing_the_toolbar_resource)

- [Múltiples barras de herramientas](#_core_multiple_toolbars)

## <a name="the-application-wizard-toolbar-option"></a><a name="_core_the_appwizard_toolbar_option"></a>La opción de la barra de herramientas del Asistente para aplicaciones

Para obtener una sola barra de herramientas con botones predeterminados, seleccione la opción de barra de herramientas Acoplamiento estándar en la página denominada Características de la interfaz de usuario. Esto agrega código a la aplicación que:

- Crea el objeto de barra de herramientas.

- Administra la barra de herramientas, incluida su capacidad para acoplar o flotar.

## <a name="the-toolbar-in-code"></a><a name="_core_the_toolbar_in_code"></a>La barra de herramientas en el código

La barra de herramientas es un [CToolBar](../mfc/reference/ctoolbar-class.md) objeto `CMainFrame` declarado como un miembro de datos de la clase de la aplicación. En otras palabras, el objeto de barra de herramientas está incrustado en el objeto de ventana de marco principal. Esto significa que MFC crea la barra de herramientas cuando crea la ventana de marco y destruye la barra de herramientas cuando destruye la ventana de marco. La siguiente declaración de clase parcial, para una aplicación de interfaz de varios documentos (MDI), muestra los miembros de datos para una barra de herramientas incrustada y una barra de estado incrustada. También muestra la invalidación de la `OnCreate` función miembro.

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

La creación `CMainFrame::OnCreate`de la barra de herramientas se produce en . MFC llama a [OnCreate](../mfc/reference/cwnd-class.md#oncreate) después de crear la ventana para el marco, pero antes de que se vuelva visible. El `OnCreate` valor predeterminado que genera el Asistente para aplicaciones realiza las siguientes tareas de la barra de herramientas:

1. Llama `CToolBar` al objeto [Create](../mfc/reference/ctoolbar-class.md#create) función miembro para crear el subyacente [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objeto.

1. Llama a [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) para cargar la información de recursos de la barra de herramientas.

1. Llama a funciones para habilitar las sugerencias de acoplamiento, flotantes y herramientas. Para obtener más información sobre estas llamadas, consulte el artículo [Acoplar y barras](../mfc/docking-and-floating-toolbars.md)de herramientas flotantes .

> [!NOTE]
> El ejemplo general de MFC [DOCKTOOL](../overview/visual-cpp-samples.md) incluye ilustraciones de barras de herramientas MFC antiguas y nuevas. Las barras de `COldToolbar` herramientas que utilizan `LoadBitmap` requieren `LoadToolBar`llamadas `SetButtons`en el paso 2 a (en lugar de ) y a . Las nuevas barras `LoadToolBar`de herramientas requieren llamadas a .

Las llamadas de acoplamiento, flotantes y sugerencias de herramientas son opcionales. Puede eliminar esas `OnCreate` líneas si lo prefiere. El resultado es una barra de herramientas que permanece fija, no puede flotar o volver a acoplar e incapaz de mostrar sugerencias de herramientas.

## <a name="editing-the-toolbar-resource"></a><a name="_core_editing_the_toolbar_resource"></a>Edición del recurso de la barra de herramientas

La barra de herramientas predeterminada que se obtiene con el Asistente para aplicaciones se basa en un **RT_TOOLBAR** recurso personalizado, introducido en MFC versión 4.0. Puede editar este recurso con el editor de la barra de [herramientas.](../windows/toolbar-editor.md) El editor le permite agregar, eliminar y reorganizar fácilmente los botones. Contiene un editor gráfico para los botones que es muy similar al editor de gráficos general en Visual C++. Si ha editado barras de herramientas en versiones anteriores de Visual C++, la tarea le resultará mucho más fácil ahora.

Para conectar un botón de barra de herramientas a `ID_MYCOMMAND`un comando, asigne al botón un identificador de comando, como . Especifique el identificador de comando en la página de propiedades del botón en el editor de la barra de herramientas. A continuación, cree una función de controlador para el comando (consulte Asignación de [mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para obtener más información).

Nuevas funciones miembro [de CToolBar](../mfc/reference/ctoolbar-class.md) funcionan con el recurso **RT_TOOLBAR.** [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) ahora toma el lugar de [LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap) para cargar el mapa de bits de las imágenes del botón de barra de herramientas y [SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons) para establecer los estilos de botón y conectar botones con imágenes de mapa de bits.

Para obtener más información sobre el uso del editor de la barra de herramientas, consulte [Editor de](../windows/toolbar-editor.md)barras de herramientas .

## <a name="multiple-toolbars"></a><a name="_core_multiple_toolbars"></a>Múltiples barras de herramientas

El Asistente para aplicaciones proporciona una barra de herramientas predeterminada. Si necesita más de una barra de herramientas en la aplicación, puede modelar el código para barras de herramientas adicionales en función del código generado por el asistente para la barra de herramientas predeterminada.

Si desea mostrar una barra de herramientas como resultado de un comando, deberá:

- Cree un nuevo recurso de barra de `OnCreate` herramientas con el editor de la barra de herramientas y cárguelo con la [LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) función miembro.

- Incrustar un nuevo [CToolBar](../mfc/reference/ctoolbar-class.md) objeto en la clase de ventana de marco principal.

- Realice las llamadas `OnCreate` de función adecuadas para acoplar o flotar la barra de herramientas, establecer sus estilos, etc.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Implementación de la barra de herramientas MFC (información general sobre las barras de herramientas)](../mfc/mfc-toolbar-implementation.md)

- [Barras de herramientas de acoplamiento y flotantes](../mfc/docking-and-floating-toolbars.md)

- [Consejos de herramientas de la barra de herramientas](../mfc/toolbar-tool-tips.md)

- Las clases [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Trabajar con el control de la barra de herramientas](../mfc/working-with-the-toolbar-control.md)

- [Uso de las barras de herramientas antiguas](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Consulte también

[Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)
