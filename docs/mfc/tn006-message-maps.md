---
title: "TN006: Mapas de mensajes | Microsoft Docs"
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
  - "vc.messages.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de mensajes [C++], mensajería de Windows"
  - "ON_COMMAND (macro)"
  - "ON_COMMAND_EX (macro)"
  - "ON_COMMAND_RANGE (macro)"
  - "ON_COMMAND_RANGE_EX (macro)"
  - "ON_CONTROL (macro)"
  - "ON_CONTROL_RANGE (macro)"
  - "ON_MESSAGE (macro)"
  - "ON_NOTIFY (mensaje)"
  - "ON_NOTIFY_RANGE (macro)"
  - "ON_REGISTERED_MESSAGE (macro)"
  - "ON_UPDATE_COMMAND_UI (macro)"
  - "TN006"
  - "mensajes de Windows [C++], mapas de mensajes"
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
caps.latest.revision: 16
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN006: Mapas de mensajes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe la facilidad de mapa de mensajes MFC.  
  
## El problema  
 Microsoft Windows implementa funciones virtuales en las clases de ventana que utilice su facilidad de mensajería.  Debido al elevado número de mensajes implicados, proporcionando una función virtual independiente para cada mensaje de Windows crearía un vtable prohibitivo grande.  
  
 Dado que el número de mensajes sistema\- definido de Windows cambian con el tiempo, y que las aplicaciones pueden definir sus propios mensajes de Windows, los mapas de mensajes proporcionan un nivel de direccionamiento indirecto que evita que la interfaz interrumpan código existente.  
  
## Información general  
 MFC proporciona una alternativa a la instrucción switch que se utilizó en programas basados en Windows tradicionales para controlar los mensajes enviados a una ventana.  Una asignación de mensajes a los métodos puede definirse para cuando un mensaje se recibe en una ventana, llamar al método adecuado automáticamente.  Esta utilidad del mensaje\- mapa está diseñado para ser similar a funciones virtuales pero tiene las ventajas adicionales no posibles con funciones virtuales de C\+\+.  
  
## Definición de un mapa de mensajes  
 La macro de [DECLARE\_MESSAGE\_MAP](../Topic/DECLARE_MESSAGE_MAP.md) declara a tres miembros para la clase.  
  
-   Una matriz privado de las entradas de `AFX_MSGMAP_ENTRY` denominado `_messageEntries`.  
  
-   Una estructura protegida de `AFX_MSGMAP` denominado `messageMap` que señala a `_messageEntries` la matriz.  
  
-   Una función virtual protegida denominado `GetMessageMap` que devuelve la dirección de `messageMap`.  
  
 Esta macro se debe colocar en la declaración de cualquier clase mediante mapas de mensajes.  Por convención, está en el final de la declaración de clase.  Por ejemplo:  
  
```  
class CMyWnd : public CMyParentWndClass  
{  
    // my stuff...  
  
protected:  
    //{{AFX_MSG(CMyWnd)  
    afx_msg void OnPaint();  
    //}}AFX_MSG  
  
    DECLARE_MESSAGE_MAP()  
};  
```  
  
 Éste es el formato generado por AppWizard y ClassWizard cuando crean nuevas clases.  Los corchetes de \/\/{{y \/\/}} son necesarios para ClassWizard.  
  
 La tabla del mapa de mensajes se define utilizando un conjunto de macros que se expandan a las entradas del mapa de mensajes.  Una tabla comienza con una macro\-instrucción de [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) , que define la clase que controla este mapa de mensajes y se pasa la clase primaria a la que no se controlan los mensajes.  Los extremos de la tabla con la macro\-instrucción de [END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md) .  
  
 Entre estas dos llamadas es una entrada para cada mensaje administrado por este mapa de mensajes.  Cada mensaje estándar de Windows tiene una macro del formulario ON\_WM\_*MESSAGE\_NAME* que genera una entrada para ese mensaje.  
  
 Una firma de la función estándar se ha definido para desempaquetar los parámetros de cada mensaje de Windows y proporcionar seguridad de tipos.  Estas firmas se encuentran en el archivo Afxwin.h en la declaración de [CWnd](../mfc/reference/cwnd-class.md).  Cada uno se marca con la palabra clave `afx_msg` para identificar fácil.  
  
