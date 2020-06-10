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
ms.openlocfilehash: 277802bff3e4833396c4bf114ff8880fcd26343d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623002"
---
# <a name="control-classes"></a>Clases de control

Las clases de control encapsulan una amplia variedad de controles estándar de Windows que van desde controles de texto estático hasta controles de árbol. Además, MFC proporciona algunos controles nuevos, incluidos botones con mapas de bits y barras de control.

Los controles cuyos nombres de clase terminan en "**Ctrl**" eran nuevos en Windows 95 y Windows NT versión 3,51.

## <a name="static-display-controls"></a>Controles de presentación estáticos

[CStatic](reference/cstatic-class.md)<br/>
Una ventana de presentación estática. Los controles estáticos se utilizan para etiquetar, cuadro o separar otros controles en un cuadro de diálogo o ventana. También pueden mostrar imágenes gráficas en lugar de texto o un cuadro.

## <a name="text-controls"></a>Controles de texto

[CEdit](reference/cedit-class.md)<br/>
Una ventana de control de texto modificable. Los controles de edición se usan para aceptar la entrada de texto del usuario.

[CIPAddressCtrl](reference/cipaddressctrl-class.md)<br/>
Admite un cuadro de edición para manipular una dirección de protocolo de Internet (IP).

[CRichEditCtrl](reference/cricheditctrl-class.md)<br/>
Un control en el que el usuario puede escribir y editar texto. A diferencia del control encapsulado en `CEdit` , un control Rich Edit admite el formato de caracteres y párrafos y objetos OLE.

## <a name="controls-that-represent-numbers"></a>Controles que representan números

[CSliderCtrl](reference/csliderctrl-class.md)<br/>
Un control que contiene un control deslizante, que el usuario mueve para seleccionar un valor o un conjunto de valores.

[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)<br/>
Un par de botones de flecha en los que el usuario puede hacer clic para aumentar o disminuir un valor.

[CProgressCtrl](reference/cprogressctrl-class.md)<br/>
Muestra un rectángulo que se rellena gradualmente de izquierda a derecha para indicar el progreso de una operación.

[CScrollBar](reference/cscrollbar-class.md)<br/>
Una ventana de control de barra de desplazamiento. La clase proporciona la funcionalidad de una barra de desplazamiento, para su uso como un control en un cuadro de diálogo o ventana, a través de la cual el usuario puede especificar una posición dentro de un intervalo.

## <a name="buttons"></a>Botones

[CButton](reference/cbutton-class.md)<br/>
Una ventana de control de botón. La clase proporciona una interfaz de programación para un botón de inserción, casilla o botón de radio en un cuadro de diálogo o una ventana.

[CBitmapButton](reference/cbitmapbutton-class.md)<br/>
Un botón con un mapa de bits en lugar de un título de texto.

## <a name="lists"></a>Listas

[CListBox](reference/clistbox-class.md)<br/>
Una ventana de control de cuadro de lista. Un cuadro de lista muestra una lista de elementos que el usuario puede ver y seleccionar.

[CDragListBox](reference/cdraglistbox-class.md)<br/>
Proporciona la funcionalidad de un cuadro de lista de Windows. permite al usuario desplace los elementos del cuadro de lista, como nombres de archivo y literales de cadena, dentro del cuadro de lista. Los cuadros de lista con esta funcionalidad son útiles para una lista de elementos en un orden distinto del alfabético, como incluir rutas de nombres o archivos en un proyecto.

[CComboBox](reference/ccombobox-class.md)<br/>
Una ventana de control de cuadro combinado. Un cuadro combinado consta de un control de edición y un cuadro de lista.

[CComboBoxEx](reference/ccomboboxex-class.md)<br/>
Extiende el control de cuadro combinado proporcionando compatibilidad con las listas de imágenes.

[CCheckListBox](reference/cchecklistbox-class.md)<br/>
Muestra una lista de elementos con casillas, que el usuario puede activar o desactivar, junto a cada elemento.

[CListCtrl](reference/clistctrl-class.md)<br/>
Muestra una colección de elementos, cada uno de los cuales consta de un icono y una etiqueta, de forma similar al panel derecho del explorador de archivos.

[CTreeCtrl](reference/ctreectrl-class.md)<br/>
Muestra una lista jerárquica de iconos y etiquetas organizadas de forma similar al panel izquierdo del explorador de archivos.

## <a name="toolbars-and-status-bars"></a>Barras de herramientas y barras de estado

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
Proporciona la funcionalidad del control de barra de herramientas común de Windows. La mayoría de los programas MFC usan [CToolBar](reference/ctoolbar-class.md) en lugar de esta clase.

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
Una ventana horizontal, normalmente dividida en paneles, en la que una aplicación puede mostrar información de estado. La mayoría de los programas MFC utilizan [CStatusBar](reference/cstatusbar-class.md) en lugar de esta clase.

## <a name="miscellaneous-controls"></a>Controles varios

[CAnimateCtrl](reference/canimatectrl-class.md)<br/>
Muestra un clip de vídeo simple.

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
Pequeña ventana emergente que muestra una sola línea de texto que describe el propósito de una herramienta en una aplicación.

[CDateTimeCtrl](reference/cdatetimectrl-class.md)<br/>
Admite un control de edición extendido o un control de interfaz de calendario simple que permite al usuario elegir un valor de fecha u hora específico.

[CHeaderCtrl](reference/cheaderctrl-class.md)<br/>
Muestra títulos o etiquetas para las columnas.

[CMonthCalCtrl](reference/cmonthcalctrl-class.md)<br/>
Admite un control de interfaz de calendario simple que permite al usuario seleccionar una fecha.

[CTabCtrl](reference/ctabctrl-class.md)<br/>
Un control con pestañas en las que el usuario puede hacer clic, análogo a los divisores de un bloc de notas.

[CHotKeyCtrl](reference/chotkeyctrl-class.md)<br/>
Permite al usuario crear una combinación de teclas de acceso rápido, que el usuario puede pulsar para realizar una acción rápidamente.

[CLinkCtrl](reference/clinkctrl-class.md)<br/>
Representa el texto marcado y inicia las aplicaciones adecuadas cuando el usuario hace clic en el vínculo incrustado.

[CHtmlEditCtrl](reference/chtmleditctrl-class.md)<br/>
Proporciona la funcionalidad del control ActiveX de WebBrowser en una ventana de MFC.

## <a name="related-classes"></a>Clases relacionadas

[CImageList](reference/cimagelist-class.md)<br/>
Proporciona la funcionalidad de la lista de imágenes de Windows. Las listas de imágenes se utilizan con controles de lista y de árbol. También se pueden usar para almacenar y archivar un conjunto de mapas de bits con el mismo tamaño.

[CCtrlView](reference/cctrlview-class.md)<br/>
La clase base para todas las vistas asociadas a controles de Windows. A continuación se describen las vistas basadas en controles.

[CEditView](reference/ceditview-class.md)<br/>
Una vista que contiene un control de edición estándar de Windows.

[CRichEditView](reference/cricheditview-class.md)<br/>
Una vista que contiene un control Rich Edit de Windows.

[CListView](reference/clistview-class.md)<br/>
Una vista que contiene un control de lista de Windows.

[CTreeView](reference/ctreeview-class.md)<br/>
Una vista que contiene un control de árbol de Windows.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
