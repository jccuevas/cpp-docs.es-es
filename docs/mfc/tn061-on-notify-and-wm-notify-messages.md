---
title: "TN061: Mensajes ON_NOTIFY y WM_NOTIFY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_NOTIFY"
  - "WM_NOTIFY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mensajes de notificación"
  - "ON_NOTIFY (mensaje)"
  - "ON_NOTIFY_EX (mensaje)"
  - "ON_NOTIFY_EX_RANGE (mensaje)"
  - "ON_NOTIFY_RANGE (mensaje)"
  - "TN061"
  - "WM_NOTIFY (mensaje)"
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN061: Mensajes ON_NOTIFY y WM_NOTIFY
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota técnica proporciona información adicional en el nuevo mensaje de **WM\_NOTIFY** y describe \(y utilizado\) la manera recomendada de controlar mensajes de **WM\_NOTIFY** en la aplicación MFC.  
  
 **Mensajes de notificación de Windows 3.x**  
  
 En Windows 3.x, los controles notifican a los elementos primarios de eventos como los clics, los cambios en el contenido y selección, y dibujo del fondo del control enviando un mensaje al elemento primario.  Las notificaciones simples se envían como mensajes especiales de **WM\_COMMAND** , con el código de notificación \(como **BN\_CLICKED**\) y el identificador de control empaquetado en `wParam` y el identificador de control en `lParam`.  Observe que desde `wParam` y `lParam` está lleno, no hay ninguna manera de pasar ningún dato adicionales — estos mensajes pueden ser sólo notificación simple.  Por ejemplo, en la notificación de **BN\_CLICKED** , no hay ninguna manera de enviar información sobre la ubicación del cursor cuando se hizo clic en el botón.  
  
 Cuando los controles de Windows 3.x deben enviar un mensaje de notificación que incluye datos adicionales, utilice una variedad de mensajes especial, incluidos `WM_CTLCOLOR`, `WM_VSCROLL`, `WM_HSCROLL`, `WM_DRAWITEM`, `WM_MEASUREITEM`, `WM_COMPAREITEM`, `WM_DELETEITEM`, `WM_CHARTOITEM`, `WM_VKEYTOITEM`, etc.  Estos mensajes se pueden reflejar de nuevo al control que los envió.  Para obtener más información, vea [TN062: Mensaje Reflexión para Controles de Windows](../mfc/tn062-message-reflection-for-windows-controls.md).  
  
 **Mensajes de notificación en Win32**  
  
 Para los controles que existían en Windows 3.1, la API Win32 utiliza la mayoría de los mensajes de notificación utilizados en Windows 3.x.  Sin embargo, Win32 también agrega varios complejo, los controles complejos a los admitidos en Windows 3.x.  Con frecuencia, necesidad de estos controles de enviar datos adicionales con los mensajes de notificación.  En lugar de agregar un nuevo mensaje de **WM\_\*** para cada nueva notificación que necesita datos adicionales, los diseñadores de la API Win32 eligieron para agregar un único mensaje, **WM\_NOTIFY**, que pueden pasar cualquier cantidad de datos adicionales en un modo estandarizado.  
  
 Los mensajes de**WM\_NOTIFY** contienen el identificador del control que envía el mensaje en `wParam` y un puntero a una estructura en `lParam`.  Esta estructura es una estructura de **NMHDR** o de alguna estructura mayor que tiene una estructura de **NMHDR** como primer miembro.  Observe que ya que el miembro de **NMHDR** es primero, un puntero a esta estructura puede utilizarse como puntero a **NMHDR** o como un puntero a la estructura mayor dependiendo de cómo se convierte.  
  
 En la mayoría de los casos, el puntero señalará a una estructura mayor y deberá conviértalo cuando se usa.  Sólo en algunas notificaciones, como las notificaciones de notificaciones \(cuyos nombres empiezan con **NM\_**\) y de **TTN\_SHOW** y de **TTN\_POP** de control tooltip, es una estructura de **NMHDR** utilizada realmente.  
  
 La estructura de **NMHDR** o miembro inicial contiene el identificador y el identificador del control que envía el mensaje y el código de notificación \(como **TTN\_SHOW**\).  El formato de la estructura de **NMHDR** se muestra a continuación:  
  
