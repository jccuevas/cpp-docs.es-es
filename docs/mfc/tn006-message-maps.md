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
ms.openlocfilehash: 3536cb215da04fb7114853d3fa5d764585cbb58e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306154"
---
# <a name="tn006-message-maps"></a>TN006: Mapas de mensajes

Esta nota describe la opción de mapa de mensajes MFC.

## <a name="the-problem"></a>El problema

Microsoft Windows implementa funciones virtuales en las clases de ventana que utilice su servicio de mensajería. Debido al gran número de mensajes implicada, proporcionando una función virtual independiente para cada mensaje de Windows crearía una vtable prohibitivamente grande.

Dado que cambia el número de mensajes definidos por el sistema de Windows con el tiempo, y dado que las aplicaciones pueden definir sus propios mensajes de Windows, mapas de mensajes proporcionan un nivel de direccionamiento indirecto que impide que los cambios de la interfaz de romper el código existente.

## <a name="overview"></a>Información general

MFC proporciona una alternativa a la instrucción switch que se usó en programas tradicionales de Windows para controlar los mensajes enviados a una ventana. Una asignación de mensajes a los métodos se puede definir para que cuando se recibe un mensaje de una ventana, se llama automáticamente al método apropiado. Este recurso de mapa de mensajes está diseñado para ser similar a funciones virtuales, pero tiene ventajas adicionales no son posibles con funciones virtuales de C++.

## <a name="defining-a-message-map"></a>Definir un mapa de mensajes

El [DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) macro declara tres miembros de una clase.

- Llama una matriz privada de entradas AFX_MSGMAP_ENTRY *_messageEntries*.

- Llama una estructura AFX_MSGMAP protegida *messageMap* que apunta a la *_messageEntries* matriz.

- Una función virtual llamado protegida `GetMessageMap` que devuelve la dirección de *messageMap*.

Esta macro debe colocarse en la declaración de cualquier clase con mapas de mensajes. Por convención, está al final de la declaración de clase. Por ejemplo:

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

Este es el formato generado por AppWizard y ClassWizard cuando creen nuevas clases. La / / {{y / /}} entre corchetes son necesarios para ClassWizard.

Tabla del mapa de mensajes se define mediante el uso de un conjunto de macros que se expanden a las entradas de mapa de mensajes. Una tabla comienza por un [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) llamada de macro, que define la clase que controla este mapa de mensajes y la clase primaria a la que se pasan los mensajes no controlados. La tabla finaliza con la [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) llamada de macro.

Entre estas dos macros llamadas es una entrada para cada mensaje que va a administrar este mapa de mensajes. Cada mensaje de Windows estándar tiene una macro del formulario ON_WM_*MESSAGE_NAME* que genera una entrada para ese mensaje.

Se ha definido una firma de función estándar para desempaquetar los parámetros de cada mensaje de Windows y para proporcionar seguridad de tipos. Estas firmas pueden encontrarse en el archivo Afxwin.h en la declaración de [CWnd](../mfc/reference/cwnd-class.md). Cada una de ellas está marcada con la palabra clave **afx_msg** para facilitar su identificación.

> [!NOTE]
> ClassWizard requiere el uso de la **afx_msg** palabra clave en las declaraciones de controlador de mapa de mensajes.

Estas firmas de función se derivaban mediante el uso de una convención simple. El nombre de la función siempre empieza por `"On`". Esto es seguido por el nombre del mensaje de Windows con el "WM_" quitado y la primera letra de cada palabra en mayúsculas. El orden de los parámetros es *wParam* seguido `LOWORD`(*lParam*), a continuación, `HIWORD`(*lParam*). No se pasan parámetros sin utilizar. Los identificadores que se ajustan a las clases de MFC se convierten en punteros a los objetos MFC adecuados. El ejemplo siguiente muestra cómo controlar el mensaje WM_PAINT y hacer el `CMyWnd::OnPaint` llamada a función:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

La tabla de asignación de mensajes debe definirse fuera del ámbito de cualquier definición de función o clase. No se debe colocar en un bloque extern "C".

> [!NOTE]
> ClassWizard modificará las entradas de mapa de mensajes que se producen entre la / / {{y / /}} corchete de comentario.

## <a name="user-defined-windows-messages"></a>Los mensajes de Windows definidos por el usuario

Mensajes definidos por el usuario pueden incluirse en un mapa de mensajes mediante el uso de la [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) macro. Esta macro acepta un número de mensaje y un método del formulario:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

En este ejemplo, establecemos un controlador para un mensaje personalizado que tiene un identificador de mensaje de Windows que deriva de la base WM_USER estándar para los mensajes definidos por el usuario. El ejemplo siguiente muestra cómo llamar a este controlador:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

El intervalo de mensajes definidos por el usuario que usan este enfoque debe estar en el intervalo WM_USER a 0x7fff.

