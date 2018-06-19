---
title: 'TN061: Mensajes ON_NOTIFY y WM_NOTIFY | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: dc8e49ec04e1932c7bac4faa9a8737b480d8ef54
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384741"
---
# <a name="tn061-onnotify-and-wmnotify-messages"></a>TN061: Mensajes ON_NOTIFY y WM_NOTIFY
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota técnica proporciona información general sobre la nueva **WM_NOTIFY** el mensaje y se describe el modo recomendado (y más común) del control de **WM_NOTIFY** mensajes en la aplicación MFC.  
  
 **Mensajes de notificación en Windows 3.x**  
  
 En Windows 3.x, sus elementos primarios de eventos como clics del mouse, notificar a los controles de cambios en contenido y selección y pintura de fondo del control mediante el envío de un mensaje al elemento primario. Las notificaciones de simples se envían como especiales **WM_COMMAND** mensajes, con el código de notificación (como **BN_CLICKED**) y controlar el Id. de empaquetado en `wParam` y el identificador del control en `lParam`. Tenga en cuenta que puesto que `wParam` y `lParam` son completa, no hay ninguna manera de pasar datos adicionales, estos mensajes pueden ser solo notificaciones simple. Por ejemplo, en la **BN_CLICKED** notificación, no hay ninguna manera de enviar información acerca de la ubicación del cursor del mouse cuando se hace clic en el botón.  
  
 Si los controles en Windows 3.x deba enviar un mensaje de notificación que incluye datos adicionales, usan una variedad de mensajes con fines especiales, incluidos los `WM_CTLCOLOR`, `WM_VSCROLL`, `WM_HSCROLL`, `WM_DRAWITEM`, `WM_MEASUREITEM`, `WM_COMPAREITEM`, `WM_DELETEITEM`, `WM_CHARTOITEM`, `WM_VKEYTOITEM`, y así sucesivamente. Estos mensajes se pueden reflejar hacia el control que se enviaron. Para obtener más información, consulte [TN062: reflexión de mensajes para controles de Windows](../mfc/tn062-message-reflection-for-windows-controls.md).  
  
 **Mensajes de notificación en Win32**  
  
 Para los controles que existían en Windows 3.1, la API de Win32 usa la mayoría de los mensajes de notificación que se usaron en Windows 3.x. Sin embargo, Win32 también agrega una serie de controles sofisticados y complejos para aquellos admitidos en Windows 3.x. Con frecuencia, estos controles se necesitan enviar datos adicionales con sus mensajes de notificación. En lugar de agregar un nuevo **WM_\***  del mensaje para cada nueva notificación que necesita datos adicionales, los diseñadores de la API de Win32 que eligió agregar un solo mensaje, **WM_NOTIFY**, que puede pasar cualquiera cantidad de datos adicionales en un modo estandarizado.  
  
 **WM_NOTIFY** mensajes contienen el identificador del control que envía el mensaje `wParam` y un puntero a una estructura en `lParam`. Esta estructura es un **NMHDR** estructura o alguna estructura más grande que tiene un **NMHDR** estructura como su primer miembro. Tenga en cuenta que puesto que la **NMHDR** miembro es el primero, un puntero a esta estructura se puede utilizar como puntero a un **NMHDR** o como un puntero a la estructura mayor dependiendo de cómo se convierte.  
  
 En la mayoría de los casos, el puntero señalará a una estructura mayor y debe convertirlo al usarlo. En algunas notificaciones, como las notificaciones comunes (cuyos nombres empiezan por **NM_**) y el control de información sobre herramientas **TTN_SHOW** y **TTN_POP** notificaciones, es un **NMHDR** estructura que se utiliza realmente.  
  
 El **NMHDR** estructura o el miembro inicial contiene el identificador y el identificador del control que envía el mensaje y el código de notificación (como **TTN_SHOW**). El formato de la **NMHDR** estructura, se muestra a continuación:  
  
```  
typedef struct tagNMHDR {  
    HWND hwndFrom;  
    UINT idFrom;  
    UINT code;  
} NMHDR;  
```  
  
 Para una **TTN_SHOW** mensaje, el **código** miembro se establecería en **TTN_SHOW**.  
  
 La mayoría de las notificaciones pasan un puntero a una estructura más grande que contiene un **NMHDR** estructura como su primer miembro. Por ejemplo, considere la estructura utilizada por el control de vista de lista **LVN_KEYDOWN** mensaje de notificación, que se envía cuando se presiona una tecla en un control de vista de lista. El puntero apunta a un **LV_KEYDOWN** estructura, que se define como se muestra a continuación:  
  
