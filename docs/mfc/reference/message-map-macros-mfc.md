---
title: Macros de mapa de mensajes (MFC)
ms.date: 03/27/2019
f1_keywords:
- AFXWIN/DECLARE_MESSAGE_MAP
- AFXWIN/BEGIN_MESSAGE_MAP
- AFXWIN/BEGIN_TEMPLATE_MESSAGE_MAP
- AFXWIN/END_MESSAGE_MAP
- AFXWIN/ON_COMMAND
- AFXWIN/ON_COMMAND_EX
- AFXWIN/ON_CONTROL
- AFXWIN/ON_MESSAGE
- AFXWIN/ON_OLECMD
- AFXWIN/ON_REGISTERED_MESSAGE
- AFXWIN/ON_REGISTERED_THREAD_MESSAGE
- AFXWIN/ON_THREAD_MESSAGE
- AFXWIN/ON_UPDATE_COMMAND_UI
- AFXWIN/ON_COMMAND_RANGE
- AFXWIN/ON_UPDATE_COMMAND_UI_RANGE
- AFXWIN/ON_CONTROL_RANGE
helpviewer_keywords:
- message map macros
- Windows messages [MFC], declaration
- demarcating Windows messages
- message maps [MFC], macros
- message maps [MFC], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
ms.openlocfilehash: 6e9291f0f39057403bc27c7fe4ff5ca5a82dfe3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356582"
---
# <a name="message-map-macros-mfc"></a>Macros de mapa de mensajes (MFC)

Para admitir mapas de mensajes, MFC proporciona las siguientes macros:

### <a name="message-map-declaration-and-demarcation-macros"></a>Macros de declaración y demarcación de mapa de mensajes

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Declara que se usará un mapa de mensajes en una clase para asignar mensajes a funciones (debe utilizarse en la declaración de clase).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Comienza la definición de un mapa de mensajes (debe usarse en la implementación de la clase).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Comienza la definición de un mapa de mensajes en un tipo de clase que contiene un único argumento de plantilla. |
|[END_MESSAGE_MAP](#end_message_map)|Finaliza la definición de un mapa de mensajes (debe utilizarse en la implementación de la clase).|

### <a name="message-mapping-macros"></a>Macros de asignación de mensajes

|||
|-|-|
|[ON_COMMAND](#on_command)|Indica qué función controlará un mensaje de comando especificado.|
|[ON_COMMAND_EX](#on_command_ex)|Indica qué función controlará un mensaje de comando especificado.|
|[ON_CONTROL](#on_control)|Indica qué función controlará un mensaje de notificación de control especificado.|
|[ON_MESSAGE](#on_message)|Indica qué función controlará un mensaje definido por el usuario.|
|[ON_OLECMD](#on_olecmd)|Indica qué función controlará un comando de menú desde un DocObject o su contenedor.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Indica qué función controlará un mensaje registrado definido por el usuario.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Indica qué función controlará un mensaje definido `CWinThread` por el usuario registrado cuando tenga una clase.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Indica qué función controlará un mensaje definido `CWinThread` por el usuario cuando tenga una clase.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Indica qué función controlará un mensaje de comando de actualización de interfaz de usuario especificado.|

### <a name="message-map-range-macros"></a>Macros de rango de mapa de mensajes

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Indica qué función controlará el rango de identificadores de comando especificado en los dos primeros parámetros de la macro.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Indica qué controlador de actualización controlará el intervalo de identificadores de comando especificado en los dos primeros parámetros de la macro.|
|[ON_CONTROL_RANGE](#on_control_range)|Indica qué función controlará las notificaciones del intervalo de identificadores de control especificado en el segundo y tercer parámetros de la macro. El primer parámetro es un mensaje de notificación de control, como BN_CLICKED.|

Para obtener más información sobre los mapas de mensajes, las macros de declaración y demarcación de mapa de mensajes y las macros de asignación de mensajes, vea [Mapas](../../mfc/reference/message-maps-mfc.md) de mensajes y Temas de [control y asignación](../../mfc/message-handling-and-mapping.md)de mensajes . Para obtener más información acerca de los intervalos de mapa de mensajes, vea [Controladores para intervalos de mapa](../../mfc/handlers-for-message-map-ranges.md)de mensajes .

## <a name="begin_message_map"></a><a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

Comienza la definición del mapa de mensajes.

### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase cuyo mapa de mensajes es.

*baseClass*<br/>
Especifica el nombre de la clase base de *theClass*.

### <a name="remarks"></a>Observaciones

En el archivo de implementación (.cpp) que define las funciones miembro de la clase, inicie el mapa de mensajes con la macro BEGIN_MESSAGE_MAP, agregue entradas de macro para cada una de las funciones de controlador de mensajes y complete el mapa de mensajes con la macro END_MESSAGE_MAP.

Para obtener más información acerca de los mapas de mensajes, consulte [Mapas](message-maps-mfc.md) de mensajes

### <a name="example"></a>Ejemplo

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

Comienza la definición de un mapa de mensajes en un tipo de clase que contiene un único argumento de plantilla.

### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase cuyo mapa de mensajes es.

*type_name*<br/>
El nombre del parámetro de plantilla especificado para la clase.

*baseClass*<br/>
Especifica el nombre de la clase base de *theClass*.

### <a name="remarks"></a>Observaciones

Esta macro es similar a la [macro BEGIN_MESSAGE_MAP;](message-map-macros-mfc.md#begin_message_map) sin embargo, esta macro está pensada para clases que contienen un único argumento de plantilla.

En la sección de implementación del método de la clase, inicie el mapa de mensajes con la macro BEGIN_TEMPLATE_MESSAGE_MAP; a continuación, agregue entradas de macro para cada uno de los métodos de controlador de mensajes como lo haría para un mapa de mensajes estándar. Al igual que con la macro BEGIN_MESSAGE_MAP, complete el mapa de mensajes de plantilla con la macro [END_MESSAGE_MAP.](message-map-macros-mfc.md#end_message_map)

Para obtener más información sobre la implementación de mapas de mensajes para clases de plantilla, consulte [Cómo: Crear un mapa](../how-to-create-a-message-map-for-a-template-class.md)de mensajes para una clase de plantilla .

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

Declara que la clase define un mapa de mensajes. Cada `CCmdTarget`clase derivada del programa debe proporcionar un mapa de mensajes para controlar los mensajes.

### <a name="syntax"></a>Sintaxis

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Observaciones

Utilice la macro DECLARE_MESSAGE_MAP al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones miembro de la clase, use la macro BEGIN_MESSAGE_MAP, las entradas de macro para cada una de las funciones de controlador de mensajes y la macro END_MESSAGE_MAP.

> [!NOTE]
> Si declara algún miembro después de DECLARE_MESSAGE_MAP, debe especificar un nuevo tipo de acceso (**public**, **private**o **protected**) para ellos.

Para obtener más información sobre los mapas de mensajes y la macro de DECLARE_MESSAGE_MAP, vea Temas de [control y asignación](../../mfc/message-handling-and-mapping.md)de mensajes .

### <a name="example"></a>Ejemplo

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a>END_MESSAGE_MAP

Finaliza la definición del mapa de mensajes.

### <a name="syntax"></a>Sintaxis

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Observaciones

Para obtener más información sobre los mapas de mensajes y la macro de END_MESSAGE_MAP, vea Temas de [control y asignación](../../mfc/message-handling-and-mapping.md)de mensajes .

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="on_command"></a><a name="on_command"></a>ON_COMMAND

Esta macro asigna un mensaje de comando a una función miembro.

### <a name="syntax"></a>Sintaxis

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Parámetros

*commandId*<br/>
Identificador del comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

### <a name="remarks"></a>Observaciones

Indica qué función controlará un mensaje de comando de un objeto de interfaz de usuario de comando, como un elemento de menú o un botón de barra de herramientas.

Cuando un objeto de destino de comando recibe un mensaje de WM_COMMAND `memberFxn` de Windows con el identificador especificado, ON_COMMAND llamará a la función miembro para controlar el mensaje.

Utilice ON_COMMAND para asignar un único comando a una función miembro. Utilice [ON_COMMAND_RANGE](#on_command_range) para asignar un rango de identificadores de comando a una función miembro. Solo una entrada de mapa de mensajes puede coincidir con un ID de comando determinado. Es decir, no puede asignar un comando a más de un controlador. Para obtener más información y ejemplos, vea Temas de [control y asignación](../../mfc/message-handling-and-mapping.md)de mensajes .

### <a name="example"></a>Ejemplo

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_command_ex"></a><a name="on_command_ex"></a>ON_COMMAND_EX

Función miembro de controlador de comandos extendida.

### <a name="syntax"></a>Sintaxis

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Parámetros

*commandId*<br/>
Identificador del comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

### <a name="remarks"></a>Observaciones

Una forma extendida de controladores de mensajes de comando está disponible para usos avanzados. La macro ON_COMMAND_EX se utiliza para estos controladores de mensajes y proporciona un superconjunto de la funcionalidad [de ON_COMMAND.](message-map-macros-mfc.md#on_command) Las funciones miembro del controlador de comandos extendido toman un único parámetro, un UINT que contiene el identificador de comando y devuelven un BOOL. El valor devuelto debe ser TRUE para indicar que se ha controlado el comando; de lo contrario, el enrutamiento continuará a otros objetos de destino de comando.

Para obtener más información, consulte Nota técnica [TN006: Mapas de mensajes]tm006-message-maps.md).

### <a name="requirements"></a>Requisitos

Archivo de encabezado: afxmsg_.h

## <a name="on_control"></a><a name="on_control"></a>ON_CONTROL

Indica qué función controlará un mensaje de notificación de control personalizado.

### <a name="syntax"></a>Sintaxis

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Parámetros

*wNotifyCode*<br/>
El código de notificación del control.

*commandId*<br/>
Identificador del comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

### <a name="remarks"></a>Observaciones

Los mensajes de notificación de control son los que se envían desde un control a su ventana primaria.

Debe haber exactamente una ON_CONTROL instrucción de macro en el mapa de mensajes para cada mensaje de notificación de control que se debe asignar a una función de controlador de mensajes.

Para obtener más información y ejemplos, vea Temas de [control y asignación](../../mfc/message-handling-and-mapping.md)de mensajes .

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_message"></a><a name="on_message"></a>ON_MESSAGE

Indica qué función controlará un mensaje definido por el usuario.

### <a name="syntax"></a>Sintaxis

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parámetros

*Mensaje*<br/>
El id. del mensaje.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el mensaje.

El tipo de la `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`función debe ser .

### <a name="remarks"></a>Observaciones

Los mensajes definidos por el usuario son mensajes que no son mensajes estándar de Windows WM_MESSAGE. Al seleccionar un ID de mensaje, debe utilizar valores dentro del intervalo de WM_USER (0x0400) a 0x7FFF o WM_APP (0x8000) a 0xBFFF. Para obtener más información sobre los ID de mensajes, consulte [WM_APP](/windows/win32/winmsg/wm-app).

Debe haber exactamente una ON_MESSAGE instrucción de macro en el mapa de mensajes para cada mensaje definido por el usuario que se debe asignar a una función de controlador de mensajes.

> [!NOTE]
> Además de los mensajes definidos por el usuario, ON_MESSAGE controla los mensajes de Windows menos comunes. Para obtener más información, consulte [Mapas](../../mfc/tn006-message-maps.md)de mensajes .

Para obtener más información y ejemplos, consulte Temas de [control y asignación](../../mfc/message-handling-and-mapping.md) de mensajes y [controladores definidos por el usuario](user-defined-handlers.md)

### <a name="example"></a>Ejemplo

```cpp
#define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd2, CWnd)
   ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()

// inside the class declaration
afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

LRESULT CMyWnd2::OnMyMessage(WPARAM wParam, LPARAM lParam)
{
   UNREFERENCED_PARAMETER(wParam);
   UNREFERENCED_PARAMETER(lParam);

   // Handle message here.

   return 0;
}
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_olecmd"></a><a name="on_olecmd"></a>ON_OLECMD

Enruta los comandos `IOleCommandTarget`a través de la interfaz de envío de comandos.

### <a name="syntax"></a>Sintaxis

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Parámetros

*pguid*<br/>
Identificador del grupo de comandos al que pertenece el comando. Use NULL para el grupo estándar.

*olecmdid*<br/>
Identificador del comando OLE.

*commandId*<br/>
El identificador de menú, el identificador de barra de herramientas, el identificador de botón u otro identificador del recurso u objeto que emite el comando.

### <a name="remarks"></a>Observaciones

`IOleCommandTarget`Permite que un contenedor reciba comandos que se originan en la interfaz de usuario de un DocObject y permite que el contenedor envíe los mismos comandos (como Nuevo, Abrir, Guardar como e Imprimir en el menú Archivo; y Copiar, Pegar, Deshacer, etc. en el menú Editar) a un DocObject.

`IOleCommandTarget`es más simple que `IDispatch`OLE Automation. `IOleCommandTarget`se basa enteramente en un conjunto estándar de comandos que rara vez tienen argumentos, y no hay información de tipo involucrada (la seguridad de tipos también se reduce para los argumentos de comando). Si necesita distribuir comandos con argumentos, utilice [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

MFC `IOleCommandTarget` ha implementado los comandos de menú estándar en las macros siguientes:

**ON_OLECMD_CLEARSELECTION( )**

Distribuye el comando Editar borrado. Implementado como:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY( )**

Distribuye el comando Editar copia. Implementado como:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT( )**

Distribuye el comando Editar corte. Implementado como:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW( )**

Distribuye el comando Archivo nuevo. Implementado como:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN( )**

Distribuye el comando Abrir archivo. Implementado como:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP( )**

Distribuye el comando Configuración de página de archivos. Implementado como:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE( )**

Distribuye el comando Editar pegar. Implementado como:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL( )**

Distribuye el comando Editar pegado especial especial. Implementado como:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT( )**

Distribuye el comando Impresión de archivos. Implementado como:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW( )**

Distribuye el comando Vista previa de impresión de archivos. Implementado como:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO( )**

Distribuye el comando Editar rehacer. Implementado como:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE( )**

Distribuye el comando Guardar archivo. Implementado como:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS( )**

Distribuye el comando Guardar como archivo. Implementado como:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS( )**

Distribuye el comando Archivo Guardar copia como. Implementado como:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL( )**

Distribuye el comando Editar seleccionar todo. Implementado como:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO( )**

Distribuye el comando Editar deshacer. Implementado como:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdocob.h

## <a name="on_registered_message"></a><a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

La `RegisterWindowMessage` función de Windows se utiliza para definir un nuevo mensaje de ventana que se garantiza que es único en todo el sistema.

### <a name="syntax"></a>Sintaxis

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parámetros

*nMessageVariable*<br/>
La variable de ID de mensaje de ventana registrada.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el mensaje.

### <a name="remarks"></a>Observaciones

Esta macro indica qué función controlará el mensaje registrado.

Para obtener más información y ejemplos, vea Temas de [control y asignación](../../mfc/message-handling-and-mapping.md)de mensajes .

### <a name="example"></a>Ejemplo

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

Indica qué función controlará el mensaje registrado por la función RegisterWindowMessage de Windows.

### <a name="syntax"></a>Sintaxis

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parámetros

*nMessageVariable*<br/>
La variable de ID de mensaje de ventana registrada.

*memberFxn*<br/>
El nombre de la función CWinThread-message-handler a la que se asigna el mensaje.

### <a name="remarks"></a>Observaciones

RegisterWindowMessage se utiliza para definir un nuevo mensaje de ventana que se garantiza que es único en todo el sistema. ON_REGISTERED_THREAD_MESSAGE debe usarse en lugar de ON_REGISTERED_MESSAGE cuando tiene una clase CWinThread.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_thread_message"></a><a name="on_thread_message"></a>ON_THREAD_MESSAGE

Indica qué función controlará un mensaje definido por el usuario.

### <a name="syntax"></a>Sintaxis

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parámetros

*Mensaje*<br/>
El id. del mensaje.

*memberFxn*<br/>
El nombre `CWinThread`de la función -message-handler a la que se asigna el mensaje.

### <a name="remarks"></a>Observaciones

ON_THREAD_MESSAGE debe utilizarse en lugar `CWinThread` de ON_MESSAGE cuando tiene una clase. Los mensajes definidos por el usuario son mensajes que no son mensajes estándar de Windows WM_MESSAGE. Debe haber exactamente una ON_THREAD_MESSAGE instrucción de macro en el mapa de mensajes para cada mensaje definido por el usuario que se debe asignar a una función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

Esta macro indica qué función controlará un mensaje de comando de actualización de la interfaz de usuario.

### <a name="syntax"></a>Sintaxis

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Parámetros

*messageId*<br/>
El id. del mensaje.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el mensaje.

### <a name="remarks"></a>Observaciones

Debe haber exactamente una instrucción de macro ON_UPDATE_COMMAND_UI en el mapa de mensajes para cada comando de actualización de interfaz de usuario que se debe asignar a una función de controlador de mensajes.

Para obtener más información y ejemplos, vea Temas de [control y asignación](../../mfc/message-handling-and-mapping.md)de mensajes .

### <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="on_command_range"></a><a name="on_command_range"></a>ON_COMMAND_RANGE

Utilice esta macro para asignar un intervalo contiguo de id de comando a una única función de controlador de mensajes.

### <a name="syntax"></a>Sintaxis

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parámetros

*id1*<br/>
IDENTIFICADOR de comando al principio de un intervalo contiguo de identificadores de comando.

*id2*<br/>
IDENTIFICADOR de comando al final de un intervalo contiguo de identificadores de comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asignan los comandos.

### <a name="remarks"></a>Observaciones

El rango de ID comienza con *id1* y termina con *id2*.

Utilice ON_COMMAND_RANGE para asignar un rango de identificadores de comando a una función miembro. Utilice [ON_COMMAND](#on_command) para asignar un único comando a una función miembro. Solo una entrada de mapa de mensajes puede coincidir con un ID de comando determinado. Es decir, no puede asignar un comando a más de un controlador. Para obtener más información sobre la asignación de intervalos de mensajes, vea [Controladores de intervalos de mapas de mensajes](../../mfc/handlers-for-message-map-ranges.md).

No hay compatibilidad automática con los intervalos de mapas de mensajes, por lo que debe colocar la macro usted mismo.

### <a name="example"></a>Ejemplo

```cpp
// The code fragment below shows how to use ON_COMMAND_RANGE macro
// to map a contiguous range of command IDs to a single message
// handler function (i.e. OnRangeCmds() in the sample below). In
// addition, it also shows how to use CheckMenuRadioItem() to check a
// selected menu item and makes it a radio item.

BEGIN_MESSAGE_MAP(CChildFrame, CMDIChildWnd)
   ON_COMMAND_RANGE(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, &CChildFrame::OnRangeCmds)
END_MESSAGE_MAP()

void CChildFrame::OnRangeCmds(UINT nID)
{
   CMenu* mmenu = AfxGetMainWnd()->GetMenu();
   CMenu* submenu = mmenu->GetSubMenu(5);
   submenu->CheckMenuRadioItem(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3,
      nID, MF_BYCOMMAND);
}
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

Asigna un intervalo contiguo de id a los id de comando a una única función de controlador de mensajes de actualización.

### <a name="syntax"></a>Sintaxis

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parámetros

*id1*<br/>
IDENTIFICADOR de comando al principio de un intervalo contiguo de identificadores de comando.

*id2*<br/>
IDENTIFICADOR de comando al final de un intervalo contiguo de identificadores de comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes de actualización a la que se asignan los comandos.

### <a name="remarks"></a>Observaciones

Actualizar controladores de mensajes actualizar el estado de los elementos de menú y botones de barra de herramientas asociados con el comando. El rango de ID comienza con *id1* y termina con *id2*.

No hay compatibilidad automática con los intervalos de mapas de mensajes, por lo que debe colocar la macro usted mismo.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_control_range"></a><a name="on_control_range"></a>ON_CONTROL_RANGE

Utilice esta macro para asignar un intervalo contiguo de id a los id de control a una única función de controlador de mensajes para un mensaje de notificación de Windows especificado, como BN_CLICKED.

### <a name="syntax"></a>Sintaxis

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Parámetros

*wNotifyCode*<br/>
El código de notificación al que responde el controlador.

*id1*<br/>
Identificador de comando al principio de un intervalo contiguo de identificadores de control.

*id2*<br/>
Identificador de comando al final de un intervalo contiguo de identificadores de control.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asignan los controles.

### <a name="remarks"></a>Observaciones

El rango de ID comienza con *id1* y termina con *id2*. Se llama al controlador para la notificación especificada procedente de cualquiera de los controles asignados.

No hay compatibilidad automática con los intervalos de mapas de mensajes, por lo que debe colocar la macro usted mismo.

Para obtener más información sobre la implementación de funciones de controlador para un intervalo de id de control, consulte [controladores para intervalos de mapa](../../mfc/handlers-for-message-map-ranges.md)de mensajes .

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="see-also"></a>Consulte también

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006: Mapas de mensajes](../tn006-message-maps.md)<br/>
[Clase COleCmdUI](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[Controladores definidos por el usuario](user-defined-handlers.md)<br/>
[CCmdUI (clase)](ccmdui-class.md)
