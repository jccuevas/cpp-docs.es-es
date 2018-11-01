---
title: 'TN062: Reflexión de mensajes para controles de Windows'
ms.date: 06/28/2018
f1_keywords:
- vc.controls.messages
helpviewer_keywords:
- ON_WM_VKEYTOITEM_REFLECT macro [MFC]
- ON_WM_DRAWITEM_REFLECT macro [MFC]
- ON_WM_VSCROLL_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT message [MFC]
- ON_CONTROL_REFLECT_EX macro [MFC]
- ON_UPDATE_COMMAND_UI_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT_EX message [MFC]
- ON_WM_HSCROLL_REFLECT macro [MFC]
- message reflection [MFC]
- ON_WM_COMPAREITEM_REFLECT macro [MFC]
- ON_WM_MEASUREITEM_REFLECT macro [MFC]
- ON_NOTIFY message [MFC]
- WM_COMMAND [MFC]
- WM_CTLCOLOR message [MFC]
- TN062 [MFC]
- ON_WM_CHARTOITEM_REFLECT macro [MFC]
- ON_WM_CTLCOLOR_REFLECT macro [MFC]
- ON_WM_DELETEITEM_REFLECT macro [MFC]
- notification messages [MFC]
- ON_WM_PARENTNOTIFY_REFLECT macro [MFC]
- WM_NOTIFY message [MFC]
- ON_CONTROL_REFLECT macro
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
ms.openlocfilehash: aa189eec430d72bef753fef7ebbe9ad929d76c87
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677505"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062: Reflexión de mensajes para controles de Windows

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota técnica describe la reflexión de mensajes, una nueva característica de MFC 4.0. También contiene instrucciones para crear un control reutilizable simple que usa la reflexión de mensajes.