```  
typedef struct tagLV_KEYDOWN {  
    NMHDR hdr;     
    WORD wVKey;    
    UINT flags;    
} LV_KEYDOWN;  
```  
  
 Tenga en cuenta que puesto que la **NMHDR** miembro es el primero en esta estructura, el puntero se le pasó en el mensaje de notificación puede convertirse a ser un puntero a un **NMHDR** o un puntero a un **LV_KEYDOWN** .  
  
 **Las notificaciones comunes a todos los nuevos controles de Windows**  
  
 Algunas notificaciones son comunes a todos los nuevos controles de Windows. Estas notificaciones pasan un puntero a un **NMHDR** estructura.  
  
|Código de notificación|Enviar el mensaje porque|  
|-----------------------|------------------|  
|**NM_CLICK**|Usuario hace clic en el botón primario del mouse en el control|  
|**NM_DBLCLK**|Botón de usuario hace doble clic en primario del mouse en el control|  
|**NM_RCLICK**|Usuario hace clic en el botón secundario del mouse en el control|  
|**NM_RDBLCLK**|Usuario hace doble clic en botón secundario en el control|  
|**NM_RETURN**|Presionada la tecla ENTRAR mientras el control tiene foco de entrada de usuario|  
|**NM_SETFOCUS**|Control tiene foco de entrada|  
|**NM_KILLFOCUS**|Control ha perdido el foco de entrada|  
|**NM_OUTOFMEMORY**|Control no pudo completar una operación porque no había suficiente memoria disponible|  
  
##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON_NOTIFY: Control de mensajes WM_NOTIFY en aplicaciones MFC  
 La función `CWnd::OnNotify` controla los mensajes de notificación. La implementación predeterminada comprueba el mapa de mensajes para controladores de notificación para llamar a. En general, no invalide `OnNotify`. En su lugar, proporcione una función de controlador y agregue una entrada de mapa de mensajes para ese controlador al mapa de mensajes de la clase de la ventana propietaria.  
  
 ClassWizard, a través de la hoja de propiedades de ClassWizard, puede crear el `ON_NOTIFY` entrada de mapa de mensajes y proporcionarle una función de controlador de esqueleto. Para obtener más información sobre el uso de ClassWizard para facilitar esta tarea, vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).  
  
 El `ON_NOTIFY` macros de mapa de mensajes tienen la siguiente sintaxis:  
  
```  
 
ON_NOTIFY(
wNotifyCode  ,  
id  ,
    memberFxn)  
 
```  
  
 donde los parámetros en cursiva se reemplazan con:  
  
 `wNotifyCode`  
 El código para el mensaje de notificación se ocuparán de, como **LVN_KEYDOWN**.  
  
 `id`  
 El identificador de elemento secundario del control para el que se envía la notificación.  
  
 `memberFxn`  
 La función miembro se llama cuando se envía esta notificación.  
  
 La función miembro debe declararse con el prototipo siguiente:  
  
```  
 
afx_msg void  
memberFxn  
(NMHDR* 
pNotifyStruct  , LRESULT* result);

 
```  
  
## <a name="remarks"></a>Comentarios  
 donde los parámetros en cursiva son:  
  
 `pNotifyStruct`  
 Un puntero a la estructura de notificación, tal como se describe en la sección anterior.  
  
 *Resultado*  
 Un puntero en el código de resultado se configuran antes de volver.  
  
## <a name="example"></a>Ejemplo  
 Para especificar que desea que la función miembro `OnKeydownList1` para controlar **LVN_KEYDOWN** mensajes desde el `CListCtrl` cuyo identificador es `IDC_LIST1`, usaría ClassWizard agregar lo siguiente a su mapa de mensajes:  
  
```  
ON_NOTIFY(LVN_KEYDOWN,
    IDC_LIST1,
    OnKeydownList1)  
```  
  
 En el ejemplo anterior, la función proporcionada por ClassWizard es:  
  
