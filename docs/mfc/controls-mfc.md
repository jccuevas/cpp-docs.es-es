---
title: Controles (MFC) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd841b6bc3c55ed58db101c6226bbc24819b248f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="controls-mfc"></a>Controles (MFC)
Los controles de formularios son objetos con los que pueden interactuar los usuarios para escribir o manipular datos. Aparecen normalmente en los cuadros de diálogo o en las barras de herramientas. En esta familia de temas se abordan tres clases principales de controles:  
  
-   Controles comunes de Windows, como los controles dibujados por el propietario  
  
-   Controles ActiveX  
  
-   Otras clases de controles proporcionadas por la biblioteca MFC (Microsoft Foundation Class)  
  
## <a name="windows-common-controls"></a>Controles comunes de Windows  
 El sistema operativo Windows siempre ha proporcionado varios controles comunes de Windows. Estos objetos de control se pueden programar y el editor de cuadros de diálogo de Visual C++ admite agregarlos a los cuadros de diálogo. Las biblioteca MFC (Microsoft Foundation Class) proporciona clases que encapsulan cada uno de estos controles, como se muestra en la tabla [Controles comunes y clases MFC de Windows](#_core_windows_common_controls_and_mfc_classes). (Para algunos elementos de la tabla hay temas relacionados que los describen más detalladamente. Para los controles que no tienen temas relacionados, vea la documentación de la clase MFC).  
  
 La clase [CWnd](../mfc/reference/cwnd-class.md) es la clase base de todas las clases de ventana, incluidas todas las clases de control. 
  
## <a name="activex-controls"></a>Controles ActiveX  
 Los controles ActiveX, antes conocidos como controles OLE, se pueden utilizar en cuadros de diálogo en las aplicaciones para Windows o en páginas HTML en World Wide Web. Para obtener más información, vea [Controles ActiveX MFC](../mfc/mfc-activex-controls.md).  
  
## <a name="other-mfc-control-classes"></a>Otras clases de controles MFC  
 Además de las clases que encapsulan todos los controles comunes de Windows y que admiten la programación de controles ActiveX propios (o el uso de controles ActiveX suministrados por otros), MFC proporciona sus propias clases de controles:  
  
-   [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
  
-   [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
  
-   [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
  
##  <a name="_core_finding_information_about_windows_common_controls"></a> Buscar información sobre los controles comunes de Windows  
 En la tabla siguiente se describe brevemente cada uno de los controles comunes de Windows y se incluye la clase contenedora MFC del control.  
  
### <a name="_core_windows_common_controls_and_mfc_classes"></a>  Controles comunes y clases MFC de Windows  
  
|Control|clase MFC|Descripción|¿Nuevo en Windows 95|  
|-------------|---------------|-----------------|------------------------|  
|[animación](../mfc/using-canimatectrl.md)|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Muestra cuadros sucesivos de un clip de vídeo AVI|Sí|  
|botón|[CButton](../mfc/reference/cbutton-class.md)|Botones de comando que producen una acción; también se utilizan para las casillas, los botones de radio y los cuadros de grupo|No|  
|cuadro combinado|[CComboBox](../mfc/reference/ccombobox-class.md)|Combinación de un cuadro de edición y un cuadro de lista|No|  
|[selector de fecha y hora](../mfc/using-cdatetimectrl.md)|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|Permite elegir un valor de fecha y hora concreto|Sí|  
|cuadro de edición|[CEdit](../mfc/reference/cedit-class.md)|Cuadros para escribir texto|No|  
|[cuadro combinado extendido](../mfc/using-ccomboboxex.md)|[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)|Un control de cuadro combinado con la capacidad de mostrar imágenes|Sí|  
|[header](../mfc/using-cheaderctrl.md)|[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)|Botón que aparece sobre una columna de texto; controla el ancho del texto mostrado|Sí|  
|[tecla de acceso rápido](../mfc/using-chotkeyctrl.md)|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Ventana que permite crear una “tecla de acceso rápido” para realizar una acción rápidamente|Sí|  
|[lista de imágenes](../mfc/using-cimagelist.md)|[CImageList](../mfc/reference/cimagelist-class.md)|Colección de imágenes que se utilizan para administrar conjuntos grandes de iconos o de mapas de bits (la lista de imágenes no es realmente un control; admite las listas utilizadas por otros controles)|Sí|  
|[lista](../mfc/using-clistctrl.md)|[CListCtrl](../mfc/reference/clistctrl-class.md)|Ventana que muestra una lista de texto con iconos|Sí|  
|cuadro de lista|[CListBox](../mfc/reference/clistbox-class.md)|Cuadro que contiene una lista de cadenas|No|  
|[calendario mensual](../mfc/using-cmonthcalctrl.md)|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|Control que muestra información de fecha|Sí|  
|[progreso](../mfc/using-cprogressctrl.md)|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Ventana que indica el progreso de una operación prolongada|Sí|  
|[rebar](../mfc/using-crebarctrl.md)|[CRebarCtrl](../mfc/reference/crebarctrl-class.md)|Barra de herramientas que puede contener ventanas secundarias adicionales en forma de controles|Sí|  
|[rich edit](../mfc/using-cricheditctrl.md)|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|Ventana en la que el usuario puede realizar modificación con formato de carácter y de párrafo (vea [Clases relacionadas con los controles rich edit](../mfc/classes-related-to-rich-edit-controls.md))|Sí|  
|barra de desplazamiento|[CScrollBar](../mfc/reference/cscrollbar-class.md)|Barra de desplazamiento utilizada como control dentro de un cuadro de diálogo (no en una ventana)|No|  
|[control deslizante](../mfc/using-csliderctrl.md)|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|Ventana que contiene un control deslizante con marcas de graduación opcionales|Sí|  
|[botón de número](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Par de botones de flecha en los que el usuario puede hacer clic para aumentar o reducir un valor|Sí|  
|texto estático|[CStatic](../mfc/reference/cstatic-class.md)|Texto para etiquetar otros controles|No|  
|[barra de estado](../mfc/using-cstatusbarctrl.md)|[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)|Ventana para mostrar información de estado, similar a la clase MFC `CStatusBar`|Sí|  
|[pestaña](../mfc/using-ctabctrl.md)|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Análoga a los divisores de un bloc de notas; se usa en "cuadros de diálogo de pestaña" o en hojas de propiedades|Sí|  
|[toolbar](../mfc/using-ctoolbarctrl.md)|[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)|Ventana con botones que generan comandos, similares a la clase MFC `CToolBar`|Sí|  
|[información sobre herramientas](../mfc/using-ctooltipctrl.md)|[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)|Pequeña ventana emergente que describe el propósito de un botón de la barra de herramientas o de otra herramienta|Sí|  
|[árbol](../mfc/using-ctreectrl.md)|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Ventana que muestra una lista jerárquica de elementos|Sí|  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   Un control individual: vea la tabla [Controles comunes de Windows y clases MFC](#_core_windows_common_controls_and_mfc_classes) en este tema para obtener vínculos a todos los controles.  
  
-   [Crear y utilizar controles](../mfc/making-and-using-controls.md)  
  
-   [Utilizar el editor de cuadros de diálogo para agregar controles](../mfc/using-the-dialog-editor-to-add-controls.md)  
  
-   [Agregar controles a un cuadro de diálogo a mano](../mfc/adding-controls-by-hand.md)  
  
-   [Derivar clases de control de las clases de control MFC](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [Utilizar los controles comunes como ventanas secundarias](../mfc/using-a-common-control-as-a-child-window.md)  
  
-   [Notificaciones de los controles comunes](../mfc/receiving-notification-from-common-controls.md)  
  
-   [Agregar controles comunes a un cuadro de diálogo](../mfc/using-common-controls-in-a-dialog-box.md)  
  
-   [Derivar un control de un control estándar de Windows](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [Acceso a los controles de cuadro de diálogo con seguridad de tipos](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [Recibir mensajes de notificación de los controles comunes](../mfc/receiving-notification-from-common-controls.md)  
  
-   [Muestras](../mfc/common-control-sample-list.md)  
  
 Para obtener información acerca de los controles comunes de Windows en el SDK de Windows, vea [controles comunes](http://msdn.microsoft.com/library/windows/desktop/bb775493).  
  
## <a name="see-also"></a>Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [Editor de cuadros de diálogo](../windows/dialog-editor.md)

