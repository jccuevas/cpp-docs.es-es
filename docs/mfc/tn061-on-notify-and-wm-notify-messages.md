---
title: 'TN061: Mensajes ON_NOTIFY y Wm_notify | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
dev_langs:
- C++
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2395cb7b1f3d719fd64494ee9b9c7c64ba222bac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381834"
---
# <a name="tn061-onnotify-and-wmnotify-messages"></a>TN061: Mensajes ON_NOTIFY y WM_NOTIFY

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota técnica proporciona información general sobre el nuevo mensaje WM_NOTIFY y describe el modo recomendado (y más común) de tratamiento de mensajes WM_NOTIFY en la aplicación MFC.

**Mensajes de notificación en Windows 3.x**

En Windows 3.x, controles notifique a sus elementos primarios de eventos, como clics del mouse, los cambios en contenido y la selección y el dibujo del control en segundo plano mediante el envío de un mensaje con el elemento primario. Simple notificaciones se envían como mensajes WM_COMMAND especiales, con el código de notificación (por ejemplo, BN_CLICKED) y controlar el Id. que se empaquetan en *wParam* y el identificador del control en *lParam*. Tenga en cuenta que puesto que *wParam* y *lParam* está lleno, no hay ninguna manera de pasar datos adicionales, estos mensajes pueden ser de solo notificación simple. Por ejemplo, en la notificación BN_CLICKED, no hay ninguna manera de enviar información acerca de la ubicación del cursor del mouse cuando se hizo clic en el botón.

