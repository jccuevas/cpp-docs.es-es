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
ms.openlocfilehash: 45c6a9174cbd39c4c0c24ffbdfdefb9d184a3cc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594693"
---
# <a name="afx-messages"></a>mensajes AFX

Estos mensajes se utilizan en MFC.

## <a name="messages"></a>Mensajes

En la tabla siguiente se enumera los mensajes que se usan en la biblioteca MFC:

||||||
|-|-|-|-|-|
|Mensaje|Descripción|[in] *wParam*|*lParam* (todos los parámetros son [in] a menos que se indique lo contrario).|Valor devuelto|
|AFX_WM_ACCGETOBJECT|No usado.|No usado.|No es aplicable.|No es aplicable.|
|AFX_WM_ACCGETSTATE|Se usa para admitir la accesibilidad. Enviar este mensaje a `CMFCPopupMenu` o `CMFCRibbonPanelMenu` para recuperar el estado del elemento actual.|Índice del elemento, que podría ser un botón de menú o un separador.|No usado.|El estado del elemento. Es -1 si el índice no es válido, 0 si el botón de menú no tiene ningún atributo especial. En caso contrario, es una combinación de las marcas siguientes:<br /><br /> TBBS_DISABLED: el elemento está deshabilitado<br /><br /> TBBS_CHECKED: el elemento está activado<br /><br /> TBBS_BUTTON: el elemento es un botón de comando estándar<br /><br /> TBBS_PRESSED: el botón está presionado<br /><br /> TBBS_INDETERMINATE: estado indefinido<br /><br /> TBBS_SEPARATOR - en lugar de un botón de menú, este formularios de elemento de una separación entre otros elementos de menú|
|AFX_WM_CHANGE_ACTIVE_TAB|El marco envía este mensaje para el control de barra de control de tamaño ajustable. Procesar este mensaje para recibir notificaciones de `CMFCTabCtrl` objetos cuando un usuario cambia una pestaña activa.|El índice de una pestaña.|No usado.|Distinto de cero.|
|AFX_WM_CHANGE_CURRENT_FOLDER|El marco envía este mensaje con el elemento primario de `CMFCShellListCtrl` cuando el usuario ha cambiado la carpeta actual.|No usado.|No usado.|No usado.|
|AFX_WM_CHANGEVISUALMANAGER|El marco envía este mensaje a todas las ventanas de marco cuando el usuario cambia el administrador Visual actual. En respuesta a este mensaje, una ventana de marco vuelve a calcular su región y ajusta los otros parámetros según sea necesario. Puede procesar el mensaje AFX_WM_CHANGEVISUALMANAGER en la aplicación si necesita recibir notificaciones acerca de este evento. Debe llamar al controlador de la clase base (`OnChangeVisualManager`) para asegurarse de que interno del marco de procesamiento de este evento tiene lugar.|No usado.|No usado.|No usado.|
|AFX_WM_CHANGING_ACTIVE_TAB|Envía al elemento primario de `CMFCTabCtrl` objeto.  Procesar este mensaje si desea recibir notificaciones del `CMFCTabCtrl` objetos cuando un usuario restablece una pestaña.|El índice de la pestaña que se va a activar.|No usado.|Distinto de cero.|
|AFX_WM_CHECKEMPTYMINIFRAME|Sólo para uso interno.|No es aplicable.|No es aplicable.|No es aplicable.|
|AFX_WM_CREATETOOLBAR|Enviado desde `CMFCToolBarsListPropertyPage` cuando un usuario crea una nueva barra de herramientas durante el proceso de personalización. Puede procesar este mensaje para crear instancias de un objeto derivado de CMFCToolBar personalizado. Si controla este mensaje y crear su propia barra de herramientas, se omite la llamada al controlador predeterminado.|No usado.|Un puntero a una cadena que contiene el nombre de la barra de herramientas.|Un puntero a la barra de herramientas recién creado. NULL indica que se canceló la creación de la barra de herramientas.|
|AFX_WM_CUSTOMIZEHELP|Envía a la ventana de marco principal de la hoja de propiedades de personalización `CMFCToolbarCustomize Dialog` cuando el usuario presiona el **ayuda** botón o la tecla F1.|Especifica la página activa de la hoja de propiedades de personalización.|Puntero a un objeto `CMFCToolbarCustomize Dialog` .|Valor de cero.|
|AFX_WM_CUSTOMIZETOOLBAR|El `CMFCToolbarCustomize Dialog` envía este mensaje para notificar al marco primario que el usuario está creando una nueva barra de herramientas.|Es TRUE cuando se inicia personalización, es FALSE cuando haya finalizado la personalización.|No usado.|Valor de cero.|
|AFX_WM_DELETETOOLBAR|Se envía a la ventana de marco principal cuando el usuario está a punto de eliminar una barra de herramientas en el modo de personalización.<br /><br /> Procesar este mensaje para realizar acciones adicionales cuando un usuario elimina una barra de herramientas en el modo de personalización. También debe llamar al controlador predeterminado (`OnToolbarDelete`), lo que elimina la barra de herramientas. El controlador predeterminado devuelve un valor que indica si es posible eliminar la barra de herramientas.|No usado.|Puntero a un `CMFCToolBar` objeto va a eliminar.|Distinto de cero si no se puede eliminar una barra de herramientas; en caso contrario, es 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` Este mensaje se envía a la ventana de marco principal para recuperar los colores del documento.|No usado.|[in, out] Puntero a un `CList<COLORREF, COLORREF>` objeto.|Valor de cero.|
|AFX_WM_GETDRAGBOUNDS|Sólo para uso interno.|No es aplicable.|No es aplicable.|No es aplicable.|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Se envía a la ventana de marco principal cuando un usuario resalta un elemento de lista de la cinta de opciones.|Índice del elemento resaltado|Un puntero a `CMFCBaseRibbonElement`|No usado.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Envía a un elemento primario de `CMFCShellListCtrl` o `CMFCShellTreeCtrl` controla cuando un usuario termina de ejecutar un comando de shell.|El identificador del comando que ejecuta el usuario|No usado.|Si la aplicación procesa este mensaje, debe devolver cero.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|El marco envía este mensaje al elemento primario de la cinta de opciones antes de mostrar el menú emergente. Puede procesar este mensaje y modificar los menús emergentes en cualquier momento.|No usado.|Un puntero a `CMFCBaseRibbonElement`|No usado.|
|AFX_WM_ON_CANCELTABMOVE|Sólo para uso interno.|No es aplicable.|No es aplicable.||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|El marco envía este mensaje para el marco principal cuando el usuario cambia la categoría de Control de cinta activa.|No usado.|Un puntero a la `CMFCRibbonBar` cuya categoría ha cambiado.|No usado.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|El marco envía este mensaje para notificar al propietario de `CMFCDesktopAlertWnd` que la ventana está a punto de cerrarse.|No usado.|Un puntero a `CMFCDesktopAlertWnd` objeto.|No usado.|
|AFX_WM_ON_DRAGCOMPLETE|Sólo para uso interno.|No es aplicable.|No es aplicable.|No es aplicable.|
|AFX_WM_ON_GET_TAB_TOOLTIP|Se envía a la ventana de marco principal cuando una ventana de ficha está a punto de mostrar una información sobre herramientas para una ficha, si está habilitadas la información sobre herramientas personalizada.|No usado.|Un puntero a un `CMFCTabToolTipInfo` estructura.|No usado.|
|AFX_WM_ON_HSCROLL|Se envían al control de barra de control de tamaño ajustable. Procesar este mensaje para recibir notificaciones de `CMFCTabCtrl` objetos cuando se produce un evento de desplazamiento en la barra de desplazamiento horizontal de widget con pestañas.|La palabra de orden inferior se especifica un valor de la barra de desplazamiento que indica que el usuario de la solicitud de desplazamiento.  Para obtener más información, vea la tabla más adelante en este tema.|No usado.|Distinto de cero.|
|AFX_WM_ON_MOVE_TAB|Se envían al elemento primario de una ventana con pestañas cuando un usuario arrastra una pestaña a una nueva posición.|Índice de base cero de la pestaña en su posición original.|[out] Índice de base cero de la pestaña en la nueva posición.|Valor de cero.|
|AFX_WM_ON_MOVETABCOMPLETE|Sólo para uso interno.|No es aplicable.|No es aplicable.|No es aplicable.|
|AFX_WM_ON_MOVETOTABGROUP|Se envía a la ventana de marco principal cuando un usuario mueve una ventana secundaria MDI de un grupo de pestañas a otra.|Un identificador de ventana con pestañas (`CMFCTabCtrl`) desde que se ha quitado la ventana secundaria MDI.|[out] Un identificador de ventana con pestañas (`CMFCTabCtrl`) para que se ha insertado la ventana secundaria MDI.|ignorado.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Envía a un elemento primario de `CDockablePane` cuando el usuario hace clic en el **cerrar** botón en el título de la barra de control.|No usado.|Un puntero a un panel acoplable en el que el usuario hizo clic en el **cerrar** botón.|TRUE si no se puede cerrar un panel; en caso contrario, FALSE.|
|AFX_WM_ON_RENAME_TAB|Se envían al elemento primario de ventana con pestañas después de que el usuario cambia el nombre de una ficha editable.|Índice de base cero de la pestaña cuyo nombre ha cambiado.|[out] Un puntero a una cadena que contiene el nuevo nombre de pestaña.|Distinto de cero si la aplicación procesa este mensaje; el marco de trabajo, suprimirá la llamada a `CMFCBaseTabCtrl::SetTabLabel`.  Si se devuelve cero, a continuación, `CMFCBaseTabCtrl::SetTabLabel` se llama el marco de trabajo.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Envía al marco primario cuando el usuario inicia la personalización. Procesar este mensaje si desea mostrar su propio cuadro de diálogo de personalización.|No usado.|Un puntero al control de cinta para personalizarse.|Distinto de cero si la aplicación procesa este mensaje y muestra su propio cuadro de diálogo de personalización. Si la aplicación devuelve cero, el marco de trabajo mostrará el cuadro de diálogo de personalización integradas.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Sólo para uso interno.|No es aplicable.|No es aplicable.|No es aplicable.|
|AFX_WM_POSTSETPREVIEWFRAME|Enviado notificar al marco principal que el usuario puede cambiar el modo de vista previa de impresión|TRUE indica que se ha establecido el modo de vista previa de impresión. FALSE indica que el modo de vista previa de impresión se ha desactivado.|No usado.|No usado.|
|AFX_WM_PROPERTY_CHANGED|Envía al propietario del control de cuadrícula de propiedad (`CMFCPropertyGridCtrl`) cuando el usuario cambia el valor de la propiedad seleccionada.|El identificador de control de la lista de propiedades.|Un puntero a la propiedad (`CMFCPropertyGridProperty`) que ha cambiado.|No usado.|
|AFX_WM_RESETCONTEXTMENU|Se envía a la ventana de marco principal cuando el usuario restablece el menú contextual durante la personalización.|El identificador de recurso del menú contextual.|Un puntero al menú contextual actual, `CMFCPopupMenu`.|No usado.|
|AFX_WM_RESETKEYBOARD|El marco envía este mensaje a la ventana de marco principal cuando el usuario restablece todos los aceleradores de teclado durante la personalización.|No usado.|No usado.|No usado.|
|AFX_WM_RESETMENU|El marco envía este mensaje al propietario del menú (una ventana de marco) cuando el usuario restablece un menú de marco de aplicación durante la personalización|El identificador de recurso de menú.|No usado.|No usado.|
|AFX_WM_RESETPROMPT|El marco envía este mensaje cuando el usuario se restablece una barra de herramientas de la barra de herramientas de cuadro de diálogo Personalizar. El controlador predeterminado muestra un cuadro de mensaje que pregunta si el usuario desea restablecer la barra de herramientas.|No usado.|No usado.|No usado.|
|AFX_WM_RESETTOOLBAR|Un `CMFCToolBar` objeto envía este mensaje cuando una barra de herramientas se restaura a su estado original, es decir, carga de los recursos. Procesar este mensaje para volver a insertar los botones de barra de herramientas cuyas clases se derivan `CMFCToolbarButton`. Para obtener más información, consulta `CMFCToolbarComboBoxButton`.|El identificador de recurso de una barra de herramientas cuyo estado se ha restaurado.|No usado.|Valor de cero.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` objeto envía este mensaje a su propietario cuando el usuario hace clic en un botón de menú normal. Procesar este mensaje cada vez que use `CMFCToolbarMenuButton` para mostrar un menú emergente cuando el usuario hace clic en un botón.|El identificador de comando de un botón que envía el mensaje.|Coordenadas de pantalla del cursor. La palabra de orden inferior especifica la coordenada "x". La palabra de orden superior especifica la coordenada y.|No usado.|
|AFX_WM_TOOLBARMENU|Se envía a la ventana de marco principal cuando el usuario suelta el botón secundario del mouse mientras el puntero del mouse se encuentra en el cliente o el área no cliente de un panel.|No usado.|Coordenadas de pantalla del puntero del mouse. La palabra de orden inferior especifica la coordenada "x". La palabra de orden superior especifica la coordenada y.|Cero si la aplicación procesa este mensaje; en caso contrario, es distinto de cero.|
|AFX_WM_UPDATETOOLTIPS|Se envía a todos los propietarios de la información sobre herramientas para indicar que se deben volver a crear los controles de información sobre herramientas.|El tipo de control que se debe procesar este mensaje. Consulte la tabla más adelante en este tema para obtener una lista de valores posibles.|No usado.|No usado.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` envía este mensaje en el marco principal cuando el usuario hace clic en el **ayuda** botón o entra en el modo de ayuda, haga clic en el **ayuda** botón de título o la tecla F1.|No usado.|Un puntero a la instancia de `CMFCWindowsManagerDialog`.|No usado.|

La siguiente tabla muestra los valores de la palabra baja de la *lParam* parámetro del método AFX_WM_HSCROLL:

|||
|-|-|
|Valor|Significado|
|SB_ENDSCROLL|El usuario finaliza el desplazamiento.|
|SB_LEFT|El usuario se desplaza a la esquina superior izquierda.|
|SB_RIGHT|El usuario se desplaza a la esquina inferior derecha.|
|SB_LINELEFT|El usuario desplaza una unidad de la izquierda.|
|SB_LINERIGHT|El usuario desplaza una unidad de la derecha.|
|SB_PAGELEFT|El usuario desplaza a la izquierda el ancho de la ventana.|
|SB_PAGERIGHT|El usuario desplaza el ancho de la ventana derecha.|
|SB_THUMBPOSITION|El usuario ha arrastrado el cuadro de desplazamiento (control) y soltado el botón del mouse. La palabra de orden superior indica la posición del cuadro de desplazamiento al final de la operación de arrastre.|
|SB_THUMBTRACK|El usuario está arrastrando el cuadro de desplazamiento. El mensaje AFX_WM_ON_HSCROLL se envía repetidamente con este valor hasta que el usuario suelta el botón del mouse. La palabra de orden superior indica la posición a la que se ha arrastrado el cuadro de desplazamiento.|

> [!NOTE]
>  La palabra de orden superior de la *lParam* parámetro especifica la posición actual del cuadro de desplazamiento si la palabra de orden inferior es SB_THUMBPOSITION o SB_THUMBTRACK; en caso contrario, no se utiliza esta palabra.

En la tabla siguiente se enumera los valores de marca para la *lParam* parámetro del mensaje AFX_WM_UPDATETOOLTIPS:

|||
|-|-|
|Marcar|Valor|
|AFX_TOOLTIP_TYPE_DEFAULT|0 x 0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0 x 0080|
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
