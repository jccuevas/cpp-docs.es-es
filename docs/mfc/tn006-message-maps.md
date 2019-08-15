---
title: 'TN006: Mapas de mensajes'
ms.date: 06/25/2018
f1_keywords:
- vc.messages.maps
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
ms.openlocfilehash: 489db046910cc4b44e381b3f9056cfe8f8b7ccfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511105"
---
# <a name="tn006-message-maps"></a>TN006: Mapas de mensajes

En esta nota se describe la utilidad mapa de mensajes de MFC.

## <a name="the-problem"></a>El problema

Microsoft Windows implementa funciones virtuales en clases de ventana que usan su utilidad de mensajería. Debido al gran número de mensajes implicados, si se proporciona una función virtual independiente para cada mensaje de Windows, se crearía una vtable muy grande.

Dado que el número de mensajes de Windows definidos por el sistema cambia con el tiempo, y dado que las aplicaciones pueden definir sus propios mensajes de Windows, los mapas de mensajes proporcionan un nivel de direccionamiento indirecto que evita que los cambios en la interfaz interrumpan el código existente.

## <a name="overview"></a>Información general

MFC proporciona una alternativa a la instrucción switch que se usó en los programas tradicionales basados en Windows para controlar los mensajes enviados a una ventana. Se puede definir una asignación de mensajes a métodos para que, cuando se reciba un mensaje en una ventana, se llame automáticamente al método correspondiente. Esta utilidad de asignación de mensajes está diseñada para ser similar a las funciones virtuales, pero tiene ventajas C++ adicionales que no son posibles con las funciones virtuales.

## <a name="defining-a-message-map"></a>Definir un mapa de mensajes

La macro [DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) declara tres miembros para una clase.

- Una matriz privada de entradas de AFX_MSGMAP_ENTRY denominada *_messageEntries*.

- Una estructura AFX_MSGMAP protegida denominada *messageMap* que apunta a la matriz *_messageEntries* .

- Función virtual protegida a la `GetMessageMap` que se llama que devuelve la dirección de *messageMap*.

Esta macro debe colocarse en la declaración de cualquier clase que use mapas de mensajes. Por Convención, está al final de la declaración de clase. Por ejemplo:

```cpp
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

Este es el formato generado por AppWizard y ClassWizard cuando crea nuevas clases. Los corchetes//{{y//}} son necesarios para ClassWizard.

La tabla del mapa de mensajes se define mediante un conjunto de macros que se expanden a las entradas de mapa de mensajes. Una tabla se inicia con una llamada de macro [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) , que define la clase controlada por este mapa de mensajes y la clase primaria a la que se pasan los mensajes no controlados. La tabla finaliza con la llamada a la macro [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) .

Entre estas dos llamadas a macros se encuentra una entrada para que este mapa de mensajes Controle cada mensaje. Cada mensaje de Windows estándar tiene una macro con el formato ON_WM_*MESSAGE_NAME* que genera una entrada para ese mensaje.

Se ha definido una firma de función estándar para desempaquetar los parámetros de cada mensaje de Windows y proporcionar seguridad de tipos. Estas firmas se pueden encontrar en el archivo AFXWIN. h en la declaración de [CWnd](../mfc/reference/cwnd-class.md). Cada una se marca con la palabra clave **afx_msg** para facilitar la identificación.

> [!NOTE]
> ClassWizard requiere que use la palabra clave **afx_msg** en las declaraciones de controlador de mapa de mensajes.

Estas firmas de función se derivan mediante una Convención simple. El nombre de la función siempre comienza por `"On`". A esto le sigue el nombre del mensaje de Windows con el "WM_" quitado y la primera letra de cada palabra en mayúscula. El orden de los parámetros es *wParam* seguido `LOWORD`de (*lParam*) then `HIWORD`(*lParam*). No se pasan los parámetros no usados. Los identificadores que se ajustan a las clases MFC se convierten en punteros a los objetos MFC adecuados. En el ejemplo siguiente se muestra cómo controlar el mensaje WM_PAINT y hacer `CMyWnd::OnPaint` que se llame a la función:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

La tabla del mapa de mensajes debe definirse fuera del ámbito de cualquier definición de función o clase. No debe colocarse en un bloque "C" externo.

> [!NOTE]
> ClassWizard modificará las entradas del mapa de mensajes que se producen entre el corchete de comentarios//{{y//}}.

## <a name="user-defined-windows-messages"></a>Mensajes de Windows definidos por el usuario

Los mensajes definidos por el usuario se pueden incluir en un mapa de mensajes mediante la macro [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) . Esta macro acepta un número de mensaje y un método con el formato:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

En este ejemplo, se establece un controlador para un mensaje personalizado que tiene un identificador de mensaje de Windows derivado de la base WM_USER estándar para los mensajes definidos por el usuario. En el ejemplo siguiente se muestra cómo llamar a este controlador:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

El intervalo de mensajes definidos por el usuario que utilizan este enfoque debe estar en el intervalo de WM_USER a 0x7fff.

