---
title: "Control de notificaciones de personalizaci&#243;n | Microsoft Docs"
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
  - "TBN_CUSTHELP"
  - "TBN_QUERYINSERT"
  - "TBNOTIFY"
  - "NMHDR"
  - "TBN_TOOLBARCHANGE"
  - "TBN_ENDDRAG"
  - "NM_SETFOCUS"
  - "TBN_RESET"
  - "NM_RETURN"
  - "NM_ENDWAIT"
  - "NM_STARTWAIT"
  - "TBN_BEGINDRAG"
  - "NM_OUTOFMEMORY"
  - "TBN_QUERYDELETE"
  - "NM_DBLCLK"
  - "TBN_ENDADJUST"
  - "NM_KILLFOCUS"
  - "NM_RCLICK"
  - "TBN_BEGINADJUST"
  - "NM_CLICK"
  - "NM_RDBLCLK::"
  - "TBN_GETBUTTONINFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TBN_ENDADJUST (notificación)"
  - "TBNOTIFY (notificación)"
  - "TBN_BEGINDRAG (notificación)"
  - "TBN_TOOLBARCHANGE (notificación)"
  - "NM_CLICK (notificación)"
  - "NM_RETURN (notificación)"
  - "NM_RCLICK (notificación)"
  - "TBN_ENDDRAG (notificación)"
  - "TBN_BEGINADJUST (notificación)"
  - "NM_ENDWAIT (notificación)"
  - "NM_KILLFOCUS (notificación)"
  - "NM_SETFOCUS (notificación)"
  - "NM_OUTOFMEMORY (notificación)"
  - "TBN_QUERYINSERT (notificación)"
  - "NMHDR"
  - "NM_STARTWAIT (notificación)"
  - "CToolBarCtrl (clase), controlar notificaciones"
  - "TBN_CUSTHELP (notificación)"
  - "TBN_RESET (notificación)"
  - "NM_DBLCLK (notificación)"
  - "TBN_QUERYDELETE (notificación)"
  - "NM_RDBLCLK (notificación)"
  - "TBN_GETBUTTONINFO (notificación)"