> [!NOTE]
>  ClassWizard requiere que utilice la palabra clave de `afx_msg` en las declaraciones de controlador del mapa de mensajes.  
  
 Estas firmas function se derivadas utilizando la convención simple.  El nombre de la función siempre comienza con `"On`”.  Esto va seguido del nombre del mensaje de Windows con “WM\_” quitado y la primera letra de cada palabra capitalizada.  El orden de los parámetros es `wParam` seguido de `LOWORD`\(`lParam`\) y `HIWORD`\(`lParam`\).  Los parámetros no usados no se pasan.  Cualquier identificador que es ajustado por las clases MFC se convierte a punteros a los objetos adecuados de MFC.  El ejemplo siguiente se muestra cómo controlar el mensaje de `WM_PAINT` y hacer que la función de `CMyWnd::OnPaint` que se denomine:  
  
```  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)  
    //{{AFX_MSG_MAP(CMyWnd)  
    ON_WM_PAINT()  
    //}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 La tabla del mapa de mensajes debe definirse fuera del ámbito de cualquier función o definición de clase.  No debería ubicarse en un bloque extern “c”.  
  
> [!NOTE]
>  ClassWizard modificará las entradas del mapa de mensajes que aparecen entre el corchete de comentario de \/\/{{y \/\/}}.  
  
## Mensajes definidos por el usuario de Windows  
 Los mensajes definidos por el usuario se pueden incluir en un mapa de mensajes mediante la macro de [ON\_MESSAGE](../Topic/ON_MESSAGE.md) .  Esta macro acepta un número de mensaje y un método de la forma:  
  
```  
    // inside the class declaration  
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);  
  
    #define WM_MYMESSAGE (WM_USER + 100)  
  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)  
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)  
END_MESSAGE_MAP()  
```  
  
 En este ejemplo, establecemos un controlador para un mensaje personalizado que tenga un identificador de mensaje de Windows derivado de base estándar de `WM_USER` para los mensajes definidos por el usuario.  El siguiente ejemplo se muestra cómo llamar a este controlador:  
  
```  
CWnd* pWnd = ...;  
pWnd->SendMessage(WM_MYMESSAGE);  
```  
  
 El intervalo de los mensajes definidos por el usuario que usan este enfoque debe estar en el intervalo `WM_USER` a 0x7fff.  
  
> [!NOTE]
>  Pero no admite escribir rutinas de controlador de `ON_MESSAGE` de la interfaz de usuario de ClassWizard.  Debe entrarlas en manualmente del editor de Visual C\+\+.  ClassWizard analizará estas entradas y permiten examinarlos como cualquier otra entrada de mensaje\- mapa.  
  
## Mensajes registrados de Windows  
 La función de [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) se utiliza para definir un mensaje de la nueva ventana que se garantiza que es único en el sistema.  La macro `ON_REGISTERED_MESSAGE` se utiliza para administrar estos mensajes.  Esta macro acepta un nombre de una variable de `UINT NEAR` que contiene el identificador de mensaje registrada de las ventanas  Por ejemplo  
  
```  
class CMyWnd : public CMyParentWndClass  
{  
public:  
    CMyWnd();  
  
    //{{AFX_MSG(CMyWnd)  
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);  
    //}}AFX_MSG  
  
    DECLARE_MESSAGE_MAP()  
};  
  
static UINT NEAR WM_FIND = RegisterWindowMessage("COMMDLG_FIND");  
  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)  
    //{{AFX_MSG_MAP(CMyWnd)  
    ON_REGISTERED_MESSAGE(WM_FIND, OnFind)  
    //}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 La variable registrada del identificador de mensaje de Windows \(WM\_FIND en este ejemplo\) debe ser una variable de `NEAR` debido a la manera en que se implementa `ON_REGISTERED_MESSAGE` .  
  
 El intervalo de los mensajes definidos por el usuario que usan este enfoque estará en el intervalo 0x C000 a 0xFFFF.  
  
> [!NOTE]
>  Pero no admite escribir rutinas de controlador de `ON_REGISTERED_MESSAGE` de la interfaz de usuario de ClassWizard.  Debe entrarlas en manualmente del editor de texto.  ClassWizard analizará estas entradas y permiten examinarlos como cualquier otra entrada de mensaje\- mapa.  
  
## Mensajes de comando  
 Los mensajes del comando de menú y de aceleradores se controlan en mapas de mensajes con la macro de `ON_COMMAND` .  Esta macro acepta un identificador de comando y un método.  Sólo el mensaje específico de `WM_COMMAND` que tiene `wParam` igual al identificador especificado de comando controla el método especificado en la entrada de mensaje\- mapa.  Las funciones miembro de controlador de comandos no toman ningún parámetro y `void`return.  La macro tiene el formato siguiente:  
  
