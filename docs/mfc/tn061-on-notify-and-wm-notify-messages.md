---
title: 'TN061: Mensajes ON_NOTIFY y WM_NOTIFY'
ms.date: 06/28/2018
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: aa1efb628ee45be3dfaee320cf64c4b2cbb91f04
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302242"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061: Mensajes ON_NOTIFY y WM_NOTIFY

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota técnica proporciona información general sobre el nuevo mensaje de WM_NOTIFY y describe la forma recomendada (y más común) de controlar los mensajes de WM_NOTIFY en la aplicación MFC.

**Mensajes de notificación en Windows 3. x**

En Windows 3. x, los controles envían una notificación a sus elementos primarios de eventos, como clics del mouse, cambios en el contenido y la selección, y controlan la pintura del fondo mediante el envío de un mensaje al elemento primario. Las notificaciones simples se envían como mensajes de WM_COMMAND especiales, con el código de notificación (como BN_CLICKED) y el identificador de control empaquetados en *wParam* y en el identificador del control en *lParam*. Tenga en cuenta que, como *wParam* y *lParam* están llenos, no hay ninguna manera de pasar datos adicionales; estos mensajes solo pueden ser una notificación simple. Por ejemplo, en la notificación de BN_CLICKED, no hay ninguna manera de enviar información sobre la ubicación del cursor del mouse cuando se hizo clic en el botón.

