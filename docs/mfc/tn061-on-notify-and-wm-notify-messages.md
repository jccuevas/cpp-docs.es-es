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
ms.openlocfilehash: 845558dad6b9f6e820c759cb83fce2c6cbceaa0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366597"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061: Mensajes ON_NOTIFY y WM_NOTIFY

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota técnica proporciona información general sobre el nuevo mensaje de WM_NOTIFY y describe la forma recomendada (y más común) de controlar WM_NOTIFY mensajes en la aplicación MFC.

**Mensajes de notificación en Windows 3.x**

En Windows 3.x, los controles notifican a sus padres eventos como clics del mouse, cambios en el contenido y la selección, y controlan la pintura en segundo plano enviando un mensaje al elemento primario. Las notificaciones simples se envían como mensajes especiales WM_COMMAND, con el código de notificación (como BN_CLICKED) y el identificador de control empaquetado en *wParam* y el identificador del control en *lParam*. Tenga en cuenta que, dado que *wParam* y *lParam* están llenos, no hay manera de pasar ningún dato adicional: estos mensajes pueden ser solo una notificación simple. Por ejemplo, en la notificación de BN_CLICKED, no hay forma de enviar información sobre la ubicación del cursor del mouse cuando se hizo clic en el botón.

Cuando los controles de Windows 3.x necesitan enviar un mensaje de notificación que incluye datos adicionales, usan una variedad de mensajes de propósito especial, incluidos WM_CTLCOLOR, WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_CHARTOITEM, WM_VKEYTOITEM, etc. Estos mensajes se pueden reflejar en el control que los envió. Para obtener más información, vea [TN062: Reflexión de](../mfc/tn062-message-reflection-for-windows-controls.md)mensajes para controles de Windows .

**Mensajes de notificación en Win32**

Para los controles que existían en Windows 3.1, la API de Win32 usa la mayoría de los mensajes de notificación que se usaron en Windows 3.x. Sin embargo, Win32 también agrega una serie de controles sofisticados y complejos a los admitidos en Windows 3.x. Con frecuencia, estos controles deben enviar datos adicionales con sus mensajes de notificación. En lugar de agregar un nuevo mensaje **de WM_** <strong>\*</strong> para cada nueva notificación que necesita datos adicionales, los diseñadores de la API de Win32 optaron por agregar solo un mensaje, WM_NOTIFY, que puede pasar cualquier cantidad de datos adicionales de forma estandarizada.

WM_NOTIFY mensajes contienen el identificador del control que envía el mensaje en *wParam* y un puntero a una estructura en *lParam*. Esta estructura es una estructura **NMHDR** o alguna estructura más grande que tiene una estructura **NMHDR** como su primer miembro. Tenga en cuenta que puesto que el miembro **NMHDR** es primero, un puntero a esta estructura se puede utilizar como puntero a un **NMHDR** o como puntero a la estructura más grande dependiendo de cómo se la convierta.

En la mayoría de los casos, el puntero apuntará a una estructura más grande y tendrá que lanzarla cuando la use. En sólo unas pocas notificaciones, como las notificaciones comunes (cuyos nombres comienzan con **NM_)** y las notificaciones de TTN_SHOW y TTN_POP del control de información sobre herramientas, es una estructura **NMHDR** realmente utilizada.

La estructura **NMHDR** o el miembro inicial contiene el identificador y el identificador del control que envía el mensaje y el código de notificación (por ejemplo, TTN_SHOW). El formato de la estructura **NMHDR** se muestra a continuación:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Para un mensaje de TTN_SHOW, el miembro de **código** se establecería en TTN_SHOW.

La mayoría de las notificaciones pasan un puntero a una estructura más grande que contiene una estructura **NMHDR** como su primer miembro. Por ejemplo, tenga en cuenta la estructura utilizada por el mensaje de notificación LVN_KEYDOWN del control de vista de lista, que se envía cuando se presiona una tecla en un control de vista de lista. El puntero apunta a una estructura **LV_KEYDOWN,** que se define como se muestra a continuación:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Tenga en cuenta que puesto que el miembro **NMHDR** es el primero en esta estructura, el puntero que se pasa en el mensaje de notificación se puede convertir a un puntero a un **NMHDR** o un puntero a un **LV_KEYDOWN**.

**Notificaciones comunes a todos los nuevos controles de Windows**

Algunas notificaciones son comunes a todos los nuevos controles de Windows. Estas notificaciones pasan un puntero a una estructura **NMHDR.**

|Código de notificación|Enviado porque|
|-----------------------|------------------|
|NM_CLICK|El usuario ha clic en el botón izquierdo del ratón en el control|
|NM_DBLCLK|El usuario ha pulsado dos clics en el botón izquierdo del ratón en el control|
|NM_RCLICK|El usuario ha pulsado el botón derecho del ratón en el control|
|NM_RDBLCLK|El usuario ha pulsado dos clics con el botón derecho del ratón en el control|
|NM_RETURN|El usuario presiona la tecla ENTER mientras el control tiene el foco de entrada|
|NM_SETFOCUS|Se ha dado control al enfoque de entrada|
|NM_KILLFOCUS|El control ha perdido el enfoque de entrada|
|NM_OUTOFMEMORY|El control no pudo completar una operación porque no había suficiente memoria disponible|

