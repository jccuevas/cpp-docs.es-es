---
title: 'TN006: Mapas de mensajes | Documentos de Microsoft'
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.messages.maps
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c4bc820c6b54e055235c1bd29bd55ccfc032c92
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121681"
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

- Llama a una matriz de entradas AFX_MSGMAP_ENTRY privada *_messageEntries*.

- Llama a una estructura AFX_MSGMAP protegida *messageMap* que apunta a la *_messageEntries* matriz.

- Una función virtual denominado protegida `GetMessageMap` que devuelve la dirección de *messageMap*.

Esta macro se debe colocar en la declaración de cualquier clase con mapas de mensajes. Por convención, es el final de la declaración de clase. Por ejemplo:

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

Este es el formato generado por AppWizard y ClassWizard al crear nuevas clases. El / / {{y / /}} corchetes son necesarios para ClassWizard.

Tabla del mapa de mensajes se define mediante un conjunto de macros que se expanden a las entradas de mapa de mensajes. Una tabla comienza por un [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) llamada de macro, que define la clase que controla este mapa de mensajes y la clase primaria a la que se pasan los mensajes no controlados. La tabla termina con la [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) llamada de macro.

Entre estas llamadas a dos macros es una entrada para cada mensaje que se va a ser controlada por este mapa de mensajes. Cada mensaje estándar de Windows tiene una macro del formulario ON_WM_*MESSAGE_NAME* que genera una entrada para ese mensaje.

Se ha definido una firma de función estándar para desempaquetar los parámetros de cada mensaje de Windows y proporciona seguridad de tipos. Estas firmas pueden encontrarse en el archivo Afxwin.h en la declaración de [CWnd](../mfc/reference/cwnd-class.md). Cada una de ellas está marcada con la palabra clave **afx_msg** para facilitar su identificación.

> [!NOTE]
> ClassWizard requiere el uso de la **afx_msg** palabra clave en las declaraciones de controlador de mapa de mensajes.

 Estas firmas de función obtenidas mediante una convención simple. El nombre de la función siempre empieza por `"On`". Esto es seguido por el nombre del mensaje de Windows con la "WM_" quitado y la primera letra de cada palabra en mayúsculas. El orden de los parámetros es *wParam* seguido `LOWORD`(*lParam*), a continuación, `HIWORD`(*lParam*). No se pasan parámetros sin utilizar. Los identificadores que se ajustan las clases de MFC se convierten en punteros a los objetos MFC adecuados. En el ejemplo siguiente se muestra cómo controlar el mensaje WM_PAINT y hacer el `CMyWnd::OnPaint` función que se llamará:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

 La tabla de asignación de mensajes debe definirse fuera del ámbito de cualquier definición de función o clase. No se deben colocar en un bloque extern "C".

> [!NOTE]
> ClassWizard modificará las entradas del mapa de mensajes que se producen entre la / / {{y / /}} corchete de cierre de comentario.

## <a name="user-defined-windows-messages"></a>Mensajes de Windows definidas por el usuario

Mensajes definidos por el usuario pueden incluirse en un mapa de mensajes mediante el uso de la [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) macro. Esta macro acepta un número de mensaje y un método de la forma:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

En este ejemplo, establecemos un controlador para un mensaje personalizado que tiene un identificador de mensaje de Windows que deriva de la base WM_USER estándar para los mensajes definidos por el usuario. En el ejemplo siguiente se muestra cómo llamar a este controlador:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

El intervalo de mensajes definidos por el usuario que use este enfoque debe estar en el intervalo WM_USER que 0x7fff.

> [!NOTE]
> ClassWizard no admite al escribir rutinas de controlador ON_MESSAGE desde la interfaz de usuario de ClassWizard. También debe escribir manualmente en el editor de Visual C++. ClassWizard analizará estas entradas y le permiten examinar ellos al igual que las demás entradas de mapa de mensajes.

## <a name="registered-windows-messages"></a>Mensajes de Windows registrados

El [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) función se utiliza para definir un nuevo mensaje de ventana que se garantiza que sea único en todo el sistema. La macro ON_REGISTERED_MESSAGE se utiliza para controlar estos mensajes. Esta macro acepta un nombre de un *UINT cerca* variable que contiene el identificador de mensaje de windows registrados. Por ejemplo

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