> [!NOTE]
> ClassWizard no admite las rutinas de controlador ON_MESSAGE escribiendo desde la interfaz de usuario del Asistente para clases. También debe escribir manualmente desde el editor de Visual C++. ClassWizard analizará estas entradas y le permiten examinar ellos al igual que cualquier otra entrada de mapa de mensajes.

## <a name="registered-windows-messages"></a>Mensajes registrados de Windows

El [RegisterWindowMessage](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea) función se utiliza para definir un nuevo mensaje de ventana que se garantiza que sea único en todo el sistema. La macro ON_REGISTERED_MESSAGE sirve para controlar estos mensajes. Esta macro acepta un nombre de un *UINT CASI* variable que contiene el identificador de mensaje de windows registrados. Por ejemplo

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

La variable de Id. de mensaje registrada de Windows (WM_FIND en este ejemplo) debe ser un *NEAR* variable debido al modo en que se implementa ON_REGISTERED_MESSAGE.

La duración de los mensajes definidos por el usuario que usan este enfoque será en el intervalo 0xC000 a 0xFFFF.

> [!NOTE]
> ClassWizard no admite las rutinas de controlador ON_REGISTERED_MESSAGE escribiendo desde la interfaz de usuario del Asistente para clases. También debe escribir manualmente desde el editor de texto. ClassWizard analizará estas entradas y le permiten examinar ellos al igual que cualquier otra entrada de mapa de mensajes.

## <a name="command-messages"></a>Mensajes de comando

Mensajes de comandos de menús y los aceleradores se controlan de mapas de mensajes con el ON_COMMAND (macro). Esta macro acepta un identificador de comando y un método. Solo en el mensaje WM_COMMAND específico que tiene un *wParam* igual que el identificador se controla mediante el método especificado en la entrada de mapa de mensajes de comando especificado. Las funciones miembro de controlador de comando no toman ningún parámetro y devolver **void**. La macro tiene el formato siguiente:

```cpp
ON_COMMAND(id, memberFxn)
```

Comando update mensajes se enrutan a través del mismo mecanismo, pero use en su lugar la macro ON_UPDATE_COMMAND_UI. Funciones de miembro de controlador de actualización de comandos toman un único parámetro, un puntero a un [CCmdUI](../mfc/reference/ccmdui-class.md) objeto y devolver **void**. La macro tiene el formato

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Usuarios avanzados pueden usar el ON_COMMAND_EX (macro), que es una extensión de los controladores de mensajes de comando. La macro proporciona un superconjunto de la funcionalidad ON_COMMAND. Funciones miembro de controlador de comandos extendido toman un único parámetro, un **UINT** que contiene el identificador de comando y devolver un **BOOL**. El valor devuelto debe ser **TRUE** para indicar que se ha controlado el comando. Enrutamiento en caso contrario, continuará a otros objetos de destino del comando.

Ejemplos de estas formas:

- Inside Resource.h (normalmente generado por Visual C++)

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

- Dentro de la definición de asignación de mensaje

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

Los usuarios avanzados pueden controlar una variedad de comandos utilizando un controlador de comandos única: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) o ON_COMMAND_RANGE_EX. Consulte la documentación del producto para obtener más información sobre estas macros.

> [!NOTE]
> ClassWizard admite la creación de controladores ON_COMMAND y ON_UPDATE_COMMAND_UI, pero no admite la creación de controladores ON_COMMAND_EX o ON_COMMAND_RANGE. Sin embargo, clase de asistente analizará y le permiten examinar todas las variantes de controlador de comando de cuatro.

## <a name="control-notification-messages"></a>Mensajes de notificación de control

Los mensajes enviados desde los controles secundarios a una ventana tiene un adicional el bit de información en su mensaje de entrada de mapa: identificador. del control Se llama el controlador de mensajes especificado en una entrada de asignación de mensaje solo si las condiciones siguientes son verdaderas:

- El código de notificación de control (palabra alta de *lParam*), como BN_CLICKED, coincide con el código de notificación especificado en la entrada de mapa de mensajes.

- El identificador de control (*wParam*) coincide con el identificador del control especificado en la entrada de mapa de mensajes.

Mensajes de notificación de control personalizado pueden usar el [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) macro para definir una entrada de asignación de mensaje con un código de notificación personalizada. Esta macro tiene el formato

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

Para uso avanzado [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) puede usarse para controlar una notificación de control específico de una gama de controles con el mismo controlador.

> [!NOTE]
> ClassWizard no admite la creación de un controlador ON_CONTROL o ON_CONTROL_RANGE en la interfaz de usuario. También debe escribir manualmente con el editor de texto. ClassWizard analizará estas entradas y le permiten examinar ellos al igual que otras entradas de mapa de mensajes.

Utilice el método más eficaz los controles comunes de Windows [WM_NOTIFY](/windows/desktop/controls/wm-notify) para las notificaciones de control complejo. Esta versión de MFC tiene compatibilidad directa para el nuevo mensaje mediante el uso de las macros de mensajes ON_NOTIFY y ON_NOTIFY_RANGE. Consulte la documentación del producto para obtener más información sobre estas macros.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