## <a name="on_notify-handling-wm_notify-messages-in-mfc-applications"></a><a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY: Manejo de mensajes WM_NOTIFY en aplicaciones MFC

La `CWnd::OnNotify` función controla los mensajes de notificación. Su implementación predeterminada comprueba el mapa de mensajes para que los controladores de notificación llamen. En general, no `OnNotify`se reemplaza . En su lugar, proporcione una función de controlador y agregue una entrada de mapa de mensajes para ese controlador al mapa de mensajes de la clase de la ventana de propietario.

ClassWizard, a través de la hoja de propiedades ClassWizard, puede crear la entrada de mapa de mensajes ON_NOTIFY y proporcionarle una función de controlador de esqueleto. Para obtener más información sobre el uso de ClassWizard para facilitar esto, vea Asignación de [mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

La macro de mapa de mensajes ON_NOTIFY tiene la sintaxis siguiente:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

donde los parámetros son:

*wNotifyCode*<br/>
El código del mensaje de notificación que se va a controlar, como LVN_KEYDOWN.

*id*<br/>
Identificador secundario del control para el que se envía la notificación.

*memberFxn*<br/>
La función miembro que se llamará cuando se envía esta notificación.

La función miembro debe declararse con el siguiente prototipo:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

donde los parámetros son:

*pNotifyStruct*<br/>
Un puntero a la estructura de notificación, como se describe en la sección anterior.

*Resultado*<br/>
Un puntero al código de resultado que establecerá antes de volver.

## <a name="example"></a>Ejemplo

Para especificar que desea `OnKeydownList1` que la función `CListCtrl` miembro `IDC_LIST1`controle LVN_KEYDOWN mensajes del cuyo identificador es , usaría ClassWizard para agregar lo siguiente al mapa de mensajes:

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

Tenga en cuenta que ClassWizard proporciona un puntero del tipo adecuado automáticamente. Puede acceder a la estructura de notificaciones a través de *pNMHDR* o *pLVKeyDow*.

## <a name="on_notify_range"></a><a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

Si necesita procesar el mismo mensaje de WM_NOTIFY para un conjunto de controles, puede usar ON_NOTIFY_RANGE en lugar de ON_NOTIFY. Por ejemplo, es posible que tenga un conjunto de botones para los que desea realizar la misma acción para un mensaje de notificación determinado.

Cuando se usa ON_NOTIFY_RANGE, se especifica un intervalo contiguo de identificadores secundarios para los que se controlará el mensaje de notificación especificando los identificadores secundarios inicial y final del intervalo.

ClassWizard no controla ON_NOTIFY_RANGE; para usarlo, necesita editar su mapa de mensajes usted mismo.

La entrada de mapa de mensajes y el prototipo de función para ON_NOTIFY_RANGE son los siguientes:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

donde los parámetros son:

*wNotifyCode*<br/>
El código del mensaje de notificación que se va a controlar, como LVN_KEYDOWN.

*id*<br/>
El primer identificador en el intervalo contiguo de identificadores.

*idLast*<br/>
El último identificador del intervalo contiguo de identificadores.

*memberFxn*<br/>
La función miembro que se llamará cuando se envía esta notificación.

La función miembro debe declararse con el siguiente prototipo:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

donde los parámetros son:

*id*<br/>
Identificador secundario del control que envió la notificación.

*pNotifyStruct*<br/>
Un puntero a la estructura de notificación, como se describió anteriormente.

*Resultado*<br/>
Un puntero al código de resultado que establecerá antes de volver.

## <a name="on_notify_ex-on_notify_ex_range"></a><a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

Si desea que más de un objeto del enrutamiento de notificaciones controle un mensaje, puede usar ON_NOTIFY_EX (o ON_NOTIFY_EX_RANGE) en lugar de ON_NOTIFY (o ON_NOTIFY_RANGE). La única diferencia entre la versión **EX** y la versión regular es que la función miembro llamada para la versión **EX** devuelve un **BOOL** que indica si el procesamiento de mensajes debe continuar o no. Devolver **FALSE** desde esta función le permite procesar el mismo mensaje en más de un objeto.

ClassWizard no controla ON_NOTIFY_EX ni ON_NOTIFY_EX_RANGE; si desea utilizar cualquiera de ellos, debe editar su mapa de mensajes usted mismo.

La entrada de mapa de mensajes y el prototipo de función para ON_NOTIFY_EX y ON_NOTIFY_EX_RANGE son los siguientes. Los significados de los parámetros son los mismos que para las versiones que no**son EX.**

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

El prototipo para ambos de los anteriores es el mismo:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

En ambos casos, *id* contiene el identificador secundario del control que envió la notificación.

La función debe devolver **TRUE** si el mensaje de notificación se ha controlado completamente o **FALSE** si otros objetos en el enrutamiento de comandos deben tener la oportunidad de controlar el mensaje.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
