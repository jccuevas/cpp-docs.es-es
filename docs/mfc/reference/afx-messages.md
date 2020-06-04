---
title: mensajes AFX
ms.date: 11/04/2016
f1_keywords:
- SB_LINELEFT
- SB_THUMBTRACK
- AFX_TOOLTIP_TYPE_EDIT
- AFX_WM_ON_HSCROLL
- SB_PAGERIGHT
- AFX_WM_RESETPROMPT
- AFX_WM_CHANGE_RIBBON_CATEGORY
- AFX_TOOLTIP_TYPE_MINIFRAME
- AFX_WM_CUSTOMIZETOOLBAR
- AFX_WM_CHANGE_ACTIVE_TAB
- AFX_WM_ACCGETOBJECT
- AFX_WM_TOOLBARMENU
- AFX_TOOLTIP_TYPE_DOCKBAR
- AFX_WM_CUSTOMIZEHELP
- AFX_WM_ON_GET_TAB_TOOLTIP
- AFX_WM_ON_RIBBON_CUSTOMIZE
- AFX_WM_ON_DRAGCOMPLETE
- AFX_WM_RESETTOOLBAR
- AFX_WM_ON_MOVETOTABGROUP
- AFX_WM_CHECKEMPTYMINIFRAME
- AFX_WM_GETDOCUMENTCOLORS
- SB_RIGHT
- AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU
- AFX_WM_ACCGETSTATE
- SB_PAGELEFT
- SB_ENDSCROLL
- AFX_WM_ON_CANCELTABMOVE
- AFX_TOOLTIP_TYPE_TAB
- AFX_WM_WINDOW_HELP
- AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM
- AFX_WM_SHOWREGULARMENU
- AFX_TOOLTIP_TYPE_TOOLBAR
- AFX_WM_CHANGE_CURRENT_FOLDER
- AFX_WM_UPDATETOOLTIPS
- AFX_WM_ON_MOVE_TAB
- AFX_WM_CHANGING_ACTIVE_TAB
- AFX_WM_RESETMENU
- AFX_WM_GETDRAGBOUNDS
- AFX_WM_RESETCONTEXTMENU
- AFX_TOOLTIP_TYPE_BUTTON
- AFX_WM_ON_CLOSEPOPUPWINDOW
- AFX_TOOLTIP_TYPE_TOOLBOX
- AFX_WM_CHANGEVISUALMANAGER
- SB_LINERIGHT
- AFX_WM_ON_RENAME_TAB
- AFX_TOOLTIP_TYPE_DEFAULT
- AFX_WM_ON_TABGROUPMOUSEMOVE
- SB_LEFT
- AFX_WM_DELETETOOLBAR
- AFX_WM_PROPERTY_CHANGED
- AFX_TOOLTIP_TYPE_ALL
- AFX_WM_ACCHITTEST
- AFX_WM_ON_AFTER_SHELL_COMMAND
- AFX_WM_ON_PRESS_CLOSE_BUTTON
- AFX_WM_RESETKEYBOARD
- AFX_WM_ON_MOVETABCOMPLETE
- AFX_WM_CREATETOOLBAR
- SB_THUMBPOSITION
- AFX_WM_POSTSETPREVIEWFRAME
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
ms.openlocfilehash: b4ed86c11d3c5b5f1ce38e3146533109f3a6b00d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363597"
---
# <a name="afx-messages"></a>mensajes AFX

Estos mensajes se utilizan en MFC.

## <a name="messages"></a>error de Hadoop

En la tabla siguiente se enumeran los mensajes que se utilizan en la biblioteca MFC:

||||||
|-|-|-|-|-|
|Message|Descripción|[en] *wParam*|*lParam* (Todos los parámetros son [in] a menos que se indique lo contrario.)|Valor devuelto|
|AFX_WM_ACCGETOBJECT|No se usa.|No se usa.|No es aplicable.|No es aplicable.|
|AFX_WM_ACCGETSTATE|Se utiliza para la compatibilidad con la accesibilidad. Envíe este `CMFCPopupMenu` mensaje `CMFCRibbonPanelMenu` a o para recuperar el estado del elemento actual.|Indice de elemento, que podría ser un botón de menú o separador.|No se usa.|El estado del elemento. Es -1 si el índice no es válido, 0 si el botón de menú no tiene atributos especiales. De lo contrario, es una combinación de los siguientes indicadores:<br /><br /> TBBS_DISABLED — el elemento está deshabilitado<br /><br /> TBBS_CHECKED — el elemento está marcado<br /><br /> TBBS_BUTTON — el artículo es un pulsador estándar<br /><br /> TBBS_PRESSED — se pulsa el botón<br /><br /> TBBS_INDETERMINATE — estado indefinido<br /><br /> TBBS_SEPARATOR - en lugar de un botón de menú, este elemento forma una separación entre otros elementos de menú|
|AFX_WM_CHANGE_ACTIVE_TAB|El marco de trabajo envía este mensaje al control de barra de control redimensionable. Procesar este mensaje para `CMFCTabCtrl` recibir notificaciones de objetos cuando un usuario cambia una pestaña activa.|El índice de una pestaña.|No se usa.|Distinto.|
|AFX_WM_CHANGE_CURRENT_FOLDER|El marco de trabajo envía `CMFCShellListCtrl` este mensaje al elemento primario de cuando el usuario ha cambiado la carpeta actual.|No se usa.|No se usa.|No se usa.|
|AFX_WM_CHANGEVISUALMANAGER|El marco de trabajo envía este mensaje a todas las ventanas de marco cuando el usuario cambia el Administrador visual actual. En respuesta a este mensaje, una ventana de marco vuelve a calcular su región y ajusta otros parámetros según sea necesario. Puede procesar el mensaje AFX_WM_CHANGEVISUALMANAGER en la aplicación si necesita recibir una notificación sobre este evento. Debe llamar al controlador`OnChangeVisualManager`de clase base ( ) para asegurarse de que se lleva a cabo el procesamiento interno del marco de trabajo de este evento.|No se usa.|No se usa.|No se usa.|
|AFX_WM_CHANGING_ACTIVE_TAB|Se envía al `CMFCTabCtrl` elemento primario del objeto.  Procesar este mensaje si desea recibir `CMFCTabCtrl` notificaciones de objetos cuando un usuario restablece una pestaña.|El índice de la pestaña que se está activando.|No se usa.|Distinto.|
|AFX_WM_CHECKEMPTYMINIFRAME|Solo para uso interno.|No es aplicable.|No es aplicable.|No es aplicable.|
|AFX_WM_CREATETOOLBAR|Se `CMFCToolBarsListPropertyPage` envía desde cuando un usuario crea una nueva barra de herramientas durante el proceso de personalización. Puede procesar este mensaje para crear instancias de un personalizado CMFCToolBar-objeto derivado. Si controla este mensaje y crea su propia barra de herramientas, omita la llamada al controlador predeterminado.|No se usa.|Puntero a una cadena que contiene el nombre de la barra de herramientas.|Un puntero a la barra de herramientas recién creada. NULL indica que se canceló la creación de la barra de herramientas.|
|AFX_WM_CUSTOMIZEHELP|Se envía a la ventana de `CMFCToolbarCustomize Dialog` marco principal desde la hoja de propiedades de personalización cuando el usuario presiona el botón **Ayuda** o la tecla F1.|Especifica la página activa de la hoja de propiedades de personalización.|Puntero a un objeto `CMFCToolbarCustomize Dialog` .|Cero.|
|AFX_WM_CUSTOMIZETOOLBAR|El `CMFCToolbarCustomize Dialog` envía este mensaje para notificar al marco primario que el usuario está creando una nueva barra de herramientas.|TRUECuando se inicia la personalización, FALSE cuando finaliza la personalización.|No se usa.|Cero.|
|AFX_WM_DELETETOOLBAR|Se envía a la ventana de marco principal cuando el usuario está a punto de eliminar una barra de herramientas en el modo de personalización.<br /><br /> Procesar este mensaje para realizar acciones adicionales cuando un usuario elimina una barra de herramientas en modo de personalización. También debe llamar al`OnToolbarDelete`controlador predeterminado ( ), que elimina la barra de herramientas. El controlador predeterminado devuelve un valor que indica si es posible eliminar la barra de herramientas.|No se usa.|Puntero a `CMFCToolBar` un objeto que se va a eliminar.|Distinto de cero si no se puede eliminar una barra de herramientas; de lo contrario 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton`envía este mensaje a la ventana de marco principal para recuperar los colores del documento.|No se usa.|[adentro, fuera] Puntero a `CList<COLORREF, COLORREF>` un objeto.|Cero.|
|AFX_WM_GETDRAGBOUNDS|Solo para uso interno.|No es aplicable.|No es aplicable.|No es aplicable.|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Se envía a la ventana de marco principal cuando un usuario resalta un elemento de lista de la cinta de opciones.|Indice del elemento resaltado|Un puntero a`CMFCBaseRibbonElement`|No se usa.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Se envía a `CMFCShellListCtrl` `CMFCShellTreeCtrl` un elemento primario o controla cuando un usuario termina de ejecutar un comando de shell.|El ID del comando que el usuario ejecutó|No se usa.|Si la aplicación procesa este mensaje, debe devolver cero.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|El marco de trabajo envía este mensaje al elemento primario de la cinta de opciones antes de que muestre el menú emergente. Puede procesar este mensaje y modificar los menús emergentes en cualquier momento.|No se usa.|Un puntero a`CMFCBaseRibbonElement`|No se usa.|
|AFX_WM_ON_CANCELTABMOVE|Solo para uso interno.|No es aplicable.|No es aplicable.||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|El marco de trabajo envía este mensaje al marco principal cuando el usuario cambia la categoría de control de cinta de opciones activa.|No se usa.|Un puntero `CMFCRibbonBar` a la categoría cuya categoría ha cambiado.|No se usa.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|El marco de trabajo envía `CMFCDesktopAlertWnd` este mensaje para notificar al propietario de que la ventana está a punto de cerrarse.|No se usa.|Un puntero `CMFCDesktopAlertWnd` al objeto.|No se usa.|
|AFX_WM_ON_DRAGCOMPLETE|Solo para uso interno.|No es aplicable.|No es aplicable.|No es aplicable.|
|AFX_WM_ON_GET_TAB_TOOLTIP|Se envía a la ventana de marco principal cuando una ventana de pestaña está a punto de mostrar una información sobre herramientas para una pestaña, si la información sobre herramientas personalizada está habilitada.|No se usa.|Un puntero `CMFCTabToolTipInfo` a una estructura.|No se usa.|
|AFX_WM_ON_HSCROLL|Se envía al control de barra de control redimensionable. Procesar este mensaje para `CMFCTabCtrl` recibir notificaciones de objetos cuando se produce un evento de desplazamiento en la barra de desplazamiento horizontal del widget con pestañas.|La palabra de orden bajo especifica un valor de barra de desplazamiento que indica la solicitud de desplazamiento del usuario.  Para obtener más información, vea la tabla más adelante en este tema.|No se usa.|Distinto.|
|AFX_WM_ON_MOVE_TAB|Se envía al elemento primario de una ventana con fichas cuando un usuario arrastra una pestaña a una nueva posición.|El índice de base cero de la pestaña en su posición original.|[fuera] El índice de base cero de la pestaña en su nueva posición.|Cero.|
|AFX_WM_ON_MOVETABCOMPLETE|Solo para uso interno.|No es aplicable.|No es aplicable.|No es aplicable.|
|AFX_WM_ON_MOVETOTABGROUP|Se envía a la ventana de marco principal cuando un usuario mueve una ventana secundaria MDI de un grupo con fichas a otro.|Identificador de la`CMFCTabCtrl`ventana con pestañas ( ) desde la que se ha quitado la ventana secundaria MDI.|[fuera] Identificador de la`CMFCTabCtrl`ventana con pestañas ( ) en la que se ha insertado la ventana secundaria MDI.|ignorado.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Se envía a `CDockablePane` un elemento primario de cuando el usuario hace clic en el botón **Cerrar** en el título de la barra de control.|No se usa.|Puntero a un panel acoplable en el que el usuario ha haciendo clic en el botón **Cerrar.**|TRUESi no se puede cerrar un panel; de lo contrario FALSO.|
|AFX_WM_ON_RENAME_TAB|Se envía al elemento primario de la ventana con fichas después de que el usuario cambiara el nombre de una pestaña editable.|El índice de base cero de la pestaña renombrada.|[fuera] Puntero a una cadena que contiene el nuevo nombre de tabulación.|Distinto de cero si la aplicación procesa este mensaje; el marco de trabajo `CMFCBaseTabCtrl::SetTabLabel`suprimirá la llamada a .  Si se devuelve `CMFCBaseTabCtrl::SetTabLabel` cero, el marco de trabajo llama a continuación.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Se envía al marco primario cuando el usuario inicia la personalización. Procese este mensaje si desea mostrar su propio cuadro de diálogo de personalización.|No se usa.|Puntero al control de la cinta de opciones que se va a personalizar.|Distinto de cero si la aplicación procesa este mensaje y muestra su propio cuadro de diálogo de personalización. Si la aplicación devuelve cero, el marco de trabajo mostrará el cuadro de diálogo de personalización integrado.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Solo para uso interno.|No es aplicable.|No es aplicable.|No es aplicable.|
|AFX_WM_POSTSETPREVIEWFRAME|Enviado para notificar al marco principal que el usuario cambió el modo de vista previa de impresión|TRUE indica que el modo de vista previa de impresión está establecido. FALSE indica que el modo de vista previa de impresión está desactivado.|No se usa.|No se usa.|
|AFX_WM_PROPERTY_CHANGED|Se envía al propietario del`CMFCPropertyGridCtrl`control de cuadrícula de propiedades ( ) cuando el usuario cambia el valor de la propiedad seleccionada.|El identificador de control de la lista de propiedades.|Un puntero a`CMFCPropertyGridProperty`la propiedad ( ) que ha cambiado.|No se usa.|
|AFX_WM_RESETCONTEXTMENU|Se envía a la ventana de marco principal cuando el usuario restablece el menú contextual durante la personalización.|El identificador de recurso del menú contextual.|Un puntero al menú `CMFCPopupMenu`contextual actual, .|No se usa.|
|AFX_WM_RESETKEYBOARD|El marco de trabajo envía este mensaje a la ventana de marco principal cuando el usuario restablece todos los aceleradores de teclado durante la personalización.|No se usa.|No se usa.|No se usa.|
|AFX_WM_RESETMENU|El marco de trabajo envía este mensaje al propietario del menú (una ventana de marco) cuando el usuario restablece un menú de marco de aplicación durante la personalización|El identificador de recurso de menú.|No se usa.|No se usa.|
|AFX_WM_RESETPROMPT|El marco de trabajo envía este mensaje cuando el usuario restablece una barra de herramientas desde el cuadro de diálogo de personalización de la barra de herramientas. El controlador predeterminado muestra un cuadro de mensaje que pregunta si el usuario desea restablecer la barra de herramientas.|No se usa.|No se usa.|No se usa.|
|AFX_WM_RESETTOOLBAR|Un `CMFCToolBar` objeto envía este mensaje cuando se restaura una barra de herramientas a su estado original, es decir, se carga desde los recursos. Procesar este mensaje para volver a insertar `CMFCToolbarButton`los botones de la barra de herramientas cuyas clases se derivan de . Para obtener más información, vea `CMFCToolbarComboBoxButton`.|El identificador de recurso de una barra de herramientas cuyo estado se restauró.|No se usa.|Cero.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton`objeto envía este mensaje a su propietario cuando el usuario hace clic en un botón de menú normal. Procese este mensaje cada `CMFCToolbarMenuButton` vez que utilice para mostrar un menú emergente cuando el usuario haga clic en un botón.|El identificador de comando de un botón que envía el mensaje.|Coordenadas de pantalla del cursor. La palabra de orden bajo especifica la coordenada x. La palabra de orden superior especifica la coordenada y.|No se usa.|
|AFX_WM_TOOLBARMENU|Se envía a la ventana de marco principal cuando el usuario suelta el botón derecho de un mouse mientras el puntero del mouse está en el área de cliente o no cliente de un panel.|No se usa.|Coordenadas de pantalla del puntero del ratón. La palabra de orden bajo especifica la coordenada x. La palabra de orden superior especifica la coordenada y.|Cero si la aplicación procesa este mensaje; de lo contrario, distinto de cero.|
|AFX_WM_UPDATETOOLTIPS|Se envía a todos los propietarios de información sobre herramientas para indicar que se deben volver a crear sus controles de información sobre herramientas.|El tipo de control que debe procesar este mensaje. Consulte la tabla más adelante en este tema para obtener una lista de valores posibles.|No se usa.|No se usa.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog`envía este mensaje al marco primario cuando el usuario hace clic en el botón **Ayuda** o entra en el modo de ayuda haciendo clic en el botón Título de **ayuda** o en la tecla F1.|No se usa.|Un puntero a `CMFCWindowsManagerDialog`la instancia de .|No se usa.|

En la tabla siguiente se muestran los valores de la palabra baja del parámetro *lParam* del método AFX_WM_HSCROLL:

|||
|-|-|
|Value|Significado|
|SB_ENDSCROLL|El usuario finaliza el desplazamiento.|
|SB_LEFT|El usuario se desplaza a la parte superior izquierda.|
|SB_RIGHT|El usuario se desplaza hacia la parte inferior derecha.|
|SB_LINELEFT|El usuario se desplaza a la izquierda por una unidad.|
|SB_LINERIGHT|El usuario se desplaza a la derecha por una unidad.|
|SB_PAGELEFT|El usuario se desplaza a la izquierda por el ancho de la ventana.|
|SB_PAGERIGHT|El usuario se desplaza a la derecha por el ancho de la ventana.|
|SB_THUMBPOSITION|El usuario ha arrastrado el cuadro de desplazamiento (thumb) y ha soltado el botón del ratón. La palabra de orden superior indica la posición del cuadro de desplazamiento al final de la operación de arrastre.|
|SB_THUMBTRACK|El usuario está arrastrando el cuadro de desplazamiento. El mensaje AFX_WM_ON_HSCROLL se envía repetidamente con este valor hasta que el usuario suelta el botón del mouse. La palabra de orden superior indica la posición a la que se ha arrastrado el cuadro de desplazamiento.|

> [!NOTE]
> La palabra de orden superior del parámetro *lParam* especifica la posición actual del cuadro de desplazamiento si la palabra de orden bajo está SB_THUMBPOSITION o SB_THUMBTRACK; de lo contrario, esta palabra no se utiliza.

En la tabla siguiente se enumeran los valores de marca para el parámetro *lParam* del mensaje AFX_WM_UPDATETOOLTIPS:

|||
|-|-|
|Marca|Value|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
