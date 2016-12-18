---
title: "TN062: Reflexi&#243;n de mensajes para controles de Windows | Microsoft Docs"
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
  - "vc.controls.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reflexión de mensajes"
  - "mensajes de notificación"
  - "ON_CONTROL_REFLECT (macro)"
  - "ON_CONTROL_REFLECT_EX (macro)"
  - "ON_NOTIFY (mensaje)"
  - "ON_NOTIFY_REFLECT (mensaje)"
  - "ON_NOTIFY_REFLECT_EX (mensaje)"
  - "ON_UPDATE_COMMAND_UI_REFLECT (macro)"
  - "ON_WM_CHARTOITEM_REFLECT (macro)"
  - "ON_WM_COMPAREITEM_REFLECT (macro)"
  - "ON_WM_CTLCOLOR_REFLECT (macro)"
  - "ON_WM_DELETEITEM_REFLECT (macro)"
  - "ON_WM_DRAWITEM_REFLECT (macro)"
  - "ON_WM_HSCROLL_REFLECT (macro)"
  - "ON_WM_MEASUREITEM_REFLECT (macro)"
  - "ON_WM_PARENTNOTIFY_REFLECT (macro)"
  - "ON_WM_VKEYTOITEM_REFLECT (macro)"
  - "ON_WM_VSCROLL_REFLECT (macro)"
  - "TN062"
  - "WM_COMMAND"
  - "WM_CTLCOLOR (mensaje)"
  - "WM_NOTIFY (mensaje)"
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN062: Reflexi&#243;n de mensajes para controles de Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota técnica describe la reflexión de mensaje, una nueva característica de MFC 4,0.  También contiene instrucciones para crear un control reutilizable simple que usa la reflexión de mensaje.  
  
 Esta nota técnica no describe la reflexión de mensaje que se aplica a controles ActiveX \(antes denominados controles OLE\).  Vea el artículo [Controles ActiveX: Crear subclases de un Control de Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
 **¿Cuál es la reflexión de mensaje?**  
  
 Los controles de Windows con frecuencia envían mensajes de notificación a sus ventanas primarias.  Por ejemplo, muchos controles exponen un control el mensaje de notificación de color \(`WM_CTLCOLOR` o uno de sus variantes\) al elemento primario para permitir que el elemento primario proporcione un pincel para pintar el fondo del control.  
  
 En Windows y en MFC antes de la versión 4.0, la ventana primaria, a menudo un cuadro de diálogo, es responsable de administrar estos mensajes.  Esto significa que el código para administrar el mensaje debe estar en la clase de la ventana primaria y que tiene que ser duplicado en cada clase que necesite controlar este mensaje.  En el caso anterior, cada cuadro de diálogo que los controles deseados con fondos personalizados tendrían que controlar el mensaje de notificación de color del control.  Sería mucho más fácil reutilizar código si una clase de control podría escribirse que deben su propio color de fondo.  
  
 En MFC 4,0, el otro mecanismo sigue funcionando — las ventanas principales pueden controlar mensajes de notificación.  Además, sin embargo, MFC 4,0 facilita la reutilización proporcionando una característica denominada “la reflexión de mensaje” que permite que estos mensajes de notificación se administran en la ventana de control secundario o la ventana primaria, o en ambos.  En el ejemplo del color de fondo del control, ahora puede escribir una clase de control que establezca su propio color de fondo controlando el mensaje reflejado de `WM_CTLCOLOR` — todo sin recurrir al elemento primario. \(Observe que desde la reflexión de mensaje es implementada por MFC, no por Windows, la clase de la ventana primaria debe derivarse de `CWnd` para que la reflexión de mensaje\).  
  
 Las versiones anteriores de MFC se parece a la reflexión de mensaje mediante las funciones virtuales para algunos mensajes, como los mensajes para los cuadros de lista propietario\- dibujados \(`WM_DRAWITEM`, etc.\).  El nuevo mecanismo de reflexión de mensaje es general y coherente.  
  
 La reflexión de mensaje es compatible con el código escrito para las versiones de MFC antes de 4,0.  
  
 Si ha proporcionado un controlador para un mensaje concreto, o para un intervalo de mensajes, en la clase de la ventana primaria, reemplazará reflejado controladores de mensajes para el mismo mensaje le proporcionó no llama a la función de controlador de clases base en dispone el controlador.  Por ejemplo, si administra `WM_CTLCOLOR` en la del cuadro de diálogo, el control reemplazará cualquier controlador de mensajes reflejados.  
  
 Si, en la clase de la ventana primaria, proporcione un controlador para un mensaje concreto de **WM\_NOTIFY** o un intervalo de los mensajes de **WM\_NOTIFY** , se llamará al controlador sólo si el control secundario que envía los mensajes no tiene un controlador de mensajes reflejados con **ON\_NOTIFY\_REFLECT\(\)**.  Si utiliza **ON\_NOTIFY\_REFLECT\_EX\(\)** en el mapa de mensajes, el controlador de mensajes puede o no puede permitir que la ventana principal controle el mensaje.  Si el controlador devuelve **FALSE**, el mensaje se controla el elemento primario también, mientras que una llamada que devuelve **VERDADERO** no permite que el elemento primario lo controle.  Observe que el mensaje reflejado se controla antes del mensaje de notificación.  
  
 Cuando se envía un mensaje de **WM\_NOTIFY** , el control se proporciona la primera oportunidad de controlarla.  Si se envía otro mensaje reflejado, la ventana primaria tiene la primera oportunidad de controlarla y el control recibirá el mensaje reflejado.  Para ello, necesitará una función controladora y una entrada adecuada en el mapa de mensajes de la clase del control.  
  
 La macro de mensaje\- mapa para los mensajes reflejados es ligeramente diferente que para las notificaciones regulares: tiene **\_REFLECT** anexado al nombre habitual.  Por ejemplo, para controlar un mensaje de **WM\_NOTIFY** en el elemento primario, se utiliza `ON_NOTIFY` macro en el mapa de mensajes del elemento primario.  Para controlar el mensaje reflejado en el control secundario, utilice la macro de **ON\_NOTIFY\_REFLECT** en el mapa de mensajes del control secundario.  En algunos casos, los parámetros son diferentes, también.  Observe que ClassWizard puede agregar las entradas de mensaje\- mapa para usted y proporcionar normalmente esquemáticas implementaciones de función con parámetros correctos.  
  
 Vea [TN061: Mensajes de ON\_NOTIFY y de WM\_NOTIFY](../mfc/tn061-on-notify-and-wm-notify-messages.md) para la información en el nuevo mensaje de **WM\_NOTIFY** .  
  
 **Entradas de Mensaje\- mapa y función Prototipos de controlador de mensajes reflejados**  
  
 Para controlar un mensaje de notificación reflejado de control, use las macros de mensaje\- mapa y los prototipos de función enumerados en la tabla siguiente.  
  
 Pero puede agregar estas entradas de mensaje\- mapa para usted y proporcionar normalmente esquemáticas implementaciones de la función.  Vea [Definir un controlador de mensajes para un mensaje reflejados](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) para obtener información sobre cómo definir los controladores de los mensajes reflejados.  
  
 Para convertir el nombre del mensaje al nombre de la macro reflejado, anteponga **ON\_** y anexe **\_REFLECT**.  Por ejemplo, `WM_CTLCOLOR` se convierte en **ON\_WM\_CTLCOLOR\_REFLECT**. \(Para ver qué mensajes pueden ser reflejados, haga la conversión opuesta en las entradas de macro en la tabla siguiente\).  
  
 Las tres excepciones a la regla anterior son los siguientes:  
  
-   La macro para las notificaciones de **WM\_COMMAND** es **ON\_CONTROL\_REFLECT**.  
  
-   La macro para las reflexiones de **WM\_NOTIFY** es **ON\_NOTIFY\_REFLECT**.  
  
-   La macro para las reflexiones de `ON_UPDATE_COMMAND_UI` es **ON\_UPDATE\_COMMAND\_UI\_REFLECT**.  
  
 En cada uno de los casos especiales anteriores, debe especificar el nombre de la función miembro de controlador.  En otros casos, debe usar el nombre estándar para la función controladora.  
  
 El significado de los parámetros y valores devueltos de funciones se documentan en o nombre de función o el nombre de función con **Activado** work item.  Por ejemplo, **CtlColor** se documenta en `OnCtlColor`.  Varios controladores de mensajes reflejados necesitan menos parámetros que los controladores similares en una ventana primaria.  Solo coinciden con los nombres en la tabla siguiente con los nombres de los parámetros formales de la documentación.  
  
|Entrada de asignación|Prototipo de función|  
|---------------------------|--------------------------|  
|**ON\_CONTROL\_REFLECT\(**  `wNotifyCode` **,**  `memberFxn`  **\)**|**afx\_msg void**  `memberFxn`  **\( \);**|  
|**ON\_NOTIFY\_REFLECT\(**  `wNotifyCode` **,**  `memberFxn`  **\)**|*resultado*\);de**afx\_msg void** `memberFxn` **\( NMHDR \*** `pNotifyStruct`**, LRESULT\***|  
|**ON\_UPDATE\_COMMAND\_UI\_REFLECT\(**  `memberFxn`  **\)**|**afx\_msg void**  `memberFxn`  **\( CCmdUI\***  `pCmdUI`  **\);**|  
|**ON\_WM\_CTLCOLOR\_REFLECT \(\)**|**afx\_msg HBRUSH CtlColor \( CDC\***  `pDC` **, UINT**  `nCtlColor`  **\);**|  
|**ON\_WM\_DRAWITEM\_REFLECT \(\)**|**afx\_msg void DrawItem \( LPDRAWITEMSTRUCT**  `lpDrawItemStruct`  **\);**|  
|**ON\_WM\_MEASUREITEM\_REFLECT \(\)**|**afx\_msg void MeasureItem \( LPMEASUREITEMSTRUCT**  `lpMeasureItemStruct`  **\);**|  
|**ON\_WM\_DELETEITEM\_REFLECT \(\)**|**afx\_msg void DeleteItem \( LPDELETEITEMSTRUCT**  `lpDeleteItemStruct`  **\);**|  
|**ON\_WM\_COMPAREITEM\_REFLECT \(\)**|**afx\_msg int CompareItem \( LPCOMPAREITEMSTRUCT**  `lpCompareItemStruct`  **\);**|  
|**ON\_WM\_CHARTOITEM\_REFLECT \(\)**|**afx\_msg int CharToItem \( UINT**  `nKey` **, UINT**  `nIndex`  **\);**|  
|**ON\_WM\_VKEYTOITEM\_REFLECT \(\)**|**afx\_msg int VKeyToItem \( UINT**  `nKey` **, UINT**  `nIndex`  **\);**|  
|**ON\_WM\_HSCROLL\_REFLECT \(\)**|**afx\_msg void HScroll \( UINT**  `nSBCode` **, UINT**  `nPos`  **\);**|  
|**ON\_WM\_VSCROLL\_REFLECT \(\)**|**afx\_msg void VScroll \( UINT**  `nSBCode` **, UINT**  `nPos`  **\);**|  
|**ON\_WM\_PARENTNOTIFY\_REFLECT \(\)**|**afx\_msg void ParentNotify \( UINT**  `message` **, LPARAM**  `lParam`  **\);**|  
  
 Las macros de **ON\_NOTIFY\_REFLECT** y de **ON\_CONTROL\_REFLECT** tienen variaciones que permiten que más de un objeto \(como el control y su elemento primario\) administre un mensaje determinado.  
  
|Entrada de asignación|Prototipo de función|  
|---------------------------|--------------------------|  
|**ON\_NOTIFY\_REFLECT\_EX\(**  `wNotifyCode` **,**  `memberFxn`  **\)**|*resultado*\);de**afx\_msg BOOL** `memberFxn` **\( NMHDR \*** `pNotifyStruct`**, LRESULT\***|  
|**ON\_CONTROL\_REFLECT\_EX\(**  `wNotifyCode` **,**  `memberFxn`  **\)**|**afx\_msg BOOL**  `memberFxn`  **\( \);**|  
  
## Administrar mensajes reflejados: Un ejemplo de control de Flujo  
 Este sencillo ejemplo crea un control reutilizable denominado `CYellowEdit`.  El control funciona igual que un control de edición normal sólo que muestra el texto negro sobre fondo amarillo.  Sería fácil agregar las funciones miembro que permitirían que el control de `CYellowEdit` presentara diferentes colores.  
  
#### Para probar el ejemplo que crea un control reutilizable  
  
1.  Cree un nuevo cuadro de diálogo en una aplicación existente.  Para obtener más información, vea el tema de [editor de cuadros de diálogo](../mfc/dialog-editor.md) .  
  
     Debe tener una aplicación en la que desarrollar el control reutilizable.  Si no tiene una aplicación existente que utilizar, cree una aplicación diálogo\- basada mediante AppWizard.  
  
2.  Con el proyecto cargado en Visual C\+\+, utilice ClassWizard para crear una nueva clase denominada `CYellowEdit` basado en `CEdit`.  
  
3.  Agregue las variables con tres miembros a la clase de `CYellowEdit` .  Los dos primeros se variables de **COLORREF** para contener el color del texto y el color de fondo.  El tercero será un objeto de `CBrush` que contendrá el pincel para pintar el fondo.  El objeto de `CBrush` permite crear el pincel una vez, simplemente haga referencia después de éste, y que destruya el pincel automáticamente cuando se destruye el control de `CYellowEdit` .  
  
4.  Inicialice las variables miembro escribiendo el constructor como sigue:  
  
    ```  
    CYellowEdit::CYellowEdit()  
    {  
       m_clrText = RGB( 0, 0, 0 );  
       m_clrBkgnd = RGB( 255, 255, 0 );  
       m_brBkgnd.CreateSolidBrush( m_clrBkgnd );  
    }  
    ```  
  
5.  Mediante ClassWizard, agregue un controlador para el mensaje reflejado de `WM_CTLCOLOR` a la clase de `CYellowEdit` .  Observe que el signo igual delante del nombre del mensaje en la lista de mensajes que puede controlar indica que el mensaje se refleja.  Esto se describe en [Definir un controlador de mensajes para un mensaje reflejados](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).  
  
     ClassWizard agrega la siguiente macro de mensaje\- mapa y la función esquemática automáticamente:  
  
    ```  
    ON_WM_CTLCOLOR_REFLECT()  
  
    // Note: other code will be in between....  
  
    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)   
    {  
       // TODO: Change any attributes of the DC here  
  
       // TODO: Return a non-NULL brush if the  
       //   parent's handler should not be called  
       return NULL;  
    }  
    ```  
  
6.  Reemplace el cuerpo de la función con el código siguiente.  El código especifica el color del texto, el color de fondo del texto, y el color de fondo para el resto del control.  
  
    ```  
    pDC->SetTextColor( m_clrText );   // text  
    pDC->SetBkColor( m_clrBkgnd );   // text bkgnd  
    return m_brBkgnd;            // ctl bkgnd  
    ```  
  
7.  Cree un control de edición en el cuadro de diálogo, asócielo a una variable miembro doble\- haciendo clic en el control de edición mientras mantiene una clave de control siguiente.  En el cuadro de diálogo de variable miembro add, finalice el nombre de variable y elija la “Control” para la categoría, después “CYellowEdit” para el tipo de la variable.  No olvide establecer la tabulación en el cuadro de diálogo.  Además, asegúrese de incluir el archivo de encabezado para el control de `CYellowEdit` en el archivo de encabezado del cuadro de diálogo.  
  
8.  Compile y ejecute su aplicación.  El control de edición tendrá un fondo amarillo.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)