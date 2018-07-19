---
title: Las clases de control | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.control
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffd7b3b7d2eb9db68fd61ac693c65d87b2ee62d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358656"
---
# <a name="control-classes"></a>Clases de control
Clases de controles encapsulan una amplia variedad de controles de Windows estándar comprendido entre controles de texto estático y controles de árbol. Además, MFC proporciona algunos controles nuevos, incluidos los botones de barras de control y mapas de bits.  
  
 Los controles cuyos nombres de clase terminan en "**Ctrl**" que son nuevos en Windows 95 y Windows NT versión 3.51.  
  
## <a name="static-display-controls"></a>Controles de presentación estáticos  
 [CStatic](../mfc/reference/cstatic-class.md)  
 Una ventana de visualización de estático. Controles estáticos se utilizan para etiquetar, cuadro o separado de otros controles en una ventana o un cuadro de diálogo. También puede mostrar imágenes gráficas en lugar de texto o un cuadro.  
  
## <a name="text-controls"></a>Controles de texto  
 [CEdit](../mfc/reference/cedit-class.md)  
 Una ventana de control de texto editable. Editar controles se usan para aceptar la entrada de texto del usuario.  
  
 [CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)  
 Admite un cuadro de edición para manipular una dirección de protocolo de Internet (IP).  
  
 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)  
 Un control en el que el usuario puede escribir y editar texto. A diferencia del control encapsulado en `CEdit`, un control rich edit admite caracteres y el formato de párrafo y objetos OLE.  
  
## <a name="controls-that-represent-numbers"></a>Controles que representan números  
 [CSliderCtrl](../mfc/reference/csliderctrl-class.md)  
 Un control que contiene un control deslizante, que el usuario se mueve al seleccionar un valor o un conjunto de valores.  
  
 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)  
 Un par de botones de flecha el usuario puede hacer clic para incrementar o disminuir un valor.  
  
 [CProgressCtrl](../mfc/reference/cprogressctrl-class.md)  
 Muestra un rectángulo que se rellena gradualmente de izquierda a derecha para indicar el progreso de una operación.  
  
 [CScrollBar](../mfc/reference/cscrollbar-class.md)  
 Una ventana de control de barra de desplazamiento. La clase proporciona la funcionalidad de una barra de desplazamiento, para su uso como un control en un cuadro de diálogo o ventana, a través del cual el usuario puede especificar una posición dentro de un intervalo.  
  
## <a name="buttons"></a>Botones  
 [CButton](../mfc/reference/cbutton-class.md)  
 Una ventana de control de botón. La clase proporciona una interfaz de programación para un botón de comando, la casilla de verificación o el botón de radio en una ventana o un cuadro de diálogo.  
  
 [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
 Un botón con un mapa de bits en lugar de una leyenda de texto.  
  
## <a name="lists"></a>Listas  
 [CListBox](../mfc/reference/clistbox-class.md)  
 Una ventana de control de cuadro de lista. Un cuadro de lista muestra una lista de elementos que puede ver y seleccionar el usuario.  
  
 [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
 Proporciona la funcionalidad de un cuadro de lista de Windows; permite al usuario mover elementos de cuadro de lista, como literales de cadena y los nombres de archivo, en el cuadro de lista. Cuadros de lista con esta funcionalidad son útiles para una lista de elementos en un orden que no sea alfabético, como incluir rutas o archivos en un proyecto.  
  
 [CComboBox](../mfc/reference/ccombobox-class.md)  
 Una ventana de control de cuadro combinado. Un cuadro combinado se compone de un control de edición más de un cuadro de lista.  
  
 [CComboBoxEx](../mfc/reference/ccomboboxex-class.md)  
 Extiende el control de cuadro combinado proporcionando compatibilidad con las listas de imágenes.  
  
 [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
 Muestra una lista de elementos con las casillas de verificación, que el usuario puede activar o desactivar, junto a cada elemento.  
  
 [CListCtrl](../mfc/reference/clistctrl-class.md)  
 Muestra una colección de elementos, cada uno de los que se compone de un icono y una etiqueta, de forma similar en el panel derecho del explorador de archivos.  
  
 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)  
 Muestra una lista jerárquica de los iconos y etiquetas organizadas de forma similar al panel izquierdo del explorador de archivos.  
  
## <a name="toolbars-and-status-bars"></a>Barras de herramientas y barras de estado  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 Proporciona la funcionalidad del control de barra de herramientas común de Windows. La mayoría de MFC programas usan [CToolBar](../mfc/reference/ctoolbar-class.md) en lugar de esta clase.  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 Ventana horizontal, que normalmente se divide en paneles, en el que una aplicación puede mostrar información de estado. La mayoría de MFC programas usan [CStatusBar](../mfc/reference/cstatusbar-class.md) en lugar de esta clase.  
  
## <a name="miscellaneous-controls"></a>Varios controles  
 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)  
 Muestra un clip de vídeo simple.  
  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 Una pequeña ventana emergente que muestra una sola línea de texto que describe el propósito de una herramienta de una aplicación.  
  
 [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)  
 Admite un control de edición extendido o un control de interfaz de calendario simple, que permite que un usuario puede elegir una fecha concreta o el valor de tiempo.  
  
 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)  
 Muestra títulos o etiquetas de columnas.  
  
 [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)  
 Admite un control de interfaz de calendario simple que permite al usuario seleccionar una fecha.  
  
 [CTabCtrl](../mfc/reference/ctabctrl-class.md)  
 Un control con pestañas en el que el usuario puede hacer clic, análogo a los divisores de un bloc de notas.  
  
 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)  
 Permite al usuario crear una combinación de teclas de acceso rápida, que el usuario puede presionar para realizar una acción rápidamente.  
  
 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)  
 Representa el texto de marcado telefónico e inicia aplicaciones adecuadas cuando el usuario hace clic en el vínculo incrustado.  
  
 [CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)  
 Proporciona la funcionalidad del control ActiveX de WebBrowser en una ventana de MFC.  
  
## <a name="related-classes"></a>Clases relacionadas  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 Proporciona la funcionalidad de la lista de imágenes de Windows. Se utilizan listas de imágenes con controles de lista y controles de árbol. Pueden usarse para almacenar y archivar un conjunto de mapas de bits mismo tamaño.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 La clase base para todas las vistas asociadas con los controles de Windows. Las vistas en función de los controles se describen a continuación.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Control de edición de una vista que contiene un estándar de Windows.  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 Control de edición de una vista que contiene un completo de Windows.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Una vista que contiene un control de lista de Windows.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Una vista que contiene un control de árbol de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