Cuando los controles en Windows 3.x deba envían un mensaje de notificación que incluye datos adicionales, usan una variedad de mensajes con una finalidad especial, incluyendo WM_CTLCOLOR, WM_VSCROLL, mensajes WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM WM_DELETEITEM, WM_ CHARTOITEM, WM_VKEYTOITEM y así sucesivamente. Estos mensajes se pueden reflejar al control que les enviado. Para obtener más información, consulte [TN062: reflexión de mensajes para controles de Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

**Mensajes de notificación en Win32**

Para los controles que existían en Windows 3.1, la API Win32 utiliza la mayoría de los mensajes de notificación que se usaron en Windows 3.x. Sin embargo, Win32 también agrega una serie de controles sofisticados y complejos a los que se admite en Windows 3.x. Con frecuencia, estos controles deben enviar datos adicionales con sus mensajes de notificación. En lugar de agregar un nuevo **WM_** <strong>\*</strong> del mensaje para cada nueva notificación que necesita datos adicionales, los diseñadores de la API Win32 decidió agregar un solo mensaje, WM_NOTIFY, que puede pasar cualquiera cantidad de datos adicionales en un modo estandarizado.

Mensajes WM_NOTIFY contienen el identificador del control que envía el mensaje *wParam* y un puntero a una estructura en *lParam*. Esta estructura es un **NMHDR** estructura o alguna estructura más grande que tiene un **NMHDR** estructura como su primer miembro. Tenga en cuenta que debido a que el **NMHDR** miembro es el primero, un puntero a esta estructura se puede usar como un puntero a un **NMHDR** o como un puntero a la estructura de mayor tamaño dependiendo de cómo convertirlo.

En la mayoría de los casos, el puntero señalará a una estructura más grande y tendrá que convertirlo al usarlo. En algunas notificaciones, como las notificaciones comunes (cuyos nombres empiezan por **NM_**) y la herramienta de sugerencia del control TTN_SHOW y TTN_POP notificaciones, es un **NMHDR** estructura usado realmente.

El **NMHDR** estructura o un miembro inicial que contiene el identificador y el identificador del control que envía el mensaje y el código de notificación (por ejemplo, TTN_SHOW). El formato de la **NMHDR** estructura se muestra a continuación:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Para un mensaje TTN_SHOW, el **código** miembro se establecería en TTN_SHOW.

La mayoría de las notificaciones pasan un puntero a una estructura más grande que contiene un **NMHDR** estructura como su primer miembro. Por ejemplo, considere la estructura de mensaje de notificación LVN_KEYDOWN del control de vista de lista, que se envía cuando se presiona una tecla en un control de vista de lista. El puntero apunta a un **LV_KEYDOWN** estructura, que se define como se muestra a continuación:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Tenga en cuenta que debido a que el **NMHDR** miembro es la primero de esta estructura, el puntero se pasan en el mensaje de notificación se puede convertir en un puntero a un **NMHDR** o un puntero a un **LV_KEYDOWN** .

**Las notificaciones comunes a todos los nuevos controles de Windows**

Algunas notificaciones son comunes a todos los nuevos controles de Windows. Estas notificaciones pasan un puntero a un **NMHDR** estructura.

|Código de notificación|Puede enviar porque|
|-----------------------|------------------|
|NM_CLICK|Usuario hizo clic en el botón primario del mouse en el control|
|NM_DBLCLK|Usuario hace doble clic en botón izquierdo del control|
|NM_RCLICK|Usuario hizo clic en el botón secundario del mouse en el control|
|NM_RDBLCLK|Usuario hace doble clic en botón secundario en el control|
|NM_RETURN|Usuario ha presionado la tecla ENTRAR mientras el control tiene foco de entrada|
|NM_SETFOCUS|Control ha recibido el foco de entrada|
|NM_KILLFOCUS|Control ha perdido el foco de entrada|
|NM_OUTOFMEMORY|Control no pudo completar una operación porque no había suficiente memoria disponible|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON_NOTIFY: Control de mensajes WM_NOTIFY en aplicaciones MFC

La función `CWnd::OnNotify` controla los mensajes de notificación. Su implementación predeterminada comprueba el mapa de mensajes para llamar a los controladores de notificación. En general, no se invalidan `OnNotify`. En su lugar, proporcione una función de controlador y agregue una entrada de mapa de mensajes para ese controlador para el mapa de mensajes de la clase de la ventana propietaria.

ClassWizard a través de la hoja de propiedades ClassWizard, puede crear la entrada de mapa de mensajes ON_NOTIFY y proporcionarle una función de controlador de esqueleto. Para obtener más información sobre el uso de ClassWizard para facilitar esta tarea, vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

La macro de mapa de mensajes ON_NOTIFY tiene la siguiente sintaxis:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

donde los parámetros son:

*wNotifyCode*<br/>
El código para el mensaje de notificación se administran como LVN_KEYDOWN.

*identificador*<br/>
El identificador de elemento secundario del control para el que se envía la notificación.

*memberFxn*<br/>
La función miembro que se llamará cuando se envía esta notificación.

La función miembro debe declararse con el prototipo siguiente:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

donde los parámetros son:

*pNotifyStruct*<br/>
Un puntero a la estructura de notificación, como se describe en la sección anterior.

*Resultado*<br/>
Un puntero para el código de resultado establecerá antes de volver.

## <a name="example"></a>Ejemplo

Para especificar que desea que la función miembro `OnKeydownList1` para controlar los mensajes LVN_KEYDOWN desde el `CListCtrl` cuyo identificador es `IDC_LIST1`, usaría ClassWizard agregar lo siguiente en el mapa de mensajes:

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

Tenga en cuenta que ClassWizard proporciona un puntero del tipo correcto automáticamente. Puede tener acceso a la estructura de notificación a través de una *pNMHDR* o *pLVKeyDow*.

##  <a name="_mfcnotes_on_notify_range"></a> ON_NOTIFY_RANGE

Si tiene que procesar el mismo mensaje WM_NOTIFY de un conjunto de controles, puede usar ON_NOTIFY_RANGE lugar ON_NOTIFY. Por ejemplo, puede tener un conjunto de botones para el que desea realizar la misma acción para un determinado mensaje de notificación.

Cuando usas ON_NOTIFY_RANGE, especifique un intervalo contiguo de identificadores de secundarios para que se va a controlar el mensaje de notificación especifica el inicio y final de los identificadores de elemento secundario del intervalo.

ClassWizard no controla ON_NOTIFY_RANGE; Para ello, deberá editar el mapa de mensajes por sí mismo.

La entrada de mapa de mensajes y el prototipo de función para ON_NOTIFY_RANGE son los siguientes:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

donde los parámetros son:

*wNotifyCode*<br/>
El código para el mensaje de notificación se administran como LVN_KEYDOWN.

*identificador*<br/>
El primer identificador en el intervalo de identificadores contiguo.

*idLast*<br/>
Identificador de la última en el intervalo de identificadores contiguo.

*memberFxn*<br/>
La función miembro que se llamará cuando se envía esta notificación.

La función miembro debe declararse con el prototipo siguiente:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

donde los parámetros son:

*identificador*<br/>
El identificador de elemento secundario del control que envía la notificación.

*pNotifyStruct*<br/>
Un puntero a la estructura de notificación, como se describió anteriormente.

*Resultado*<br/>
Un puntero para el código de resultado establecerá antes de volver.

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

Si desea más de un objeto en el enrutamiento para controlar un mensaje de notificación, puede usar ON_NOTIFY_EX (o ON_NOTIFY_EX_RANGE) en lugar de ON_NOTIFY (o ON_NOTIFY_RANGE). La única diferencia entre el **EX** versión y la versión normal es que la función miembro llama para el **EX** versión devuelve un **BOOL** que indica si debe continuar el procesamiento de mensajes. Devolver **FALSE** desde esta función le permite procesar el mismo mensaje en más de un objeto.

ClassWizard no controla ON_NOTIFY_EX o ON_NOTIFY_EX_RANGE; Si desea utilizar cualquiera de ellos, deberá editar el mapa de mensajes por sí mismo.

La entrada de mapa de mensajes y el prototipo de función para ON_NOTIFY_EX y ON_NOTIFY_EX_RANGE son los siguientes. Los significados de los parámetros son los mismos que para que no sea**EX** versiones.

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

El prototipo para ambos lo anterior es el mismo:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

En ambos casos, *identificador* contiene el identificador de elemento secundario del control que envía la notificación.

La función debe devolver **TRUE** si se ha controlado completamente el mensaje de notificación o **FALSE** si otros objetos en el enrutamiento de comandos deben tener una oportunidad para controlar el mensaje.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