ms.assetid: 219ea08e-7515-4b98-85cb-47120f08c0a2
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Control de notificaciones de personalizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control común de barra de herramientas de Windows tiene características de personalización integradas, incluyendo un cuadro de diálogo de personalización definido por el sistema que permite insertar, eliminar o reorganizar botones de la barra de herramientas. La aplicación determina si las características de personalización están disponibles y controla la medida en que el usuario puede personalizar la barra de herramientas.  
  
 Para que estas características de personalización estén disponibles para el usuario, proporcione a la barra de herramientas el estilo `CCS_ADJUSTABLE`. Las características de personalización permiten al usuario arrastrar un botón a una nueva posición o quitar un botón arrastrándolo fuera de la barra de herramientas. Además, el usuario puede hacer doble clic en la barra de herramientas para mostrar el cuadro de diálogo **Personalizar barra de herramientas**, que permite al usuario agregar, eliminar y reorganizar botones de la barra de herramientas. La aplicación puede mostrar el cuadro de diálogo mediante la función de miembro [Personalizar](../Topic/CToolBarCtrl::Customize.md).  
  
 El control de barra de herramientas envía mensajes de notificación a la ventana primaria en cada paso del proceso de personalización. Si el usuario mantiene presionada la tecla MAYÚS y comienza a arrastrar un botón, la barra de herramientas controla automáticamente la operación de arrastre. La barra de herramientas envía el mensaje de notificación **TBN\_QUERYDELETE** a la ventana primaria para determinar si se puede eliminar el botón. La operación de arrastre termina si la ventana primaria devuelve **FALSE**. De lo contrario, la barra de herramientas captura la entrada del mouse y espera a que el usuario suelte el botón del mouse.  
  
 Cuando el usuario suelta el botón del mouse, el control de barra de herramientas determina la ubicación del cursor del mouse. Si el cursor está fuera de la barra de herramientas, el botón se elimina. Si el cursor está en otro botón de barra de herramientas, la barra de herramientas envía el mensaje de notificación **TBN\_QUERYINSERT** a la ventana primaria para determinar si se puede insertar un botón a la izquierda del botón especificado. El botón se inserta si la ventana primaria devuelve **TRUE**; en caso contrario, no se inserta. La barra de herramientas envía el mensaje de notificación **TBN\_TOOLBARCHANGE** para indicar el final de la operación de arrastre.  
  
 Si el usuario comienza una operación de arrastre sin mantener presionada la tecla MAYÚS, el control de barra de herramientas envía el mensaje de notificación **TBN\_BEGINDRAG** a la ventana propietaria. Una aplicación que implementa su propio código de arrastre de botón puede usar este mensaje como una señal para comenzar una operación de arrastre. La barra de herramientas envía el mensaje de notificación **TBN\_ENDDRAG** para indicar el final de la operación de arrastre.  
  
 Un control de barra de herramientas envía mensajes de notificación cuando el usuario personaliza una barra de herramientas mediante el cuadro de diálogo **Personalizar barra de herramientas**. La barra de herramientas envía el mensaje de notificación **TBN\_BEGINADJUST** después de que el usuario haga doble clic en la barra de herramientas, pero antes de la creación del cuadro de diálogo. A continuación, la barra de herramientas comienza a enviar una serie de mensajes de notificación **TBN\_QUERYINSERT** para determinar si la barra de herramientas permite la inserción de botones. Si la ventana primaria devuelve **TRUE**, la barra de herramientas deja de enviar mensajes de notificación **TBN\_QUERYINSERT**. Si la ventana primaria no devuelve **TRUE** para ningún botón, la barra de herramientas destruye el cuadro de diálogo.  
  
 A continuación, el control de barra de herramientas determina si se pueden eliminar botones de la barra de herramientas mediante el envío de un mensaje de notificación **TBN\_QUERYDELETE** para cada botón de la barra de herramientas. La ventana primaria devuelve **TRUE** para indicar que un botón se puede eliminar; en caso contrario, devuelve **FALSE**. La barra de herramientas agrega todos los botones de barra de herramientas al cuadro de diálogo, pero atenúa aquellos que no se pueden eliminar.  
  
 Cuando el control de barra de herramientas necesita información sobre un botón en el cuadro de diálogo Personalizar barra de herramientas, envía el mensaje de notificación **TBN\_GETBUTTONINFO** y especifica el índice del botón del que necesita información y la dirección de una estructura **TBNOTIFY**. La ventana primaria debe rellenar la estructura con la información pertinente.  
  
 El cuadro de diálogo **Personalizar barra de herramientas** incluye un botón Ayuda y un botón Restablecer. Cuando el usuario elige el botón Ayuda, el control de barra de herramientas envía el mensaje de notificación **TBN\_CUSTHELP**. La ventana primaria debe responder mostrando información de ayuda. El cuadro de diálogo envía el mensaje de notificación **TBN\_RESET** cuando el usuario selecciona el botón Restablecer. Este mensaje indica que la barra de herramientas está a punto de reinicializar el cuadro de diálogo.  
  
 Estos mensajes son todos los mensaje **WM\_NOTIFY** y pueden controlarse en la ventana propietaria mediante la adición de entradas de mapa de mensajes con el formato siguiente al mapa de mensajes de la ventana propietaria:  
  
 `ON_NOTIFY( wNotifyCode, idControl, memberFxn )`  
  
 `wNotifyCode`  
 Código identificador del mensaje de notificación, como **TBN\_BEGINADJUST**.  
  
 `idControl`  
 Identificador del control que envía la notificación.  
  
 `memberFxn`  
 Función miembro que se llamará cuando se reciba esta notificación.  
  
 La función miembro se declararía con el prototipo siguiente:  
  
 `afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );`  
  
 Si el controlador de mensajes de notificación devuelve un valor, debe colocarse en **LRESULT** que apunta *result*.  
  
 Para cada mensaje, `pNotifyStruct` señala una estructura **NMHDR** o una estructura **TBNOTIFY**. Estas estructuras se describen a continuación:  
  
 La estructura **NMHDR** contiene los siguientes miembros:  
  
 `typedef struct tagNMHDR {`  
  
 `HWND hwndFrom;  // handle of control sending message`  
  
 `UINT idFrom;// identifier of control sending message`  
  
 `UINT code;  // notification code; see below`  
  
 `} NMHDR;`  
  
 **hwndFrom**  
 Identificador de ventana del control que envía la notificación. Para convertir este identificador en un puntero `CWnd`, use [CWnd::FromHandle](../Topic/CWnd::FromHandle.md).  
  
 **idFrom**  
 Identificador del control que envía la notificación.  
  
 **code**  
 Código de notificación. Este miembro puede ser un valor específico para un tipo de control, como **TBN\_BEGINADJUST** o **TTN\_NEEDTEXT**, o bien ser uno de los valores de notificación comunes que se enumeran a continuación:  
  
-   **NM\_CLICK** El usuario hizo clic con el botón izquierdo del mouse en el control.  
  
-   **NM\_DBCLICK** El usuario hizo doble clic con el botón izquierdo del mouse en el control.  
  
-   **NM\_KILLFOCUS** El control perdió el foco de entrada.  
  
-   **NM\_OUTOFMEMORY** El control no pudo completar una operación porque no hay suficiente memoria disponible.  
  
-   **NM\_RCLICK** El usuario hizo clic con el botón derecho del mouse en el control.  
  
-   **NM\_RDBCLICK** El usuario hizo doble clic con el botón derecho del mouse en el control.  
  
