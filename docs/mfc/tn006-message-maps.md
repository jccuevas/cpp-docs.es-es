---
title: 'TN006: Mapas de mensajes | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.messages.maps
dev_langs: C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 567a44cd8d8b979a75eca7647861c579bf0c070b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn006-message-maps"></a>TN006: Mapas de mensajes
Esta nota describe la opción de mapa de mensajes MFC.  
  
## <a name="the-problem"></a>El problema  
 Microsoft Windows implementa funciones virtuales en las clases de ventana que utilice su servicio de mensajería. Debido al elevado número de mensajes implicados, proporcionando una función virtual independiente para cada mensaje de Windows crearía una vtable muy grande.  
  
 Dado que el número de mensajes definidos por el sistema de Windows cambia con el tiempo, y dado que las aplicaciones pueden definir sus propios mensajes de Windows, mapas de mensajes proporcionan un nivel de direccionamiento indirecto que impide que los cambios en la interfaz interrumpir el código existente.  
  
## <a name="overview"></a>Información general  
 MFC proporciona una alternativa a la instrucción switch que se utilizó en programas tradicionales de Windows para controlar los mensajes enviados a una ventana. Una asignación de mensajes a los métodos se puede definir para que cuando se recibe un mensaje en una ventana, se llama automáticamente al método adecuado. Esta función de asignación de mensajes está diseñada para ser similar a las funciones virtuales, pero tiene más ventajas que no son posibles con funciones virtuales de C++.  
  
## <a name="defining-a-message-map"></a>Definir un mapa de mensajes  
 El [DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) macro declara tres miembros de una clase.  
  
-   Una matriz privada de `AFX_MSGMAP_ENTRY` entradas denominadas `_messageEntries`.  
  
-   Protegidos `AFX_MSGMAP` estructura denominada `messageMap` que apunta a la `_messageEntries` matriz.  
  
-   Una función virtual denominado protegida `GetMessageMap` que devuelve la dirección de `messageMap`.  
  
 Esta macro se debe colocar en la declaración de cualquier clase con mapas de mensajes. Por convención, es el final de la declaración de clase. Por ejemplo:  
  
```  
class CMyWnd : public CMyParentWndClass  
{ *// my stuff...  
 
protected: *//{{AFX_MSG(CMyWnd)  
    afx_msg void OnPaint();
*//}}AFX_MSG  
 
    DECLARE_MESSAGE_MAP() 
};  
```  
  
 Este es el formato generado por AppWizard y ClassWizard al crear nuevas clases. El / / {{y / /}} corchetes son necesarios para ClassWizard.  
  
 Tabla del mapa de mensajes se define mediante un conjunto de macros que se expanden a las entradas de mapa de mensajes. Una tabla comienza por un [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) llamada de macro, que define la clase que controla este mapa de mensajes y la clase primaria a la que se pasan los mensajes no controlados. La tabla termina con la [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) llamada de macro.  
  
 Entre estas llamadas a dos macros es una entrada para cada mensaje que se va a ser controlada por este mapa de mensajes. Cada mensaje estándar de Windows tiene una macro del formulario ON_WM_*MESSAGE_NAME* que genera una entrada para ese mensaje.  
  
 Se ha definido una firma de función estándar para desempaquetar los parámetros de cada mensaje de Windows y proporciona seguridad de tipos. Estas firmas pueden encontrarse en el archivo Afxwin.h en la declaración de [CWnd](../mfc/reference/cwnd-class.md). Cada una de ellas está marcada con la palabra clave `afx_msg` para facilitar su identificación.  
  
