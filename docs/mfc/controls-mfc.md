---
title: Controles (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: accbee66cdee4e7b849da2b034d253b1c206d8f1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617179"
---
# <a name="controls-mfc"></a>Controles (MFC)

Los controles de formularios son objetos con los que pueden interactuar los usuarios para escribir o manipular datos. Aparecen normalmente en los cuadros de diálogo o en las barras de herramientas. En esta familia de temas se abordan tres clases principales de controles:

- Controles comunes de Windows, como los controles dibujados por el propietario

- Controles ActiveX

- Otras clases de controles proporcionadas por la biblioteca MFC (Microsoft Foundation Class)

## <a name="windows-common-controls"></a>Controles comunes de Windows

El sistema operativo Windows siempre ha proporcionado varios controles comunes de Windows. Estos objetos de control se pueden programar y el editor de cuadros de diálogo de Visual C++ admite agregarlos a los cuadros de diálogo. Las biblioteca MFC (Microsoft Foundation Class) proporciona clases que encapsulan cada uno de estos controles, como se muestra en la tabla [Controles comunes y clases MFC de Windows](#_core_windows_common_controls_and_mfc_classes). (Para algunos elementos de la tabla hay temas relacionados que los describen más detalladamente. Para los controles que no tienen temas relacionados, vea la documentación de la clase MFC).

La clase [CWnd](reference/cwnd-class.md) es la clase base de todas las clases de ventana, incluidas todas las clases de control.

## <a name="activex-controls"></a>Controles ActiveX

Los controles ActiveX, antes conocidos como controles OLE, se pueden utilizar en cuadros de diálogo en las aplicaciones para Windows o en páginas HTML en World Wide Web. Para obtener más información, vea [controles ActiveX MFC](mfc-activex-controls.md).

## <a name="other-mfc-control-classes"></a>Otras clases de controles MFC

Además de las clases que encapsulan todos los controles comunes de Windows y que admiten la programación de controles ActiveX propios (o el uso de controles ActiveX suministrados por otros), MFC proporciona sus propias clases de controles:

- [CBitmapButton](reference/cbitmapbutton-class.md)

- [CCheckListBox](reference/cchecklistbox-class.md)

- [CDragListBox](reference/cdraglistbox-class.md)

## <a name="finding-information-about-windows-common-controls"></a><a name="_core_finding_information_about_windows_common_controls"></a> Buscar información sobre los controles comunes de Windows

En la tabla siguiente se describe brevemente cada uno de los controles comunes de Windows y se incluye la clase contenedora MFC del control.

### <a name="windows-common-controls-and-mfc-classes"></a><a name="_core_windows_common_controls_and_mfc_classes"></a>Controles comunes de Windows y clases MFC

|Control|clase MFC|Descripción|Novedades de Windows 95|
|-------------|---------------|-----------------|------------------------|
|[animación](using-canimatectrl.md)|[CAnimateCtrl](reference/canimatectrl-class.md)|Muestra cuadros sucesivos de un clip de vídeo AVI|Sí|
|botón|[CButton](reference/cbutton-class.md)|Botones de comando que producen una acción; también se utilizan para las casillas, los botones de radio y los cuadros de grupo|No|
|cuadro combinado|[CComboBox](reference/ccombobox-class.md)|Combinación de un cuadro de edición y un cuadro de lista|No|
|[selector de fecha y hora](using-cdatetimectrl.md)|[CDateTimeCtrl](reference/cdatetimectrl-class.md)|Permite elegir un valor de fecha y hora concreto|Sí|
|cuadro de edición|[CEdit](reference/cedit-class.md)|Cuadros para escribir texto|No|
|[cuadro combinado extendido](using-ccomboboxex.md)|[CComboBoxEx](reference/ccomboboxex-class.md)|Un control de cuadro combinado con la capacidad de mostrar imágenes|Sí|
|[encabezado](using-cheaderctrl.md)|[CHeaderCtrl](reference/cheaderctrl-class.md)|Botón que aparece sobre una columna de texto; controla el ancho del texto mostrado|Sí|
|[directa](using-chotkeyctrl.md)|[CHotKeyCtrl](reference/chotkeyctrl-class.md)|Ventana que permite crear una “tecla de acceso rápido” para realizar una acción rápidamente|Sí|
|[lista de imágenes](using-cimagelist.md)|[CImageList](reference/cimagelist-class.md)|Colección de imágenes que se utilizan para administrar conjuntos grandes de iconos o de mapas de bits (la lista de imágenes no es realmente un control; admite las listas utilizadas por otros controles)|Sí|
|[list](using-clistctrl.md)|[CListCtrl](reference/clistctrl-class.md)|Ventana que muestra una lista de texto con iconos|Sí|
|cuadro de lista|[CListBox](reference/clistbox-class.md)|Cuadro que contiene una lista de cadenas|No|
|[calendario mensual](using-cmonthcalctrl.md)|[CMonthCalCtrl](reference/cmonthcalctrl-class.md)|Control que muestra información de fecha|Sí|
|[progreso](using-cprogressctrl.md)|[CProgressCtrl](reference/cprogressctrl-class.md)|Ventana que indica el progreso de una operación prolongada|Sí|
|[rebar](using-crebarctrl.md)|[CRebarCtrl](reference/crebarctrl-class.md)|Barra de herramientas que puede contener ventanas secundarias adicionales en forma de controles|Sí|
|[rich edit](using-cricheditctrl.md)|[CRichEditCtrl](reference/cricheditctrl-class.md)|Ventana en la que el usuario puede realizar modificación con formato de carácter y de párrafo (vea [Clases relacionadas con los controles rich edit](classes-related-to-rich-edit-controls.md))|Sí|
|barra de desplazamiento|[CScrollBar](reference/cscrollbar-class.md)|Barra de desplazamiento utilizada como control dentro de un cuadro de diálogo (no en una ventana)|No|
|[hasta](using-csliderctrl.md)|[CSliderCtrl](reference/csliderctrl-class.md)|Ventana que contiene un control deslizante con marcas de graduación opcionales|Sí|
|[botón de número](using-cspinbuttonctrl.md)|[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)|Par de botones de flecha en los que el usuario puede hacer clic para aumentar o reducir un valor|Sí|
|texto estático|[CStatic](reference/cstatic-class.md)|Texto para etiquetar otros controles|No|
|[barra de estado](using-cstatusbarctrl.md)|[CStatusBarCtrl](reference/cstatusbarctrl-class.md)|Ventana para mostrar información de estado, similar a la clase MFC `CStatusBar`|Sí|
|[ficha](using-ctabctrl.md)|[CTabCtrl](reference/ctabctrl-class.md)|Análoga a los divisores de un bloc de notas; se usa en "cuadros de diálogo de pestaña" o en hojas de propiedades|Sí|
|[barra](using-ctoolbarctrl.md)|[CToolBarCtrl](reference/ctoolbarctrl-class.md)|Ventana con botones que generan comandos, similares a la clase MFC `CToolBar`|Sí|
|[información sobre herramientas](using-ctooltipctrl.md)|[CToolTipCtrl](reference/ctooltipctrl-class.md)|Pequeña ventana emergente que describe el propósito de un botón de la barra de herramientas o de otra herramienta|Sí|
|[tree](using-ctreectrl.md)|[CTreeCtrl](reference/ctreectrl-class.md)|Ventana que muestra una lista jerárquica de elementos|Sí|

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- Un control individual: vea la tabla [Controles comunes de Windows y clases MFC](#_core_windows_common_controls_and_mfc_classes) en este tema para obtener vínculos a todos los controles.

- [Crear y usar controles](making-and-using-controls.md)

- [Usar el editor de cuadros de diálogo para agregar controles](using-the-dialog-editor-to-add-controls.md)

- [Agregar controles a un cuadro de diálogo a mano](adding-controls-by-hand.md)

- [Derivar clases de control de las clases de control MFC](deriving-controls-from-a-standard-control.md)

- [Utilizar los controles comunes como ventanas secundarias](using-a-common-control-as-a-child-window.md)

- [Notificaciones de los controles comunes](receiving-notification-from-common-controls.md)

- [Agregar controles comunes a un cuadro de diálogo](using-common-controls-in-a-dialog-box.md)

- [Derivar un control de un control estándar de Windows](deriving-controls-from-a-standard-control.md)

- [Acceso a los controles de cuadro de diálogo con seguridad de tipos](type-safe-access-to-controls-in-a-dialog-box.md)

- [Recibir mensajes de notificación de los controles comunes](receiving-notification-from-common-controls.md)

- [Muestras](common-control-sample-list.md)

Para obtener información sobre los controles comunes de Windows en el Windows SDK, vea [controles comunes](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](user-interface-elements-mfc.md)<br/>
[Editor de cuadros de diálogo](../windows/dialog-editor.md)
