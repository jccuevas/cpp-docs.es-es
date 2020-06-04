---
title: Clases de control
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
ms.openlocfilehash: 79a71a4660cd49f85726d730c9fad0b2f10f83bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338173"
---
# <a name="control-classes"></a>Clases de control

Clases de control encapsulan una amplia variedad de controles de Windows estándar comprendido entre controles de texto estático y controles de árbol. Además, MFC proporciona algunos controles nuevos, incluidos los botones con barras de control y mapas de bits.

Los controles cuyos nombres de clase terminan en "**Ctrl**" se introdujeron en Windows 95 y Windows NT versión 3.51.

## <a name="static-display-controls"></a>Controles de presentación estáticos

[CStatic](../mfc/reference/cstatic-class.md)<br/>
Una ventana de presentación estática. Controles estáticos se utilizan para etiquetar, o bien separar otros controles en un cuadro de diálogo o ventana. También puede mostrar imágenes gráficas en lugar de texto o un cuadro.

## <a name="text-controls"></a>Controles de texto

[CEdit](../mfc/reference/cedit-class.md)<br/>
Una ventana de control de texto editable. Editar controles se usan para aceptar la entrada de texto del usuario.

[CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)<br/>
Admite un cuadro de edición para manipular una dirección de protocolo de Internet (IP).

[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)<br/>
Un control en el que el usuario puede escribir y editar texto. A diferencia del control encapsulado en `CEdit`, un control rich edit admite caracteres y el formato de párrafo y objetos OLE.

## <a name="controls-that-represent-numbers"></a>Controles que representan números

[CSliderCtrl](../mfc/reference/csliderctrl-class.md)<br/>
Un control que contiene un control deslizante, que el usuario se mueve al seleccionar un valor o conjunto de valores.

[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)<br/>
Un par de botones de flecha el usuario puede hacer clic para aumentar o reducir un valor.

[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)<br/>
Muestra un rectángulo que se rellena gradualmente de izquierda a derecha para indicar el progreso de una operación.

[CScrollBar](../mfc/reference/cscrollbar-class.md)<br/>
Una ventana de control de barra de desplazamiento. La clase proporciona la funcionalidad de una barra de desplazamiento, para su uso como un control en un cuadro de diálogo o ventana, a través del cual el usuario puede especificar una posición dentro de un intervalo.

## <a name="buttons"></a>Botones

[CButton](../mfc/reference/cbutton-class.md)<br/>
Una ventana de control de botón. La clase proporciona una interfaz de programación para un botón de comando, la casilla de verificación o el botón de radio en un cuadro de diálogo o ventana.

[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)<br/>
Botón con un mapa de bits en lugar de una leyenda de texto.

## <a name="lists"></a>Listas

[CListBox](../mfc/reference/clistbox-class.md)<br/>
Una ventana de control de cuadro de lista. Un cuadro de lista muestra una lista de elementos que puede ver y seleccionar el usuario.

[CDragListBox](../mfc/reference/cdraglistbox-class.md)<br/>
Proporciona la funcionalidad de un cuadro de lista de Windows; permite al usuario mover elementos de cuadro de lista, como literales de cadena y los nombres de archivo, en el cuadro de lista. Cuadros de lista con esta funcionalidad son útiles para una lista de elementos en un orden que no sea alfabético, como incluir directorios o archivos en un proyecto.

[CComboBox](../mfc/reference/ccombobox-class.md)<br/>
Una ventana de control de cuadro combinado. Un cuadro combinado consta de un control de edición más de un cuadro de lista.

[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)<br/>
Extiende el control de cuadro combinado proporcionando compatibilidad con las listas de imágenes.

[CCheckListBox](../mfc/reference/cchecklistbox-class.md)<br/>
Muestra una lista de elementos con las casillas de verificación, que el usuario puede activar o desactivar, junto a cada elemento.

[CListCtrl](../mfc/reference/clistctrl-class.md)<br/>
Muestra una colección de elementos, cada uno de los que consta de un icono y una etiqueta, de manera similar en el panel derecho del explorador de archivos.

[CTreeCtrl](../mfc/reference/ctreectrl-class.md)<br/>
Muestra una lista jerárquica de los iconos y las etiquetas que se organizan de forma similar al panel izquierdo del explorador de archivos.

## <a name="toolbars-and-status-bars"></a>Las barras de herramientas y barras de estado

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Proporciona la funcionalidad del control de barra de herramientas común de Windows. La mayoría de MFC programas usan [CToolBar](../mfc/reference/ctoolbar-class.md) en lugar de esta clase.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Una ventana horizontal, que normalmente se divide en paneles, en el que una aplicación puede mostrar información de estado. La mayoría de MFC programas usan [CStatusBar](../mfc/reference/cstatusbar-class.md) en lugar de esta clase.

## <a name="miscellaneous-controls"></a>Varios controles

[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)<br/>
Muestra un clip de vídeo sencillo.

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Una pequeña ventana emergente que muestra una sola línea de texto que describe el propósito de una herramienta en una aplicación.

[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)<br/>
Admite un control de edición extendido o un control de interfaz de calendario simple, que permite al usuario elegir una fecha concreta o el valor de hora.

[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)<br/>
Muestra los títulos o etiquetas para las columnas.

[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)<br/>
Admite un control de interfaz de calendario simple que permite al usuario seleccionar una fecha.

[CTabCtrl](../mfc/reference/ctabctrl-class.md)<br/>
Un control con pestañas en el que el usuario puede hacer clic, análogo a los divisores de un bloc de notas.

[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)<br/>
Permite al usuario crear una combinación de teclas de acceso frecuente, lo que el usuario puede presionar para realizar una acción rápidamente.

[CLinkCtrl](../mfc/reference/clinkctrl-class.md)<br/>
Representa el texto de marcado de seguridad y aplicaciones adecuadas se inicia cuando el usuario hace clic en el vínculo incrustado.

[CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)<br/>
Proporciona la funcionalidad del control ActiveX de WebBrowser en una ventana de MFC.

## <a name="related-classes"></a>Clases relacionadas

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Proporciona la funcionalidad de la lista de imágenes de Windows. Listas de imágenes se usan con los controles de lista y los controles de árbol. También puede usarse para almacenar y archivar un conjunto de mapas de bits mismo tamaño.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
La clase base para todas las vistas asociadas con los controles de Windows. Las vistas en función de los controles se describen a continuación.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Control de edición de una vista que contiene un estándar de Windows.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Control de edición de una vista que contiene un completo de Windows.

[CListView](../mfc/reference/clistview-class.md)<br/>
Una vista que contiene un control de lista de Windows.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Una vista que contiene un control de árbol de Windows.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