> [!NOTE]
>  ClassWizard requiere el uso de la `afx_msg` palabra clave en las declaraciones de controlador de mapa de mensajes.  
  
 Estas firmas de función obtenidas mediante una convención simple. El nombre de la función siempre empieza por `"On`". Esto es seguido por el nombre del mensaje de Windows con la "WM_" quitado y la primera letra de cada palabra en mayúsculas. El orden de los parámetros es `wParam` seguido `LOWORD`(`lParam`), a continuación, `HIWORD`(`lParam`). No se pasan parámetros sin utilizar. Los identificadores que se ajustan las clases de MFC se convierten en punteros a los objetos MFC adecuados. En el ejemplo siguiente se muestra cómo controlar la `WM_PAINT` el mensaje y hacer que el `CMyWnd::OnPaint` función que se llamará:  
  
```  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass) *//{{AFX_MSG_MAP(CMyWnd)  
    ON_WM_PAINT() *//}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 La tabla de asignación de mensajes debe definirse fuera del ámbito de cualquier definición de función o clase. No se deben colocar en un bloque extern "C".  
  
> [!NOTE]
>  ClassWizard modificará las entradas del mapa de mensajes que se producen entre la / / {{y / /}} corchete de cierre de comentario.  
  
## <a name="user-defined-windows-messages"></a>Mensajes de Windows definidas por el usuario  
 Mensajes definidos por el usuario pueden incluirse en un mapa de mensajes mediante el uso de la [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) macro. Esta macro acepta un número de mensaje y un método de la forma:  
  
''' * / / dentro de la declaración de clase  
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

 
 #<a name="define-wmmymessage-wmuser--100"></a>definir WM_MYMESSAGE (WM_USER + 100)  
 
BEGIN_MESSAGE_MAP (CMyWnd, CMyParentWndClass)  
    ON_MESSAGE (WM_MYMESSAGE, OnMyMessage)  
END_MESSAGE_MAP()  
```  
  
 In this example, we establish a handler for a custom message that has a Windows message ID derived from the standard `WM_USER` base for user-defined messages. The following example shows how to call this handler:  
  
```  
CWnd * pWnd =...;  
pWnd -> SendMessage(WM_MYMESSAGE);
```  
  
 The range of user-defined messages that use this approach must be in the range `WM_USER` to 0x7fff.  
  
> [!NOTE]
>  ClassWizard does not support entering `ON_MESSAGE` handler routines from the ClassWizard user interface. You must manually enter them from the Visual C++ editor. ClassWizard will parse these entries and let you browse them just like any other message-map entries.  
  
## Registered Windows Messages  
 The [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) function is used to define a new window message that is guaranteed to be unique throughout the system. The macro `ON_REGISTERED_MESSAGE` is used to handle these messages. This macro accepts a name of a `UINT NEAR` variable that contains the registered windows message ID. For example  
  
```  
clase CMyWnd: CMyParentWndClass pública  
{  
public:  
    CMyWnd();

 *//{{AFX_MSG(CMyWnd)  
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam); * //}}AFX_MSG  
 
    DECLARE_MESSAGE_MAP() 
};  
 
UINT estática CASI WM_FIND = RegisterWindowMessage("COMMDLG_FIND");

 
*//{{AFX_MSG_MAP(CMyWnd) BEGIN_MESSAGE_MAP (CMyWnd, CMyParentWndClass)  
    ON_REGISTERED_MESSAGE (WM_FIND, OnFind) * //}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 The registered Windows message ID variable (WM_FIND in this example) must be a `NEAR` variable because of the way `ON_REGISTERED_MESSAGE` is implemented.  
  
 The range of user-defined messages that use this approach will be in the range 0xC000 to 0xFFFF.  
  
> [!NOTE]
>  ClassWizard does not support entering `ON_REGISTERED_MESSAGE` handler routines from the ClassWizard user interface. You must manually enter them from the text editor. ClassWizard will parse these entries and let you browse them just like any other message-map entries.  
  
## Command Messages  
 Command messages from menus and accelerators are handled in message maps with the `ON_COMMAND` macro. This macro accepts a command ID and a method. Only the specific `WM_COMMAND` message that has a `wParam` equal to the specified command ID is handled by the method specified in the message-map entry. Command handler member functions take no parameters and return `void`. The macro has the following form:  
  
```  
ON_COMMAND (Id., memberFxn)  
```  
  
 Command update messages are routed through the same mechanism, but use the `ON_UPDATE_COMMAND_UI` macro instead. Command update handler member functions take a single parameter, a pointer to a [CCmdUI](../mfc/reference/ccmdui-class.md) object, and return `void`. The macro has the form  
  
```  
ON_UPDATE_COMMAND_UI (Id., memberFxn)  
```  
  
 Advanced users can use the `ON_COMMAND_EX` macro, which is an extended form of command message handlers. The macro provides a superset of the `ON_COMMAND` functionality. Extended command-handler member functions take a single parameter, a `UINT` that contains the command ID, and return a `BOOL`. The return value should be `TRUE` to indicate that the command has been handled. Otherwise routing will continue to other command target objects.  
  
 Examples of these forms:  
  
-   Inside Resource.h (usually generated by Visual C++)  
  
 ```  
 #<a name="define----idmycmd------100"></a>definir ID_MYCMD 100  
 #<a name="define----idcomplex----101"></a>definir ID_COMPLEX 101  
 ```  
  
-   Inside the class declaration  
  
 ```  
    afx_msg void OnMyCommand();