```  
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)  
{  
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR; *// TODO: Add your control notification handler *//       code here  
 
 *pResult = 0;  
}  
```  
  
 Tenga en cuenta que ClassWizard proporciona automáticamente un puntero del tipo adecuado. Puede tener acceso a la estructura de notificación a través `pNMHDR` o `pLVKeyDow`.  
  
##  <a name="_mfcnotes_on_notify_range"></a> ON_NOTIFY_RANGE  
 Si tiene que procesar el mismo **WM_NOTIFY** mensaje para un conjunto de controles, puede usar **ON_NOTIFY_RANGE** en lugar de `ON_NOTIFY`. Por ejemplo, puede tener un conjunto de botones que desea realizar la misma acción para un determinado mensaje de notificación.  
  
 Cuando usas **ON_NOTIFY_RANGE**, especifique un intervalo contiguo de identificadores de elemento secundario para el que se va a controlar el mensaje de notificación especifica el inicio y final de identificadores de elemento secundario del intervalo.  
  
 No controla ClassWizard **ON_NOTIFY_RANGE**; para utilizarla, debe editar el mapa de mensajes por sí mismo.  
  
 El prototipo de mapa de mensajes de entrada y la función de **ON_NOTIFY_RANGE** son los siguientes:  
  
```  
 
ON_NOTIFY_RANGE(
wNotifyCode  ,   
id  ,   
idLast  ,
    memberFxn)  
 
```  
  
 donde los parámetros en cursiva se reemplazan con:  
  
 `wNotifyCode`  
 El código para el mensaje de notificación se ocuparán de, como **LVN_KEYDOWN**.  
  
 `id`  
 El primer identificador en el intervalo contiguo de identificadores.  
  
 `idLast`  
 Identificador de la última en el intervalo contiguo de identificadores.  
  
 `memberFxn`  
 La función miembro se llama cuando se envía esta notificación.  
  
 La función miembro debe declararse con el prototipo siguiente:  
  
```  
 
afx_msg void  
memberFxn  
(UINT   
id  ,
    NMHDR* 
pNotifyStruct  ,
    LRESULT* result);

 
```  
  
## <a name="remarks"></a>Comentarios  
 donde los parámetros en cursiva son:  
  
 `id`  
 El identificador de elemento secundario del control que envía la notificación.  
  
 `pNotifyStruct`  
 Un puntero a la estructura de notificación, como se describió anteriormente.  
  
 *Resultado*  
 Un puntero en el código de resultado se configuran antes de volver.  
  
##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE  
 Si desea que más de un objeto en la notificación de enrutamiento para controlar un mensaje, puede usar **ON_NOTIFY_EX** (o **ON_NOTIFY_EX_RANGE**) en lugar de `ON_NOTIFY` (o **ON_NOTIFY_RANGE** ). La única diferencia entre el **EX** versión y la versión normal es que llama a la función miembro para el **EX** versión devuelve un **BOOL** que indica si o no debe continuar el procesamiento de mensajes. Devolver **FALSE** de esta función permite procesar el mismo mensaje en más de un objeto.  
  
 No controla ClassWizard **ON_NOTIFY_EX** o **ON_NOTIFY_EX_RANGE**; si desea utilizar cualquiera de ellos, debe editar el mapa de mensajes por sí mismo.  
  
 El prototipo de mapa de mensajes de entrada y la función de **ON_NOTIFY_EX** y **ON_NOTIFY_EX_RANGE** son los siguientes. Los significados de los parámetros son los mismos que no es**EX** versiones.  
  
```  
 
ON_NOTIFY_EX(
nCode  ,  
id  ,
    memberFxn) ON_NOTIFY_EX_RANGE(
wNotifyCode  ,   
id  ,   
idLast  ,
    memberFxn)  
 
```  
  
 El prototipo para ambos de los pasos anteriores es el mismo:  
  
```  
 
afx_msg BOOL  
memberFxn  
(UINT   
id  ,
    NMHDR* 
pNotifyStruct  ,
    LRESULT* result);

 
```  
  
## <a name="remarks"></a>Comentarios  
 En ambos casos, `id` contiene el identificador de elemento secundario del control que envía la notificación.  
  
 La función debe devolver **TRUE** si el mensaje de notificación se ha controlado completamente o **FALSE** si otros objetos en el enrutamiento de comandos deben tener una oportunidad para controlar el mensaje.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

