---
title: "Clases de control | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.control"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "botones, clases de controles MFC"
  - "clases de controles"
  - "clases de controles, MFC"
  - "controles [C++], clases de controles MFC"
  - "controles [MFC]"
  - "cuadros de lista, clases de controles MFC"
  - "controles de presentación estáticos"
  - "texto, controles para entrada"
  - "datos proporcionados por el usuario, clases de controles MFC"
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases de control encapsulan una gran variedad de controles estándar de Windows que van desde los controles de texto estático a los controles de árbol.  Además, MFC proporciona algunos nuevos controles, como botones con mapas de bits y las barras de controles.  
  
 Controles cuyos nombres de clase acaban en “**CTRL**” estaban nuevo en la versión 3.51 de Windows 95 y Windows NT.  
  
## Controles de presentación estáticos  
 [CStatic](../mfc/reference/cstatic-class.md)  
 Una ventana de la estático\-pantalla.  Los controles estáticos se utilizan para etiquetar, cuadro, o para separar otros controles en un cuadro de diálogo o una ventana.  También pueden mostrar imágenes gráficas en lugar de texto o un cuadro.  
  
## Controles de texto  
 [CEdit](../mfc/reference/cedit-class.md)  
 Una ventana del control de texto modificable.  Los controles de edición se utilizan para aceptar entrada textual del usuario.  
  
 [CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)  
 Admite un cuadro de edición para manipular una dirección de \(IP\) de protocolo de Internet.  
  
 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)  
 Un control en el que el usuario puede escribir y modificar texto.  A diferencia del control encapsulado en `CEdit`, un control rich edit admite el carácter y formato de párrafo y objetos OLE.  
  
## Controles que representan números  
 [CSliderCtrl](../mfc/reference/csliderctrl-class.md)  
 Un control que contiene un control deslizante, que el usuario se desplaza para seleccionar un valor o un conjunto de valores.  
  
 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)  
 Un par de botones de flecha que el usuario puede hacer clic para aumentar o reducir un valor.  
  
 [CProgressCtrl](../mfc/reference/cprogressctrl-class.md)  
 Muestra un rectángulo que se llena gradualmente de izquierda a derecha para indicar el progreso de una operación.  
  
 [CScrollBar](../mfc/reference/cscrollbar-class.md)  
 Una ventana del control de barra de desplazamiento.  La clase proporciona la funcionalidad de una barra de desplazamiento, para su uso como un control en un cuadro de diálogo o una ventana, a través de los que el usuario puede especificar una posición dentro de un intervalo.  
  
## Botones  
 [CButton](../mfc/reference/cbutton-class.md)  
 Una ventana del control de botón.  La clase proporciona una interfaz de programación para un botón de comando, una casilla, o un botón de radio en un cuadro de diálogo o una ventana.  
  
 [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
 Un botón con un mapa de bits en lugar de una leyenda de texto.  
  
## Listas  
 [CListBox](../mfc/reference/clistbox-class.md)  
 Una ventana del control de cuadro de lista.  Un cuadro de lista muestra una lista de elementos que el usuario pueda ver y seleccione.  
  
 [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
 Proporciona la funcionalidad de un cuadro de lista de Windows; permite al usuario mueva elementos de cuadro de lista, como nombres de archivo y literales de cadena, del cuadro de lista.  Los cuadros de lista con esta función son útiles para una lista de elementos en un orden distinto de alfabético, como nombres de ruta de acceso de inclusión o archivos de un proyecto.  
  
 [CComboBox](../mfc/reference/ccombobox-class.md)  
 Una ventana de control combobox.  Un cuadro combinado se compone de un control de edición más un cuadro de lista.  
  
 [CComboBoxEx](../mfc/reference/ccomboboxex-class.md)  
 Extiende el control de cuadro combinado proporcionando compatibilidad con las listas de imágenes.  
  
 [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
 Muestra una lista de elementos con las casillas, que el usuario puede comprobar o borrar, junto a cada elemento.  
  
 [CListCtrl](../mfc/reference/clistctrl-class.md)  
 Muestra una colección de elementos, cada uno que consta de un icono y una etiqueta, de manera similar al panel derecho del Explorador de archivos.  
  
 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)  
 Muestra una lista jerárquica de iconos y de una manera similar organizada etiquetas al panel izquierdo del Explorador de archivos.  
  
## Barras de herramientas y barras de estado  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 Proporciona la funcionalidad del control de barra de herramientas común de Windows.  La mayoría de los programas MFC utilizan [CToolBar](../mfc/reference/ctoolbar-class.md) en lugar de esta clase.  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 Una ventana horizontal, divide normalmente en los paneles, donde una aplicación puede mostrar información de estado.  La mayoría de los programas MFC utilizan [CStatusBar](../mfc/reference/cstatusbar-class.md) en lugar de esta clase.  
  
## Controles diferentes  
 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)  
 Muestra un clip de vídeo simple.  
  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 Una pequeña ventana emergente que muestra una única línea de texto que describe el propósito de una herramienta de una aplicación.  
  
 [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)  
 Admite un control de edición extendido, o un control de interfaz simple de calendario, que permite que un usuario elige una fecha concreta o valor de hora.  
  
 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)  
 Títulos o etiquetas de se muestra para las columnas.  
  
 [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)  
 Admite un control de interfaz simple de calendario que permita a un usuario seleccionar una fecha.  
  
 [CTabCtrl](../mfc/reference/ctabctrl-class.md)  
 Un control con pestañas en las que el usuario puede hacer clic, análogas a los divisores de un bloc de notas.  
  
 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)  
 Permite al usuario para crear una combinación de teclas de acceso rápido, que el usuario puede presionar para realizar una acción rápidamente.  
  
 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)  
 Genera texto anotado e inicia aplicaciones adecuadas cuando el usuario hace clic en el vínculo incrustado.  
  
 [CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)  
 Proporciona la funcionalidad del control ActiveX de WebBrowser en una ventana de MFC.  
  
## Clases relacionadas  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 Proporciona la funcionalidad de la lista de imágenes de Windows.  Las listas de imágenes se utilizan con los controles de lista y los controles de árbol.  También pueden utilizar para almacenar y almacenar un conjunto de mapas de bits mismo\- ordenados.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 La clase base para todas las vistas asociado a los controles de Windows.  Las vistas basadas en los controles son descritas debajo.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Una vista que contenga un control de edición estándar de Windows.  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 Una vista que contenga un control de edición amplio de Windows.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Una vista que contenga un control de lista de Windows.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Una vista que contiene un control de árbol de Windows.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)