```  
typedef struct tagNMHDR {  
    HWND hwndFrom;  
    UINT idFrom;  
    UINT code;  
} NMHDR;  
```  
  
 Para un mensaje de **TTN\_SHOW** , establecerán al miembro de **code** a **TTN\_SHOW**.  
  
 La mayoría de las notificaciones pasan un puntero a una estructura más grande que contiene una estructura de **NMHDR** como primer miembro.  Por ejemplo, considere la estructura utilizada por el mensaje de notificación de **LVN\_KEYDOWN** del control de vista de lista, se envía a una clave se clava un control de vista de lista.  Los puntos de puntero a una estructura de **LV\_KEYDOWN** , que se define como se muestra a continuación:  
  
```  
typedef struct tagLV_KEYDOWN {  
    NMHDR hdr;     
    WORD wVKey;    
    UINT flags;    
} LV_KEYDOWN;  
```  
  
 Observe que ya que el miembro de **NMHDR** es el primero en esta estructura, el puntero que se pasa en el mensaje de notificación puede ser echado a un puntero a **NMHDR** o puntero a **LV\_KEYDOWN**.  
  
 **Notificaciones comunes a Controles nuevos Windows**  
  
 Algunas notificaciones son comunes a todos los controles de Windows.  Estas notificaciones pasan un puntero a una estructura de **NMHDR** .  
  
|Código de notificación|Enviado porque|  
|----------------------------|--------------------|  
|**NM\_CLICK**|El usuario hizo clic en el botón primario en el control|  
|**NM\_DBLCLK**|El usuario hace doble clic en el botón primario en el control|  
|**NM\_RCLICK**|El usuario hizo clic con el botón secundario del mouse en el control|  
|**NM\_RDBLCLK**|El usuario hizo doble clic con el botón secundario del mouse en el control|  
|**NM\_RETURN**|El usuario presionó la tecla ENTRAR cuando el control tiene el foco de entrada|  
|**NM\_SETFOCUS**|El Control se ha definido el foco de entrada|  
|**NM\_KILLFOCUS**|El Control ha perdido el foco de entrada|  
|**NM\_OUTOFMEMORY**|El Control no puede completar una operación porque no hay memoria suficiente disponible|  
  
##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON\_NOTIFY: Administrar mensajes de WM\_NOTIFY en aplicaciones MFC  
 Los mensajes de notificación de los identificadores de `CWnd::OnNotify` de la función.  La implementación predeterminada comprueba el mapa de mensajes para que los controladores de notificación llamen.  No reemplaza normalmente `OnNotify`.  En su lugar, proporciona una función controladora y agrega una entrada de mensaje\- mapa para ese controlador el mapa de mensajes de la clase de la ventana propietaria.  
  
 Pero, a través de la hoja de propiedades de ClassWizard, puede crear la entrada de mensaje\- mapa de `ON_NOTIFY` y proporcionarle con una función esquemática del controlador.  Para obtener más información sobre cómo utilizar ClassWizard para facilitar este, vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).  
  
 La macro de mensaje\- mapa de `ON_NOTIFY` tiene la siguiente sintaxis:  
  
```  
  
ON_NOTIFY( wNotifyCode, id, memberFxn )  
```  
  
 donde los parámetros título en cursivas se reemplazan:  
  
 `wNotifyCode`  
 El código para que el mensaje de notificación es administrado, por ejemplo **LVN\_KEYDOWN**.  
  
 `id`  
 El identificador secundario del control para el que se envía la notificación.  
  
 `memberFxn`  
 La función miembro que se llamará cuando se envía esta notificación.  
  
 La función miembro se debe declarar con el siguiente prototipo:  
  
```  
  
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );  
```  
  
## Comentarios  
 donde los parámetros título en cursivas:  
  
 `pNotifyStruct`  
 Un puntero a la estructura de notificación, como se describe en la sección anterior.  
  
 *result*  
 Un puntero al código de resultado que establecerá antes de volver.  
  
## Ejemplo  
 Para especificar que la función `OnKeydownList1` miembro para controlar los mensajes de **LVN\_KEYDOWN** de `CListCtrl` cuyo identificador es `IDC_LIST1`, utilizaría ClassWizard para agregar lo siguiente al mapa de mensajes:  
  
```  
ON_NOTIFY( LVN_KEYDOWN, IDC_LIST1, OnKeydownList1 )  
```  
  
 En el ejemplo anterior, la función proporcionada por ClassWizard es:  
  
