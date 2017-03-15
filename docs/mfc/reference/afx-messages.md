---
title: "Mensajes AFX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SB_LINELEFT"
  - "SB_THUMBTRACK"
  - "AFX_TOOLTIP_TYPE_EDIT"
  - "AFX_WM_ON_HSCROLL"
  - "SB_PAGERIGHT"
  - "AFX_WM_RESETPROMPT"
  - "AFX_WM_CHANGE_RIBBON_CATEGORY"
  - "AFX_TOOLTIP_TYPE_MINIFRAME"
  - "AFX_WM_CUSTOMIZETOOLBAR"
  - "AFX_WM_CHANGE_ACTIVE_TAB"
  - "AFX_WM_ACCGETOBJECT"
  - "AFX_WM_TOOLBARMENU"
  - "AFX_TOOLTIP_TYPE_DOCKBAR"
  - "AFX_WM_CUSTOMIZEHELP"
  - "AFX_WM_ON_GET_TAB_TOOLTIP"
  - "AFX_WM_ON_RIBBON_CUSTOMIZE"
  - "AFX_WM_ON_DRAGCOMPLETE"
  - "AFX_WM_RESETTOOLBAR"
  - "AFX_WM_ON_MOVETOTABGROUP"
  - "AFX_WM_CHECKEMPTYMINIFRAME"
  - "AFX_WM_GETDOCUMENTCOLORS"
  - "SB_RIGHT"
  - "AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU"
  - "AFX_WM_ACCGETSTATE"
  - "SB_PAGELEFT"
  - "SB_ENDSCROLL"
  - "AFX_WM_ON_CANCELTABMOVE"
  - "AFX_TOOLTIP_TYPE_TAB"
  - "AFX_WM_WINDOW_HELP"
  - "AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM"
  - "AFX_WM_SHOWREGULARMENU"
  - "AFX_TOOLTIP_TYPE_TOOLBAR"
  - "AFX_WM_CHANGE_CURRENT_FOLDER"
  - "AFX_WM_UPDATETOOLTIPS"
  - "AFX_WM_ON_MOVE_TAB"
  - "AFX_WM_CHANGING_ACTIVE_TAB"
  - "AFX_WM_RESETMENU"
  - "AFX_WM_GETDRAGBOUNDS"
  - "AFX_WM_RESETCONTEXTMENU"
  - "AFX_TOOLTIP_TYPE_BUTTON"
  - "AFX_WM_ON_CLOSEPOPUPWINDOW"
  - "AFX_TOOLTIP_TYPE_TOOLBOX"
  - "AFX_WM_CHANGEVISUALMANAGER"
  - "SB_LINERIGHT"
  - "AFX_WM_ON_RENAME_TAB"
  - "AFX_TOOLTIP_TYPE_DEFAULT"
  - "AFX_WM_ON_TABGROUPMOUSEMOVE"
  - "SB_LEFT"
  - "AFX_WM_DELETETOOLBAR"
  - "AFX_WM_PROPERTY_CHANGED"
  - "AFX_TOOLTIP_TYPE_ALL"
  - "AFX_WM_ACCHITTEST"
  - "AFX_WM_ON_AFTER_SHELL_COMMAND"
  - "AFX_WM_ON_PRESS_CLOSE_BUTTON"
  - "AFX_WM_RESETKEYBOARD"
  - "AFX_WM_ON_MOVETABCOMPLETE"
  - "AFX_WM_CREATETOOLBAR"
  - "SB_THUMBPOSITION"
  - "AFX_WM_POSTSETPREVIEWFRAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mensajes AFX"
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# Mensajes AFX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estos mensajes se utilizan en MFC.  
  
## Mensajes  
 La tabla siguiente se enumeran los mensajes que se utilizan en la biblioteca MFC:  
  