afx_msg void OnUpdateMyCommand (CCmdUI * pCmdUI);

    afx_msg BOOL OnComplexCommand(UINT nID);

 ```  
  
-   Inside the message map definition  
  
 ```  
    ON_COMMAND(ID_MYCMD,
    OnMyCommand)  
    ON_UPDATE_COMMAND_UI(ID_MYCMD,
    OnUpdateMyCommand)  
    ON_COMMAND_EX(ID_MYCMD,
    OnComplexCommand)  
 ```  
  
-   In the implementation file  
  
 ```  
    void CMyClass::OnMyCommand()  
 {* / / controlar el comando  
 }  
 
    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)  
 {* / / establecer el estado de la interfaz de usuario con pCmdUI  
 }  
 
    BOOL CMyClass::OnComplexCommand(UINT nID)  
 {* / / controlar el comando  
    Devuelve TRUE;  
 }  
 ```  
  
 Advanced users can handle a range of commands by using a single command handler: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) or `ON_COMMAND_RANGE_EX`. See the product documentation for more information about these macros.  
  
> [!NOTE]
>  ClassWizard supports creating `ON_COMMAND` and `ON_UPDATE_COMMAND_UI` handlers, but it does not support creating `ON_COMMAND_EX` or `ON_COMMAND_RANGE` handlers. However, Class Wizard will parse and let you browse all four command handler variants.  
  
## Control Notification Messages  
 Messages that are sent from child controls to a window have an extra bit of information in their message map entry: the control's ID. The message handler specified in a message map entry is called only if the following conditions are true:  
  
-   The control notification code (high word of `lParam`), such as BN_CLICKED, matches the notification code specified in the message-map entry.  
  
-   The control ID (`wParam`) matches the control ID specified in the message-map entry.  
  
 Custom control notification messages may use the [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) macro to define a message map entry with a custom notification code. This macro has the form  
  
```  
ON_CONTROL (wNotificationCode, Id., memberFxn)  
```  
  
 For advanced usage [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) can be used to handle a specific control notification from a range of controls with the same handler.  
  
> [!NOTE]
>  ClassWizard does not support creating an `ON_CONTROL` or `ON_CONTROL_RANGE` handler in the user interface. You must manually enter them with the text editor. ClassWizard will parse these entries and let you browse them just like any other message map entries.  
  
 The Windows Common Controls use the more powerful [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) for complex control notifications. This version of MFC has direct support for this new message by using the `ON_NOTIFY` and `ON_NOTIFY_RANGE` macros. See the product documentation for more information about these macros.  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