Cuando los controles de Windows 3. x deben enviar un mensaje de notificación que incluya datos adicionales, usan una variedad de mensajes especiales, como WM_CTLCOLOR, WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM WM_ CHARTOITEM, WM_VKEYTOITEM, etc. Estos mensajes se pueden reflejar de nuevo en el control que los envió. Para obtener más información, vea [TN062: reflexión de mensajes para controles de Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

**Mensajes de notificación en Win32**

En el caso de los controles que existían en Windows 3,1, la API de Win32 usa la mayoría de los mensajes de notificación que se usaron en Windows 3. x. Sin embargo, Win32 también agrega una serie de controles sofisticados y complejos a los que se admiten en Windows 3. x. Con frecuencia, estos controles necesitan enviar datos adicionales con sus mensajes de notificación. En lugar de agregar un nuevo **WM_** <strong>\*</strong> mensaje para cada nueva notificación que necesite datos adicionales, los diseñadores de la API de Win32 optaron por agregar un solo mensaje, WM_NOTIFY, que puede pasar cualquier cantidad de datos adicionales de manera normalizada.

WM_NOTIFY mensajes contienen el identificador del control que envía el mensaje en *wParam* y un puntero a una estructura en *lParam*. Esta estructura es una estructura **nmhdr** o una estructura más grande que tiene una estructura **nmhdr** como primer miembro. Tenga en cuenta que, puesto que el miembro **NMHDR** es en primer lugar, se puede usar un puntero a esta estructura como un puntero a un **NMHDR** o como un puntero a la estructura mayor en función de cómo se convierta.

En la mayoría de los casos, el puntero apuntará a una estructura mayor y tendrá que convertirlo cuando lo use. En algunas notificaciones, como las notificaciones comunes (cuyos nombres empiezan por **NM_** ) y las notificaciones de TTN_SHOW y TTN_POP del control de información sobre herramientas, es una estructura **NMHDR** realmente utilizada.

La estructura **NMHDR** o el miembro inicial contiene el identificador y el identificador del control que envía el mensaje y el código de notificación (como TTN_SHOW). A continuación se muestra el formato de la estructura **NMHDR** :

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Para un mensaje de TTN_SHOW, el miembro de **código** se establecería en TTN_SHOW.

La mayoría de las notificaciones pasan un puntero a una estructura más grande que contiene una estructura **NMHDR** como su primer miembro. Por ejemplo, considere la estructura utilizada por el mensaje de notificación LVN_KEYDOWN del control de vista de lista, que se envía cuando se presiona una tecla en un control de vista de lista. El puntero apunta a una estructura de **LV_KEYDOWN** , que se define como se muestra a continuación:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Tenga en cuenta que, puesto que el miembro **NMHDR** está en primer lugar en esta estructura, el puntero que se pasa en el mensaje de notificación se puede convertir en un puntero a un **NMHDR** o un puntero a un **LV_KEYDOWN**.

**Notificaciones comunes a todos los nuevos controles de Windows**

Algunas notificaciones son comunes a todos los nuevos controles de Windows. Estas notificaciones pasan un puntero a una estructura **NMHDR** .

|Código de notificación|Enviado porque|
|-----------------------|------------------|
|NM_CLICK|El usuario hizo clic con el botón primario del mouse en el control|
|NM_DBLCLK|El usuario hizo doble clic con el botón primario del mouse en el control|
|NM_RCLICK|El usuario hizo clic con el botón secundario del mouse en el control|
|NM_RDBLCLK|El usuario hizo doble clic con el botón secundario del mouse en el control|
|NM_RETURN|El usuario presionó la tecla entrar mientras el control tiene el foco de entrada|
|NM_SETFOCUS|El control ha recibido el foco de entrada|
|NM_KILLFOCUS|El control ha perdido el foco de entrada|
|NM_OUTOFMEMORY|El control no pudo completar una operación porque no había suficiente memoria disponible|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY: controlar WM_NOTIFY mensajes en aplicaciones MFC

La función `CWnd::OnNotify` controla los mensajes de notificación. Su implementación predeterminada comprueba el mapa de mensajes para que los controladores de notificaciones llamen a. En general, no invalide `OnNotify`. En su lugar, se proporciona una función de controlador y se agrega una entrada de mapa de mensajes para ese controlador al mapa de mensajes de la clase de la ventana propietaria.

ClassWizard, a través de la hoja de propiedades ClassWizard, puede crear el ON_NOTIFY entrada de mapa de mensajes y proporcionar una función de controlador de esqueleto. Para obtener más información sobre el uso de ClassWizard para facilitar esta tarea, consulte [asignación de mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

La macro del mapa de mensajes de ON_NOTIFY tiene la siguiente sintaxis:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

donde los parámetros son:

*wNotifyCode*<br/>
Código para el mensaje de notificación que se va a controlar, como LVN_KEYDOWN.

*identificador*<br/>
Identificador secundario del control para el que se envía la notificación.

*memberFxn*<br/>
Función miembro a la que se llamará cuando se envíe esta notificación.

La función miembro debe declararse con el prototipo siguiente:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

donde los parámetros son:

*pNotifyStruct*<br/>
Puntero a la estructura de notificación, como se describe en la sección anterior.

*result*<br/>
Un puntero al código de resultado que se establecerá antes de devolver.

## <a name="example"></a>Ejemplo

Para especificar que desea que la función miembro `OnKeydownList1` controle los mensajes de LVN_KEYDOWN de la `CListCtrl` cuyo identificador sea `IDC_LIST1`, usaría ClassWizard para agregar lo siguiente al mapa de mensajes:

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

En el ejemplo anterior, la función proporcionada por ClassWizard es:

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Tenga en cuenta que ClassWizard proporciona automáticamente un puntero del tipo adecuado. Puede acceder a la estructura de notificación a través de *pNMHDR* o *pLVKeyDow*.

##  <a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

Si necesita procesar el mismo mensaje de WM_NOTIFY para un conjunto de controles, puede usar ON_NOTIFY_RANGE en lugar de ON_NOTIFY. Por ejemplo, puede tener un conjunto de botones para los que desea realizar la misma acción para un mensaje de notificación determinado.

Cuando se usa ON_NOTIFY_RANGE, se especifica un intervalo contiguo de identificadores secundarios para los que se va a controlar el mensaje de notificación mediante la especificación de los identificadores de inicio y final secundarios del intervalo.

ClassWizard no controla ON_NOTIFY_RANGE; para usarlo, debe modificar el mapa de mensajes.

La entrada del mapa de mensajes y el prototipo de función para ON_NOTIFY_RANGE son los siguientes:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

donde los parámetros son:

*wNotifyCode*<br/>
Código para el mensaje de notificación que se va a controlar, como LVN_KEYDOWN.

*identificador*<br/>
Primer identificador del intervalo contiguo de identificadores.

*idLast*<br/>
Último identificador del intervalo contiguo de identificadores.

*memberFxn*<br/>
Función miembro a la que se llamará cuando se envíe esta notificación.

La función miembro debe declararse con el prototipo siguiente:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

donde los parámetros son:

*identificador*<br/>
Identificador secundario del control que envió la notificación.

*pNotifyStruct*<br/>
Puntero a la estructura de notificación, tal y como se ha descrito anteriormente.

*result*<br/>
Un puntero al código de resultado que se establecerá antes de devolver.

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

Si desea que más de un objeto en el enrutamiento de notificaciones controle un mensaje, puede utilizar ON_NOTIFY_EX (o ON_NOTIFY_EX_RANGE) en lugar de ON_NOTIFY (o ON_NOTIFY_RANGE). La única diferencia entre la versión **ex** y la versión normal es que la función miembro a la que se llama para la versión **ex** devuelve un **booleano** que indica si el procesamiento de mensajes debe continuar o no. Devolver **false** desde esta función permite procesar el mismo mensaje en más de un objeto.

ClassWizard no controla ON_NOTIFY_EX ni ON_NOTIFY_EX_RANGE; Si desea utilizar cualquiera de ellos, debe modificar el mapa de mensajes.

La entrada del mapa de mensajes y el prototipo de función para ON_NOTIFY_EX y ON_NOTIFY_EX_RANGE son los siguientes. Los significados de los parámetros son los mismos que para las versiones no**ex** .

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

El prototipo de las dos opciones anteriores es el mismo:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

En ambos casos, el *identificador* contiene el identificador secundario del control que envió la notificación.

La función debe devolver **true** si el mensaje de notificación se ha controlado por completo o **false** si otros objetos del enrutamiento de comandos deben tener la oportunidad de controlar el mensaje.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