```  
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)  
{  
   LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;  
   // TODO: Add your control notification handler  
   //       code here  
  
   *pResult = 0;  
}  
```  
  
 Observe que ClassWizard proporciona un puntero de tipo adecuado automáticamente.  Puede tener acceso a la estructura de notificación con `pNMHDR` o `pLVKeyDow`.  
  
##  <a name="_mfcnotes_on_notify_range"></a> ON\_NOTIFY\_RANGE  
 Si necesita procesar el mismo mensaje de **WM\_NOTIFY** para un conjunto de controles, puede usar **ON\_NOTIFY\_RANGE** en lugar de `ON_NOTIFY`.  Por ejemplo, puede tener un conjunto de botones para los que desea realizar la misma acción para el mensaje de notificación.  
  
 Cuando se utiliza **ON\_NOTIFY\_RANGE**, puede especificar un intervalo contiguo de identificadores secundarios para que controlen el mensaje de notificación especificando los identificadores secundarios inicial y final del intervalo.  
  
 Pero no administra **ON\_NOTIFY\_RANGE**; para utilizarlo, debe editar el mensaje se asigna.  
  
 El prototipo de la entrada y la función de mensaje\- mapa para **ON\_NOTIFY\_RANGE** es la siguiente:  
  
```  
  
ON_NOTIFY_RANGE(   
wNotifyCode  
,   
id  
,   
idLast  
,   
memberFxn  
 )  
  
```  
  
 donde los parámetros título en cursivas se reemplazan:  
  
 `wNotifyCode`  
 El código para que el mensaje de notificación es administrado, por ejemplo **LVN\_KEYDOWN**.  
  
 `id`  
 El primer identificador en el intervalo contiguo de identificadores.  
  
 `idLast`  
 El identificador pasado en el intervalo contiguo de identificadores.  
  
 `memberFxn`  
 La función miembro que se llamará cuando se envía esta notificación.  
  
 La función miembro se debe declarar con el siguiente prototipo:  
  
```  
  
afx_msg void memberFxn( UINT id, NMHDR * pNotifyStruct, LRESULT * result );  
```  
  
## Comentarios  
 donde los parámetros título en cursivas:  
  
 `id`  
 El identificador secundario del control que envió la notificación.  
  
 `pNotifyStruct`  
 Un puntero a la estructura de notificación, como se ha descrito anteriormente.  
  
 *result*  
 Un puntero al código de resultado que establecerá antes de volver.  
  
##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON\_NOTIFY\_EX, ON\_NOTIFY\_EX\_RANGE  
 Si desea más de un objeto en el enrutamiento de notificación para controlar un mensaje, puede utilizar **ON\_NOTIFY\_EX** \(o **ON\_NOTIFY\_EX\_RANGE**\) en lugar de `ON_NOTIFY` \(o **ON\_NOTIFY\_RANGE**\).  La única diferencia entre la versión de **EX** y la versión regular es que la función miembro denominada para la versión de **EX** devuelve **bool** que indica si el procesamiento de mensajes debe continuar.  Devolver **FALSE** de esta función permite procesar el mismo mensaje en más de un objeto.  
  
 Pero no administra **ON\_NOTIFY\_EX** o **ON\_NOTIFY\_EX\_RANGE**; si desea utilizar cualquiera de ellos, debe editar el mensaje se asigna.  
  
 El prototipo de la entrada y la función de mensaje\- mapa para **ON\_NOTIFY\_EX** y **ON\_NOTIFY\_EX\_RANGE** son los siguientes.  El significado de los parámetros son los mismos que para las versiones no de**EX** .  
  
```  
  
ON_NOTIFY_EX( nCode, id, memberFxn ) ON_NOTIFY_EX_RANGE( wNotifyCode, id, idLast, memberFxn )  
```  
  
 El prototipo para ambos anterior es el mismo:  
  
```  
  
afx_msg BOOL memberFxn( UINT id, NMHDR * pNotifyStruct, LRESULT * result );  
```  
  
## Comentarios  
 En ambos casos, `id` contiene el identificador secundario del control que envió la notificación.  
  
 La función debe devolver **VERDADERO** si el mensaje de notificación se ha controlado completamente o **FALSE** si otros objetos en el enrutamiento de comandos tienen la oportunidad de controlar el mensaje.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)