La duración de los mensajes definidos por el usuario que use este enfoque será en el intervalo 0xC000 a 0xFFFF.

> [!NOTE]
> ClassWizard no admite al escribir rutinas de controlador ON_REGISTERED_MESSAGE desde la interfaz de usuario de ClassWizard. También debe escribir manualmente desde el editor de texto. ClassWizard analizará estas entradas y le permiten examinar ellos al igual que las demás entradas de mapa de mensajes.

## <a name="command-messages"></a>Mensajes de comando

Mensajes de comandos de menús y aceleradores se controlan de mapas de mensajes con el ON_COMMAND (macro). Esta macro acepta un identificador de comando y un método. Solo en el mensaje WM_COMMAND específico que tiene un *wParam* igual que el identificador se controla mediante el método especificado en la entrada de mapa de mensajes de comando especificado. Funciones de miembro de controlador de comandos no toman ningún parámetro y devolver **void**. La macro tiene el formato siguiente:

```cpp
ON_COMMAND(id, memberFxn)
```

Mensajes de actualización de comandos se enrutan a través del mecanismo de la mismo, pero utilice la macro ON_UPDATE_COMMAND_UI en su lugar. Funciones de miembro de controlador de actualización de comandos toman un único parámetro, un puntero a un [CCmdUI](../mfc/reference/ccmdui-class.md) de objetos y devolver **void**. La macro tiene el formato

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Los usuarios avanzados pueden usar la ON_COMMAND_EX (macro), que es una forma ampliada de controladores de mensajes de comando. La macro proporciona un superconjunto de la funcionalidad ON_COMMAND. Funciones miembro de controlador de comandos extendidos toman un único parámetro, un **UINT** que contiene el identificador de comando y devolver un **BOOL**. El valor devuelto debe ser **TRUE** para indicar que el comando se ha controlado. En caso contrario, el enrutamiento seguirá a otros objetos de destino del comando.

Ejemplos de estas formas:

- Inside Resource.h (normalmente generados por Visual C++)

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

- Dentro de la definición de la asignación de mensajes

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

 Los usuarios avanzados pueden controlar una variedad de comandos mediante el uso de un controlador de comandos única: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) o ON_COMMAND_RANGE_EX. Consulte la documentación del producto para obtener más información acerca de estas macros.

> [!NOTE]
> ClassWizard admite controladores ON_COMMAND y ON_UPDATE_COMMAND_UI creación, pero no admite la creación de controladores ON_COMMAND_EX o ON_COMMAND_RANGE. Sin embargo, Asistente para clases analizará y le permiten examinar todas las variantes de controlador de cuatro comandos.

## <a name="control-notification-messages"></a>Mensajes de notificación de control

Entrada de mapa de mensajes que se envían desde los controles secundarios a una ventana tiene adicional el bit de información en su mensaje: identificador. del control Se llama al controlador de mensaje especificado en una entrada de mapa de mensajes únicamente si se cumple las condiciones siguientes:

- El código de notificación de control (bytes más significativos del *lParam*), como BN_CLICKED, coincide con el código de notificación especificado en la entrada de mapa de mensajes.

- El identificador del control (*wParam*) coincide con el identificador del control especificado en la entrada de mapa de mensajes.

Mensajes de notificación de control personalizado pueden utilizar el [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) macro para definir una entrada de mapa de mensajes con un código de notificación personalizada. Esta macro tiene el formato

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

Para uso avanzado de [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) puede usarse para controlar una notificación de control específico de un intervalo de controles con el mismo controlador.

> [!NOTE]
> ClassWizard no admite la creación de un controlador de ON_CONTROL o ON_CONTROL_RANGE en la interfaz de usuario. También debe escribir manualmente con el editor de texto. ClassWizard analizará estas entradas y le permiten examinar ellos al igual que otras entradas de mapa de mensajes.

Usar la forma más eficaz los controles comunes de Windows [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) para las notificaciones de control complejo. Esta versión de MFC tiene una compatibilidad directa para el nuevo mensaje mediante el uso de las macros ON_NOTIFY y ON_NOTIFY_RANGE. Consulte la documentación del producto para obtener más información acerca de estas macros.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)  
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)  