||||||  
|-|-|-|-|-|  
|Mensaje|Descripción|\[in\] `wParam`|`lParam` \(los parámetros Todo se \[in\] a menos que se indique lo contrario.\)|Valor devuelto|  
|AFX\_WM\_ACCGETOBJECT|No usado.|No usado.|No es aplicable|No es aplicable|  
|AFX\_WM\_ACCGETSTATE|Se utiliza para la compatibilidad con la accesibilidad.  Enviar este mensaje a `CMFCPopupMenu` o a `CMFCRibbonPanelMenu` recuperar el estado del elemento actual.|Índice del elemento, que puede ser un botón de menú o un separador.|No usado.|El estado del elemento.  Es \-1 si el índice no es válido, 0 si el botón de menú no tiene ningún atributo especial.  Si no es una combinación de los siguientes indicadores:<br /><br /> TBBS\_DISABLED – el elemento está deshabilitado<br /><br /> TBBS\_CHECKED – se comprueba el elemento<br /><br /> TBBS\_BUTTON – el elemento es un mismo botón estándar<br /><br /> TBBS\_PRESSED – se presiona el botón<br /><br /> TBBS\_INDETERMINATE – estado undefined<br /><br /> TBBS\_SEPARATOR \- en lugar de un botón de menú, este elemento forma una separación entre otros elementos de menú|  
|AFX\_WM\_CHANGE\_ACTIVE\_TAB|El marco envía este mensaje al control de tamaño variable de barra de control.  Procesar este mensaje para recibir notificaciones de los objetos de `CMFCTabCtrl` cuando un usuario cambia una pestaña activa.|El índice de una pestaña.|No usado.|Distinto de cero.|  
|AFX\_WM\_CHANGE\_CURRENT\_FOLDER|El marco envía este mensaje al elemento primario de `CMFCShellListCtrl` cuando el usuario ha cambiado la carpeta actual.|No usado.|No usado.|No usado.|  
|AFX\_WM\_CHANGEVISUALMANAGER|El marco envía este mensaje a todas las ventanas de marco cuando el usuario cambia el administrador Visual actual.  En respuesta a este mensaje, una ventana de marco actualiza su región y ajusta otros parámetros según sea necesario.  Puede procesar el mensaje de AFX\_WM\_CHANGEVISUALMANAGER en la aplicación si necesita ser notificará este evento.  Debe llamar al controlador de la clase base \(`OnChangeVisualManager`\) para asegurarse de que tiene lugar el procesamiento interno de este evento.|No usado.|No usado.|No usado.|  
|AFX\_WM\_CHANGING\_ACTIVE\_TAB|Enviado al elemento primario del objeto de `CMFCTabCtrl` .  Procesar este mensaje si desea recibir notificaciones de los objetos de `CMFCTabCtrl` cuando un usuario restablece una pestaña.|El índice de tabulación se está activando que.|No usado.|Distinto de cero.|  
|AFX\_WM\_CHECKEMPTYMINIFRAME|Sólo para uso interno.|No es aplicable|No es aplicable|No es aplicable|  
|AFX\_WM\_CREATETOOLBAR|Enviado desde `CMFCToolBarsListPropertyPage` cuando un usuario crea una barra de herramientas nueva durante el proceso de personalización.  Puede procesar este mensaje para crear instancias de un objeto CMFCToolBar\- derivado personalizado.  Si controla este mensaje y crea posee la barra de herramientas, se omitirá la llamada al controlador predeterminado.|No usado.|Un puntero a una cadena que contiene el nombre de la barra de herramientas.|Un puntero a la barra de herramientas recién creada.  NULL indica que la creación de la barra de herramientas se canceló.|  
|AFX\_WM\_CUSTOMIZEHELP|Enviado a la ventana de marco principal de la hoja de propiedades `CMFCToolbarCustomize``Dialog` de personalización cuando el usuario presiona el botón de **Ay&uda** o F1.|Especifica la página activa de la hoja de propiedades de personalización.|Un puntero a un objeto de `CMFCToolbarCustomize` `Dialog`.|Cero|  
|AFX\_WM\_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize` `Dialog` envía este mensaje para notificar el cuadro primario que el usuario está creando una nueva barra de herramientas.|`TRUE` cuando se inicia la personalización, `FALSE` cuando la personalización.|No usado.|Cero|  
|AFX\_WM\_DELETETOOLBAR|Enviado a la ventana de marco principal cuando el usuario está a punto de eliminar una barra de herramientas en el modo de personalización.<br /><br /> Procesar este mensaje para tomar medidas adicionales cuando un usuario elimina una barra de herramientas en modo de personalización.  También debe llamar al controlador predeterminado \(`OnToolbarDelete`\), lo que elimina la barra de herramientas.  El controlador predeterminado devuelve un valor que indica si es posible eliminar la barra de herramientas.|No usado.|Puntero a un objeto de `CMFCToolBar` que se va a eliminar.|Distinto de cero si una barra de herramientas no puede eliminarse; si no 0.|  
|AFX\_WM\_GETDOCUMENTCOLORS|`CMFCColorMenuButton` envía este mensaje en la ventana de marco principal para recuperar los colores del documento.|No usado.|\[in, out\] Puntero a un objeto de `CList<COLORREF, COLORREF>` .|Cero|  
|AFX\_WM\_GETDRAGBOUNDS|Sólo para uso interno.|No es aplicable|No es aplicable|No es aplicable|  
|AFX\_WM\_HIGHLIGHT\_RIBBON\_LIST\_ITEM|Enviado a la ventana de marco principal cuando un usuario resalta un elemento de lista de la cinta de opciones.|Índice del elemento resaltado|Un puntero a `CMFCBaseRibbonElement`|No usado.|  
|AFX\_WM\_ON\_AFTER\_SHELL\_COMMAND|Enviados a un elemento primario de `CMFCShellListCtrl` o controles de `CMFCShellTreeCtrl` cuando un usuario termina de ejecutar un comando de shell.|El identificador de comando que el usuario ha ejecutado|No usado.|Si los procesos de aplicación este mensaje, se devuelve cero.|  
|AFX\_WM\_ON\_BEFORE\_SHOW\_RIBBON\_ITEM\_MENU|El marco envía este mensaje al elemento primario de la cinta de opciones antes de enviar el menú emergente.  Puede procesar este mensaje y modificar menús emergentes en cualquier momento.|No usado.|Un puntero a `CMFCBaseRibbonElement`|No usado.|  
|AFX\_WM\_ON\_CANCELTABMOVE|Sólo para uso interno.|No es aplicable|No es aplicable||  
|AFX\_WM\_ON\_CHANGE\_RIBBON\_CATEGORY|El marco envía este mensaje al marco principal cuando el usuario cambia la categoría activo del Control ribbon.|No usado.|Un puntero a `CMFCRibbonBar` cuya categoría ha cambiado.|No usado.|  
|AFX\_WM\_ON\_CLOSEPOPUPWINDOW|El marco envía este mensaje para notificar al propietario de `CMFCDesktopAlertWnd` que la ventana está a punto de cerrarla.|No usado.|Un puntero al objeto de `CMFCDesktopAlertWnd` .|No usado.|  
|AFX\_WM\_ON\_DRAGCOMPLETE|Sólo para uso interno.|No es aplicable|No es aplicable|No es aplicable|  
|AFX\_WM\_ON\_GET\_TAB\_TOOLTIP|Enviado a la ventana de marco principal cuando una ventana de la pestaña se va a mostrar la información sobre herramientas de una pestaña, si se habilitan la información sobre herramientas personalizadas.|No usado.|Un puntero a una estructura de `CMFCTabToolTipInfo` .|No usado.|  
|AFX\_WM\_ON\_HSCROLL|Enviado al control de tamaño variable de barra de control.  Procesar este mensaje para recibir notificaciones de los objetos de `CMFCTabCtrl` cuando un evento de desplazamiento aparece en la barra de desplazamiento horizontal con fichas widget.|La palabra de orden inferior especifica un valor de desplazamiento que indica la solicitud de desplazamiento del usuario.  Para obtener más información, vea la tabla más adelante en este tema.|No usado.|Distinto de cero.|  
|AFX\_WM\_ON\_MOVE\_TAB|Enviado al elemento primario de una ventana con fichas cuando un usuario arrastra una pestaña a una nueva posición.|El índice cero\- basado en la ficha en su posición original.|\[out\] El índice cero\- basado de la pestaña en la nueva posición.|Cero|  
|AFX\_WM\_ON\_MOVETABCOMPLETE|Sólo para uso interno.|No es aplicable|No es aplicable|No es aplicable|  
|AFX\_WM\_ON\_MOVETOTABGROUP|Enviado a la ventana de marco principal cuando un usuario mueve una ventana MDI secundaria a partir de un grupo con fichas a otro.|Un identificador de la ventana con fichas \(`CMFCTabCtrl`\) de las que se ha quitado la ventana MDI secundaria.|\[out\] Un identificador de la ventana con fichas \(`CMFCTabCtrl`\) a las que se ha insertado la ventana MDI secundaria.|Se omitirá.|  
|AFX\_WM\_ON\_PRESS\_CLOSE\_BUTTON|Enviados a un elemento primario de `CDockablePane` cuando el usuario hace clic en el botón de **cerrar** en la leyenda de la barra de control.|No usado.|Un puntero a un panel acoplable en el que el usuario hizo clic en el botón de **cerrar** .|`TRUE` si un panel no puede cerrar; si no es FALSE.|  
|AFX\_WM\_ON\_RENAME\_TAB|Enviado al elemento primario de la ventana con fichas cuando el usuario cambió una ficha modificable.|El índice cero\- basado en la ficha cuyo nombre ha cambiado.|\[out\] Un puntero a una cadena que contiene el nuevo nombre de la pestaña.|Distinto de cero si los procesos de aplicación este mensaje; el marco suprimirá la llamada a `CMFCBaseTabCtrl::SetTabLabel`.  Si se devuelve cero, después `CMFCBaseTabCtrl::SetTabLabel` llama el marco.|  
|AFX\_WM\_ON\_RIBBON\_CUSTOMIZE|Enviado al cuadro primario cuando el usuario inicia la personalización.  Procesar este mensaje si desea mostrar dispone del cuadro de diálogo personalización.|No usado.|Un puntero al control de la cinta que se personalizará.|Distinto de cero si los procesos de aplicación este mensaje y muestra su propio cuadro de diálogo personalización.  Si la aplicación devuelve cero, el marco se mostrará el cuadro de diálogo integrado de personalización.|  
|AFX\_WM\_ON\_TABGROUPMOUSEMOVE|Sólo para uso interno.|No es aplicable|No es aplicable|No es aplicable|  
|AFX\_WM\_POSTSETPREVIEWFRAME|Enviados para notificar al marco principal que el usuario cambia el modo de vista previa de impresión|`TRUE` indica que está establecido el modo de vista previa de impresión.  `FALSE` indica que se desactiva el modo de vista previa de impresión.|No usado.|No usado.|  
|AFX\_WM\_PROPERTY\_CHANGED|Enviado al propietario del control de cuadrícula de propiedades \(`CMFCPropertyGridCtrl`\) cuando el usuario cambia el valor de la propiedad seleccionada.|El identificador de control de la lista de propiedades.|Un puntero a la propiedad \(`CMFCProp``ertyGridProperty`\) que cambió.|No usado.|  
|AFX\_WM\_RESETCONTEXTMENU|Enviado a la ventana de marco principal cuando el usuario restablece el menú contextual durante la personalización.|El Id. de recurso de menú contextual.|Un puntero al menú contextual actual, `CMFCPopupMenu`.|No usado.|  
|AFX\_WM\_RESETKEYBOARD|El marco envía este mensaje en la ventana de marco principal cuando el usuario restablece todos los aceleradores de teclado durante la personalización.|No usado.|No usado.|No usado.|  
|AFX\_WM\_RESETMENU|El marco envía este mensaje al propietario de menú \(una ventana de marco\) cuando el usuario restaurar un menú del cuadro de la aplicación durante la personalización|El identificador de recurso de menú|No usado.|No usado.|  
|AFX\_WM\_RESETPROMPT|El marco envía este mensaje cuando el usuario restablece una barra de herramientas de la barra de herramientas personalizar el cuadro de diálogo.  El controlador predeterminado muestra un cuadro de mensaje que pregunta si el usuario desea restaurar la barra de herramientas.|No usado.|No usado.|No usado.|  
|AFX\_WM\_RESETTOOLBAR|Un objeto de `CMFCToolBar` envía este mensaje cuando una barra de herramientas se restaura su estado original, es decir, carga de recursos.  Procesar este mensaje para reinsertar los botones de la barra de herramientas cuyas clases se derivan de `CMFCToolbarButton`.  Para obtener más información, vea `CMFCToolbarComboBoxButton`.|El Id. de recurso de una barra de herramientas cuya restablecieron a estado.|No usado.|Cero|  
|AFX\_WM\_SHOWREGULARMENU|el objeto de`CMFCToolbarMenuButton` envía este mensaje al propietario cuando el usuario hace clic en un botón de menú regular.  Procesar este mensaje cada vez que se usa `CMFCToolbarMenuButton` para mostrar un menú emergente cuando el usuario hace clic en un botón.|El identificador de comando de un botón que envía el mensaje.|Coordenadas de pantalla del cursor.  La palabra de orden inferior especifica la x\-coordenada.  La palabra de alto nivel especifica la y\-coordenada.|No usado.|  
|AFX\_WM\_TOOLBARMENU|Enviado a la ventana de marco principal cuando el usuario suelta el botón secundario del mouse mientras el puntero del mouse se encuentra en el área de cliente o de no cliente de un panel.|No usado.|Coordenadas de la pantalla del puntero del mouse.  La palabra de orden inferior especifica la x\-coordenada.  La palabra de alto nivel especifica la y\-coordenada.|Cero si los procesos de aplicación este mensaje; si no, distinto de cero.|  
|AFX\_WM\_UPDATETOOLTIPS|Enviado a todos los propietarios de información sobre herramientas para indicar que los controles de información sobre herramientas deben ser recreado.|El tipo de control que debe procesar este mensaje.  Vea la tabla más adelante en este tema para obtener una lista de valores posibles.|No usado.|No usado.|  
|AFX\_WM\_WINDOW\_HELP|`CMFCWindowsManagerDialog` envía este mensaje al cuadro primario cuando el usuario hace clic en el botón de **Ay&uda** , o entra en el modo de ayuda haciendo clic en el botón de título de **Ay&uda** o F1.|No usado.|Un puntero a la instancia de `CMFCWindowsManagerDialog`.|No usado.|  
  
 La tabla siguiente se muestran los valores para word insuficiente de parámetro de `lParam` del método de AFX\_WM\_HSCROLL:  
  
|||  
|-|-|  
|Valor|Significado|  
|SB\_ENDSCROLL|El usuario finaliza el desplazamiento.|  
|SB\_LEFT|Los desplazamientos de usuario al superior izquierdo.|  
|SB\_RIGHT|Los desplazamientos de usuario al bajo\- derecho.|  
|SB\_LINELEFT|El usuario se desplaza a la izquierda por una unidad.|  
|SB\_LINERIGHT|Los desplazamientos de usuario derecha por una unidad.|  
|SB\_PAGELEFT|El usuario se desplaza a la izquierda el ancho de la ventana.|  
|SB\_PAGERIGHT|Los desplazamientos de usuario derecha según el ancho de la ventana.|  
|SB\_THUMBPOSITION|El usuario ha arrastrado el cuadro de desplazamiento \(control\) y se libera el botón del mouse.  La palabra de alto nivel indica la posición del cuadro de desplazamiento al final de la operación de arrastre.|  
|SB\_THUMBTRACK|El usuario está arrastrando el cuadro de desplazamiento.  El mensaje de AFX\_WM\_ON\_HSCROLL se envía repetidamente con este valor hasta el usuario suelta el botón del mouse.  La palabra de alto nivel indica la posición en la que se ha arrastrado el cuadro de desplazamiento.|  
  
> [!NOTE]
>  La palabra de alto nivel del parámetro de `lParam` especifica la posición actual del cuadro de desplazamiento si la palabra de orden inferior es SB\_THUMBPOSITION o SB\_THUMBTRACK; si no, esta palabra no se utiliza.  
  
 La tabla siguiente se enumeran los valores de marca para el parámetro de `lParam` de mensajes de AFX\_WM\_UPDATETOOLTIPS:  
  
|||  
|-|-|  
|Marcar|Valor|  
|AFX\_TOOLTIP\_TYPE\_DEFAULT|0x0001|  
|AFX\_TOOLTIP\_TYPE\_TOOLBAR|0x0002|  
|AFX\_TOOLTIP\_TYPE\_TAB|0x0004|  
|AFX\_TOOLTIP\_TYPE\_MINIFRAME|0x0008|  
|AFX\_TOOLTIP\_TYPE\_DOCKBAR|0x0010|  
|AFX\_TOOLTIP\_TYPE\_EDIT|0x0020|  
|AFX\_TOOLTIP\_TYPE\_BUTTON|0x0040|  
|AFX\_TOOLTIP\_TYPE\_TOOLBOX|0x0080|  
|AFX\_TOOLTIP\_TYPE\_ALL|0xFFFF|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)