> [!NOTE]
> ClassWizard no admite la entrada de rutinas de controlador ON_MESSAGE desde la interfaz de usuario de ClassWizard. Debe especificarlas manualmente desde el editor visual C++ . ClassWizard analizará estas entradas y permitirá examinarlas como cualquier otra entrada de mapa de mensajes.

## <a name="registered-windows-messages"></a>Mensajes de Windows registrados

La función [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) se usa para definir un nuevo mensaje de ventana que se garantiza que es único en todo el sistema. La macro ON_REGISTERED_MESSAGE se usa para controlar estos mensajes. Esta macro acepta un nombre de una variable *uint Near* que contiene el ID. de mensaje de Windows registrado. Por ejemplo

```cpp
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

La variable de ID. de mensaje de Windows registrada (WM_FIND en este ejemplo) debe ser una variable *cercana* debido a la manera en que se implementa ON_REGISTERED_MESSAGE.

El intervalo de mensajes definidos por el usuario que utilizan este enfoque estará en el intervalo de 0xC000 a 0xFFFF.

> [!NOTE]
> ClassWizard no admite la entrada de rutinas de controlador ON_REGISTERED_MESSAGE desde la interfaz de usuario de ClassWizard. Debe escribirlos manualmente en el editor de texto. ClassWizard analizará estas entradas y permitirá examinarlas como cualquier otra entrada de mapa de mensajes.

## <a name="command-messages"></a>Mensajes de comando

Los mensajes de comandos de los menús y los aceleradores se controlan en mapas de mensajes con la macro ON_COMMAND. Esta macro acepta un identificador de comando y un método. El método especificado en la entrada de mapa de mensajes solo controla el mensaje WM_COMMAND específico que tiene un *wParam* igual al identificador de comando especificado. Las funciones miembro del controlador de comandos no toman ningún parámetro y devuelven **void**. La macro tiene el formato siguiente:

```cpp
ON_COMMAND(id, memberFxn)
```

Los mensajes de actualización de comandos se enrutan a través del mismo mecanismo, pero se usa la macro ON_UPDATE_COMMAND_UI en su lugar. Las funciones miembro del controlador de actualización de comandos toman un único parámetro, un puntero a un objeto [CCmdUI](../mfc/reference/ccmdui-class.md) y devuelven **void**. La macro tiene el formato

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Los usuarios avanzados pueden usar la macro ON_COMMAND_EX, que es una forma extendida de controladores de mensajes de comandos. La macro proporciona un superconjunto de la funcionalidad ON_COMMAND. Las funciones miembro del controlador de comandos extendidos toman un único parámetro, un valor **uint** que contiene el identificador del comando y devuelven un valor **booleano**. El valor devuelto debe ser **true** para indicar que se ha controlado el comando. De lo contrario, el enrutamiento continuará a otros objetos de destino de comando.

Ejemplos de estas formas:

- Inside Resource. h (normalmente generado por visual C++)

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- Dentro de la declaración de clase

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- Dentro de la definición del mapa de mensajes

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- En el archivo de implementación

    ```cpp
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

Los usuarios avanzados pueden controlar una variedad de comandos mediante el uso de un solo controlador de comandos: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) o ON_COMMAND_RANGE_EX. Consulte la documentación del producto para obtener más información sobre estas macros.

> [!NOTE]
> ClassWizard admite la creación de controladores ON_COMMAND y ON_UPDATE_COMMAND_UI, pero no admite la creación de controladores ON_COMMAND_EX o ON_COMMAND_RANGE. Sin embargo, el Asistente para clases se analizará y permitirá examinar las cuatro variantes del controlador de comandos.

## <a name="control-notification-messages"></a>Mensajes de notificación de control

Los mensajes que se envían desde controles secundarios a una ventana tienen un bit de información adicional en su entrada de mapa de mensajes: el identificador del control. Solo se llama al controlador de mensajes especificado en una entrada de mapa de mensajes si se cumplen las condiciones siguientes:

- El código de notificación de control (palabra alta de *lParam*), como BN_CLICKED, coincide con el código de notificación especificado en la entrada de mapa de mensajes.

- El identificador de control (*wParam*) coincide con el identificador de control especificado en la entrada de mapa de mensajes.

Los mensajes de notificación de controles personalizados pueden utilizar la macro [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) para definir una entrada de mapa de mensajes con un código de notificación personalizado. Esta macro tiene el formato

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

Para el uso avanzado [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) se puede usar para controlar una notificación de control específica de un intervalo de controles con el mismo controlador.

> [!NOTE]
> ClassWizard no admite la creación de un controlador ON_CONTROL o ON_CONTROL_RANGE en la interfaz de usuario. Debe escribirlos manualmente con el editor de texto. ClassWizard analizará estas entradas y permitirá examinarlas como cualquier otra entrada de mapa de mensajes.

Los controles comunes de Windows usan el [WM_NOTIFY](/windows/win32/controls/wm-notify) más eficaz para las notificaciones de control complejas. Esta versión de MFC tiene compatibilidad directa con este nuevo mensaje mediante las macros ON_NOTIFY y ON_NOTIFY_RANGE. Consulte la documentación del producto para obtener más información sobre estas macros.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