Esta nota técnica no trata la reflexión de mensajes tal como se aplica a los controles ActiveX (anteriormente denominados controles OLE). Consulte el artículo [controles ActiveX: creación de subclases de un Control de Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

**¿Qué es la reflexión de mensajes**

Controles de Windows suele envían mensajes de notificación a sus ventanas primarias. Por ejemplo, muchos controles de envían un mensaje de notificación de color del control (WM_CTLCOLOR o uno de sus variantes) a su elemento principal para permitir que el elemento primario proporcionar un pincel para pintar el fondo del control.

En Windows y MFC antes de la versión 4.0, la ventana primaria, a menudo un cuadro de diálogo es responsable de controlar estos mensajes. Esto significa que el código para controlar el mensaje debe estar en la clase de la ventana primaria y que tiene se dupliquen en todas las clases que necesita para controlar ese mensaje. En el caso anterior, cada cuadro de diálogo que deseaba controles con fondos personalizados tendría que controlar el mensaje de notificación de control de color. Sería mucho más fácil reutilizar el código si se puede escribir una clase de control que deben controlar su propio color de fondo.

En MFC 4.0, el mecanismo anterior sigue funcionando, windows primaria pueden controlar mensajes de notificación. Además, sin embargo, MFC 4.0 facilita la reutilización, ya que proporciona una característica denominada "reflexión de mensajes" que permite que estos mensajes de notificación se administran en la ventana del control secundario o en la ventana primaria, o en ambos. En el ejemplo de color de fondo de control, ahora puede escribir una clase de control que se establece su propio color de fondo al controlar el mensaje WM_CTLCOLOR reflejado, todo ello sin confiar en el elemento primario. (Tenga en cuenta que dado que la reflexión de mensajes se implementa por MFC, no por Windows, la clase de ventana primaria debe derivarse de `CWnd` de reflexión de mensajes para que funcione.)

Las versiones anteriores de MFC hizo algo similar a la reflexión de mensajes proporcionando funciones virtuales para algunos mensajes, como los mensajes para los cuadros de lista dibujado por el propietario (WM_DRAWITEM y así sucesivamente). El nuevo mecanismo de reflexión de mensajes es generalizado y coherente.

Reflexión de mensajes es compatible con el código escrito para las versiones de MFC antes de 4.0.

Si ha proporcionado un controlador para un mensaje concreto o para un intervalo de mensajes en la clase de la ventana primaria, invalidará reflejan los controladores de mensajes para el mismo mensaje proporcionado no llame a la función de controlador de clase base en su propio controlador. Por ejemplo, si controla WM_CTLCOLOR en la clase de cuadro de diálogo, su control invalidará los controladores de mensajes reflejados.

Si, en la clase de ventana principal, se proporciona un controlador para un mensaje WM_NOTIFY concreto o los mensajes de un intervalo de WM_NOTIFY, se llamará al controlador sólo si el control secundario envía esos mensajes no tiene un controlador de mensajes reflejados a través de `ON_NOTIFY_REFLECT()`. Si usas `ON_NOTIFY_REFLECT_EX()` en el mapa de mensajes, el controlador de mensajes puede permitir o no la ventana primaria controlar el mensaje. Si el controlador devuelve **FALSE**, el mensaje se controlarán mediante el elemento primario, mientras que una llamada que devuelve **TRUE** no admite el elemento primario para controlarla. Tenga en cuenta que se ha controlado el mensaje reflejado antes del mensaje de notificación.

Cuando se envía un mensaje WM_NOTIFY, el control se ofrece la posibilidad de controlarla. Si se envía a cualquier otro mensaje reflejado, la ventana primaria tiene la primera oportunidad de controlarla y el control recibe el mensaje reflejado. Para ello, necesitará una función de controlador y una entrada correspondiente en el mapa de mensajes de clase del control.

La macro de mapa de mensajes para mensajes reflejados es ligeramente diferente para las notificaciones periódicas: tiene *_REFLECT* anexado a su nombre habitual. Por ejemplo, para controlar un mensaje WM_NOTIFY en el elemento primario, utilice la macro ON_NOTIFY en mapa de mensajes del elemento primario. Para controlar el mensaje reflejado en el control secundario, use la macro ON_NOTIFY_REFLECT en mapa de mensajes del control secundario. En algunos casos, los parámetros son diferentes, también. Tenga en cuenta que ClassWizard normalmente puede agregar las entradas de mapa de mensajes para usted y proporcionar implementaciones de esqueleto de función con los parámetros correctos.

Consulte [TN061: mensajes ON_NOTIFY y Wm_notify](../mfc/tn061-on-notify-and-wm-notify-messages.md) para obtener información sobre el nuevo mensaje WM_NOTIFY.

**Las entradas de mapa de mensajes y prototipos de función de controlador de mensajes reflejados**

Para controlar un mensaje de notificación de control reflejado, use las macros de mapa de mensajes y prototipos de función aparece en la tabla siguiente.

ClassWizard normalmente puede agregar estas entradas de mapa de mensajes para usted y proporcionar implementaciones de esqueleto de función. Consulte [definir un controlador de mensajes para un mensaje reflejado](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) para obtener información acerca de cómo definir controladores de mensajes reflejados.

Para convertir el nombre del mensaje en el nombre de macro reflejado, anteponga *ON_* y anexe *_REFLECT*. Por ejemplo, WM_CTLCOLOR se convierte en ON_WM_CTLCOLOR_REFLECT. (Para ver qué mensajes se pueden reflejar, realizar la conversión opuesta en las entradas de macro en la tabla siguiente).

Las tres excepciones a la regla anterior son los siguientes:

- La macro para las notificaciones de WM_COMMAND es ON_CONTROL_REFLECT.

- La macro para reflexiones WM_NOTIFY es ON_NOTIFY_REFLECT.

- La macro para reflexiones ON_UPDATE_COMMAND_UI es ON_UPDATE_COMMAND_UI_REFLECT.

En cada uno de los anteriores casos especiales, debe especificar el nombre de la función de miembro de controlador. En los demás casos, debe usar el nombre estándar para la función de controlador.

Los significados de los parámetros y valores devueltos de las funciones se documentan en el nombre de función o el nombre de función con *en* antepuesto. Por ejemplo, `CtlColor` se documenta en `OnCtlColor`. Varios controladores de mensajes reflejados necesitan menos parámetros que los controladores similar en una ventana primaria. Solo coincide con los nombres de la tabla siguiente con los nombres de los parámetros formales en la documentación.

|Entrada de asignación|Prototipo de función|
|---------------|------------------------|
|**ON_CONTROL_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**void afx_msg** `memberFxn` **();**|
|**ON_NOTIFY_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**void afx_msg** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *resultado* **);**|
|**ON_UPDATE_COMMAND_UI_REFLECT (** `memberFxn` **)**|**void afx_msg** `memberFxn` **(CCmdUI** <strong>\*</strong> `pCmdUI` **);**|
|**(DE ON_WM_CTLCOLOR_REFLECT)**|**afx_msg HBRUSH CtlColor (CDC** <strong>\*</strong> `pDC` **, UINT** `nCtlColor` **);**|
|**(DE ON_WM_DRAWITEM_REFLECT)**|**afx_msg void DrawItem (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|
|**(DE ON_WM_MEASUREITEM_REFLECT)**|**afx_msg void MeasureItem (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|
|**(DE ON_WM_DELETEITEM_REFLECT)**|**afx_msg void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|
|**(DE ON_WM_COMPAREITEM_REFLECT)**|**int afx_msg CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|
|**(DE ON_WM_CHARTOITEM_REFLECT)**|**int afx_msg CharToItem (UINT** `nKey` **, UINT** `nIndex` **);**|
|**(DE ON_WM_VKEYTOITEM_REFLECT)**|**int afx_msg VKeyToItem (UINT** `nKey` **, UINT** `nIndex` **);**|
|**(DE ON_WM_HSCROLL_REFLECT)**|**afx_msg void HScroll (UINT** `nSBCode` **, UINT** `nPos` **);**|
|**(DE ON_WM_VSCROLL_REFLECT)**|**afx_msg void VScroll (UINT** `nSBCode` **, UINT** `nPos` **);**|
|**(DE ON_WM_PARENTNOTIFY_REFLECT)**|**afx_msg void ParentNotify (UINT** `message` **, LPARAM** `lParam` **);**|

Las macros ON_NOTIFY_REFLECT y ON_CONTROL_REFLECT tienen variaciones que permiten más de un objeto (por ejemplo, el control y su elemento primario) para controlar un mensaje determinado.

|Entrada de asignación|Prototipo de función|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *resultado* **);**|
|**ON_CONTROL_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **();**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>Control de mensajes reflejado: Un ejemplo de un control reutilizable

Este sencillo ejemplo crea un control reutilizable denominado `CYellowEdit`. El control funciona igual que un control de edición habitual, salvo en que muestra texto negro sobre un fondo amarillo. Sería fácil agregar funciones miembro que permitirían la `CYellowEdit` control para mostrar colores diferentes.

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>Para probar el ejemplo que crea un control reutilizable

1. Crear un nuevo cuadro de diálogo en una aplicación existente. Para obtener más información, consulte el [editor de cuadro de diálogo](../windows/dialog-editor.md) tema.

   Debe tener una aplicación en el que se va a desarrollar el control reutilizable. Si no tiene una aplicación existente para usar, crear una aplicación basada en el cuadro de diálogo mediante el Asistente para aplicaciones.

2. Con el proyecto cargado en Visual C++, use ClassWizard para crear una nueva clase denominada `CYellowEdit` según `CEdit`.

3. Agregue tres variables de miembro a sus `CYellowEdit` clase. Los dos primeros será *COLORREF* variables para almacenar el color del texto y el color de fondo. El tercero será un `CBrush` objeto que va a contener el pincel para pintar el fondo. El `CBrush` objeto le permite crear el pincel de diseño una vez, simplemente haga referencia a él después de eso y destruir el pincel automáticamente cuando el `CYellowEdit` se destruye el control.

4. Inicialice las variables de miembro escribiendo el constructor como sigue:

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. Con ClassWizard, agregue un controlador para el mensaje WM_CTLCOLOR reflejado para su `CYellowEdit` clase. Tenga en cuenta que se indica que el mensaje se refleja el signo igual delante del nombre del mensaje en la lista de mensajes que puede controlar. Esto se describe en [definir un controlador de mensajes para un mensaje reflejado](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

   ClassWizard agrega la siguiente función de macro y el esqueleto de mapa de mensajes para usted:

    ```cpp
    ON_WM_CTLCOLOR_REFLECT()
    // Note: other code will be in between....

    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)
    {
        // TODO: Change any attributes of the DC here
        // TODO: Return a non-NULL brush if the
        //       parent's handler should not be called
        return NULL;
    }
    ```

6. Reemplace el cuerpo de la función con el código siguiente. El código especifica el color del texto, el color de fondo del texto y el color de fondo para el resto del control.

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. Crear un control de edición en el cuadro de diálogo y luego adjuntarlo a una variable miembro haciendo doble clic en el control de edición mientras mantiene presionada una tecla de control. En el cuadro de diálogo Agregar variables miembro, finalizar el nombre de variable y elija "Control" para la categoría, a continuación, "CYellowEdit" para el tipo de variable. No olvide establecer el orden de tabulación en el cuadro de diálogo. Además, no olvide incluir el archivo de encabezado para el `CYellowEdit` control en el archivo de encabezado del cuadro de diálogo.

8. Compile y ejecute su aplicación. El control de edición tendrá un fondo amarillo.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