```  
ON_COMMAND(id, memberFxn)  
```  
  
 Los mensajes de actualización de comandos se enrutan a través del mismo mecanismo, pero utilizan la macro de `ON_UPDATE_COMMAND_UI` en su lugar.  Las funciones miembro de controlador de actualización de comandos tienen un único parámetro, un puntero a un objeto de [CCmdUI](../mfc/reference/ccmdui-class.md) , y `void`return.  La macro tiene el formato  
  
```  
ON_UPDATE_COMMAND_UI(id, memberFxn)  
```  
  
 Los usuarios avanzados pueden utilizar la macro de `ON_COMMAND_EX` , que es un formulario extendido de controladores de mensajes del comando.  La macro proporciona un supraconjunto de la funcionalidad de `ON_COMMAND` .  Las funciones extendidas de miembro de comando\- controlador toman un solo parámetro, `UINT` que contiene el identificador de comando, y devuelven `BOOL`.  El valor devuelto debe ser `TRUE` para indicar que se ha controlado el comando.  Si no el enrutamiento continuará a otros objetos de destino del comando.  
  
 Ejemplos de estas formas:  
  
-   Resource.h interior \(generado normalmente por Visual C\+\+\)  
  
    ```  
    #define    ID_MYCMD      100  
    #define    ID_COMPLEX    101  
    ```  
  
-   Dentro de la declaración de clase  
  
    ```  
    afx_msg void OnMyCommand();  
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);  
    afx_msg BOOL OnComplexCommand(UINT nID);  
    ```  
  
-   En la definición del mapa de mensajes  
  
    ```  
    ON_COMMAND(ID_MYCMD, OnMyCommand)  
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)  
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)  
    ```  
  
-   En el archivo de implementación  
  
    ```  
    void CMyClass::OnMyCommand()  
    {  
        // handle the command  
    }  
  
    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)  
    {  
        // set the UI state with pCmdUI  
    }  
  
    BOOL CMyClass::OnComplexCommand(UINT nID)  
    {  
        // handle the command  
        return TRUE;  
    }  
    ```  
  
 Los usuarios avanzados pueden controlar un intervalo de comandos utilizando un controlador de un solo comando: [ON\_COMMAND\_RANGE](../Topic/ON_COMMAND_RANGE.md) o `ON_COMMAND_RANGE_EX`.  Vea la documentación del producto para obtener más información sobre estas macros.  
  
> [!NOTE]
>  ClassWizard admite crear `ON_COMMAND` y controladores de `ON_UPDATE_COMMAND_UI` , pero no permite crear `ON_COMMAND_EX` o controladores de `ON_COMMAND_RANGE` .  Sin embargo, el asistente para clases se analizará y permiten examinar los cuatro variantes de controlador de comandos.  
  
## Mensajes de notificación de Control  
 Los mensajes que se envían de los controles secundarios a una ventana tienen un bit adicional de la información en la entrada del mapa de mensajes: el identificador de control  Se llama al controlador de mensajes especificado en una entrada de asignación de mensaje solo si se cumplen las condiciones siguientes:  
  
-   El código de notificación de control \(alta palabra de `lParam`\), por ejemplo BN\_CLICKED, con el código de notificación especificado en la entrada de mensaje\- mapa.  
  
-   El identificador del control \(`wParam`\) coincide con el identificador del control especificado en la entrada de mensaje\- mapa.  
  
 Los mensajes de notificación de controles personalizados pueden utilizar la macro de [ON\_CONTROL](../Topic/ON_CONTROL.md) para definir una entrada del mapa de mensajes con un código personalizado de notificación.  Esta macro tiene el formato  
  
```  
ON_CONTROL(wNotificationCode, id, memberFxn)  
```  
  
 Para el uso avanzado [ON\_CONTROL\_RANGE](../Topic/ON_CONTROL_RANGE.md) se puede utilizar para controlar una notificación específica del control de un intervalo de controles con el mismo controlador.  
  
> [!NOTE]
>  Pero no permite crear un controlador de `ON_CONTROL` o de `ON_CONTROL_RANGE` en la interfaz de usuario.  Debe entrar en manualmente con el editor de texto.  ClassWizard analizará estas entradas y le permiten examinarlos como cualquier otro mensaje asignan entradas.  
  
 Controles comunes de Windows utilizan [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) más eficaz para las notificaciones complejas del control.  Esta versión de MFC tiene compatibilidad directa para este nuevo mensaje utilizando las macros de `ON_NOTIFY` y de `ON_NOTIFY_RANGE` .  Vea la documentación del producto para obtener más información sobre estas macros.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)