-   **NM\_RETURN** El control tiene el foco de entrada y el usuario presionó la tecla ENTRAR.  
  
-   **NM\_SETFOCUS** El control recibió el foco de entrada.  
  
 La estructura **TBNOTIFY** contiene los siguientes miembros:  
  
 `typedef struct {`  
  
 `NMHDR hdr; // information common to all WM_NOTIFY messages`  
  
 `int iItem; // index of button associated with notification`  
  
 `TBBUTTON tbButton; // info about button associated withnotification`  
  
 `int cchText;   // count of characters in button text`  
  
 `LPSTR lpszText;// address of button text`  
  
 `} TBNOTIFY, FAR* LPTBNOTIFY;`  
  
## Comentarios  
 **hdr**  
 Información común para todos los mensajes **WM\_NOTIFY**.  
  
 **iItem**  
 Índice del botón asociado a la notificación.  
  
 **tbButton**  
 estructura `TBBUTTON` que contiene información sobre el botón de barra de herramientas asociado a la notificación.  
  
 **cchText**  
 Recuento de caracteres del texto del botón.  
  
 **lpszText**  
 Puntero al texto del botón.  
  
 Las notificaciones que la barra de herramientas envía son las siguientes:  
  
-   **TBN\_BEGINADJUST** Se envía cuando el usuario comienza a personalizar un control de barra de herramientas. El puntero apunta a una estructura **NMHDR** que contiene información sobre la notificación. El controlador no tiene que devolver ningún valor específico.  
  
-   **TBN\_BEGINDRAG** Se envía cuando el usuario comienza a arrastrar un botón en un control de barra de herramientas. El puntero apunta a una estructura **TBNOTIFY**. El miembro **iItem** contiene el índice basado en cero del botón que se está arrastrando. El controlador no tiene que devolver ningún valor específico.  
  
-   **TBN\_CUSTHELP** Se envía cuando el usuario elige el botón Ayuda en el cuadro de diálogo Personalizar barra de herramientas. No de devuelve ningún valor. El puntero apunta a una estructura **NMHDR** que contiene información sobre el mensaje de notificación. El controlador no tiene que devolver ningún valor específico.  
  
-   **TBN\_ENDADJUST** Se envía cuando el usuario deja de personalizar un control de barra de herramientas. El puntero apunta a una estructura **NMHDR** que contiene información sobre el mensaje de notificación. El controlador no tiene que devolver ningún valor específico.  
  
-   **TBN\_ENDDRAG** Se envía cuando el usuario deja de arrastrar un botón en un control de barra de herramientas. El puntero apunta a una estructura **TBNOTIFY**. El miembro **iItem** contiene el índice basado en cero del botón que se está arrastrando. El controlador no tiene que devolver ningún valor específico.  
  
-   **TBN\_GETBUTTONINFO** Se envía cuando el usuario está personalizando un control de barra de herramientas. La barra de herramientas usa este mensaje de notificación para recuperar la información necesaria para el cuadro de diálogo Personalizar barra de herramientas. El puntero apunta a una estructura **TBNOTIFY**. El miembro **iItem** especifica el índice basado en cero de un botón. Los miembros **pszText** y **cchText** especifican la dirección y la longitud, en caracteres, del texto del botón actual. Una aplicación debería rellenar la estructura con información acerca del botón. Devuelva **TRUE** si la información del botón se copió en la estructura o **FALSE** en caso contrario.  
  
-   **TBN\_QUERYDELETE** Se envía mientras el usuario está personalizando una barra de herramientas para determinar si un botón se puede eliminar de un control de barra de herramientas. El puntero apunta a una estructura **TBNOTIFY**. El miembro **iItem** contiene el índice basado en cero del botón que se va a eliminar. Devuelva **TRUE** para permitir que el botón se elimine o **FALSE** para impedir su eliminación.  
  
-   **TBN\_QUERYINSERT** Se envía cuando el usuario está personalizando un control de barra de herramientas para determinar si un botón se puede insertar a la izquierda del botón especificado. El puntero apunta a una estructura **TBNOTIFY**. El miembro **iItem** contiene el índice basado en cero del botón que se va a insertar. Devuelva **TRUE** para permitir que un botón se inserte delante del botón especificado o **FALSE** para impedir que el botón se inserte.  
  
-   **TBN\_RESET** Se envía cuando el usuario restablece el contenido del cuadro de diálogo Personalizar barra de herramientas. El puntero apunta a una estructura **NMHDR** que contiene información sobre el mensaje de notificación. El controlador no tiene que devolver ningún valor específico.  
  
-   **TBN\_TOOLBARCHANGE** Se envía después de que el usuario personalice un control de barra de herramientas. El puntero apunta a una estructura **NMHDR** que contiene información sobre el mensaje de notificación. El controlador no tiene que devolver ningún valor específico.  
  
## Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)