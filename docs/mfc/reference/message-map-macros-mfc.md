---
title: Macros de mapa (MFC) del mensaje | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2d5a0f2f5f7515e36997b876373dcf25bb6fc03
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890639"
---
# <a name="message-map-macros-mfc"></a>Macros de mapa de mensajes (MFC)

Para admitir mapas de mensajes, MFC proporciona las siguientes macros:

### <a name="message-map-declaration-and-demarcation-macros"></a>Declaración de mapa de mensajes y las Macros de delimitación

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Declara que se utilizará un mapa de mensajes en una clase para asignar mensajes a funciones (debe usarse en la declaración de clase).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Inicia la definición de un mapa de mensajes (debe usarse en la implementación de la clase).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_interface_map)|Inicia la definición de un mapa de mensajes en un tipo de clase que contiene un argumento de plantilla único. |
|[END_MESSAGE_MAP](#end_message_map)|Termina la definición de un mapa de mensajes (debe usarse en la implementación de la clase).|

### <a name="message-mapping-macros"></a>Macros de asignación de mensajes

|||
|-|-|
|[ON_COMMAND](#on_command)|Indica qué función va a controlar un mensaje de comando especificado.|
|[ON_COMMAND_EX](#on_command_ex)|Indica qué función va a controlar un mensaje de comando especificado.|
|[ON_CONTROL](#on_control)|Indica qué función va a controlar un mensaje de notificación de control especificado.|
|[ON_MESSAGE](#on_message)|Indica qué función va a controlar un mensaje definido por el usuario.|
|[ON_OLECMD](#on_olecmd)|Indica qué función va a controlar un comando de menú de DocObject o su contenedor.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Indica qué función va a controlar un mensaje definido por el usuario registrado.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Indica qué función va a controlar un mensaje definido por el usuario registrado cuando tiene un `CWinThread` clase.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Indica qué función va a controlar un mensaje definido por el usuario cuando haya un `CWinThread` clase.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Indica qué función va a controlar un mensaje de comando de actualización de interfaz de usuario especificado.|

### <a name="message-map-range-macros"></a>Macros de mapa de mensajes intervalo

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Indica qué función va a controlar el intervalo de identificadores de comando especificados en los dos primeros parámetros a la macro.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Indica qué controlador de actualización va a controlar el intervalo de identificadores de comando especificados en los dos primeros pa] Pará a la macro.|
|[ON_CONTROL_RANGE](#on_control_range)|Indica la función que controlará las notificaciones desde el intervalo de identificadores especificados en los parámetros segundo y terceros a la macro de control. El primer parámetro es un mensaje de notificación de control, como BN_CLICKED.|

Para obtener más información sobre los mapas de mensajes, la declaración de mapa de mensajes y macros de delimitación y las macros de asignación de mensajes, vea [mapas de mensajes](../../mfc/reference/message-maps-mfc.md) y [de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md). Para obtener más información acerca de los intervalos de mapa de mensajes, vea [controladores para intervalos de mapa de mensajes de](../../mfc/handlers-for-message-map-ranges.md).

## <a name="begin_message_map"></a> BEGIN_MESSAGE_MAP

Inicia la definición de su mapa de mensajes.

### <a name="syntax"></a>Sintaxis

```
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase cuyo mensaje asignarlo.

*baseClass*<br/>
Especifica el nombre de la clase base de *theClass*.

### <a name="remarks"></a>Comentarios

En el archivo de implementación (.cpp) que define las funciones de miembro para la clase, inicie el mapa de mensajes con el BEGIN_MESSAGE_MAP (macro), a continuación, agregue entradas de macro para cada una de las funciones de controlador de mensajes y completar el mapa de mensajes con el END_MESSAGE_MAP macro.

Para obtener más información acerca de mapas de mensajes, vea [mapas de mensajes](message-maps-mfc.md)

### <a name="example"></a>Ejemplo

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

Inicia la definición de un mapa de mensajes en un tipo de clase que contiene un argumento de plantilla único.

### <a name="syntax"></a>Sintaxis

```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
Especifica el nombre de la clase cuyo mensaje asignarlo.

*type_name*<br/>
El nombre del parámetro de plantilla especificado para la clase.

*baseClass*<br/>
Especifica el nombre de la clase base de *theClass*.

### <a name="remarks"></a>Comentarios

Esta macro es similar a la [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) macro; sin embargo, esta macro está pensada para las clases que contiene un argumento de plantilla único.

En la sección de implementación del método de la clase, comenzará el mapa de mensajes con la macro BEGIN_TEMPLATE_MESSAGE_MAP; a continuación, agregue entradas de macro para cada uno de los métodos de controlador de mensajes como lo haría para un mapa de mensajes estándar. Como con la macro BEGIN_MESSAGE_MAP, complete el mapa de mensajes de la plantilla con el [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) macro.

Para obtener más información sobre la implementación de mapas de mensajes para las clases de plantilla, consulte [Cómo: crear un mapa de mensajes para una clase de plantilla](../how-to-create-a-message-map-for-a-template-class.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="declare_message_map"></a>  DECLARE_MESSAGE_MAP

Declara que la clase define un mapa de mensajes. Cada `CCmdTarget`-clase derivada en el programa debe proporcionar un mapa de mensajes para controlar los mensajes.

### <a name="syntax"></a>Sintaxis

```
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Comentarios

Utilice la macro DECLARE_MESSAGE_MAP al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones miembro de la clase, use el BEGIN_MESSAGE_MAP (macro), las entradas de la macro para cada una de las funciones de controlador de mensajes y el END_MESSAGE_MAP (macro).

> [!NOTE]
>  Si se declara cualquier miembro después DECLARE_MESSAGE_MAP, debe especificar un nuevo tipo de acceso (**pública**, **privada**, o **protegido**) para ellos.

Para obtener más información sobre los mapas de mensajes y el DECLARE_MESSAGE_MAP (macro), consulte [de mensajes y asignación de temas](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Ejemplo

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="end_message_map"></a>  END_MESSAGE_MAP

Termina la definición de su mapa de mensajes.

### <a name="syntax"></a>Sintaxis

```
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Comentarios

Para obtener más información sobre los mapas de mensajes y el END_MESSAGE_MAP (macro), consulte [de mensajes y asignación de temas](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="on_command"></a>  ON_COMMAND

Esta macro asigna un mensaje de comando a una función miembro.

### <a name="syntax"></a>Sintaxis

```
ON_COMMAND( id, memberFxn )
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
Identificador del comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

### <a name="remarks"></a>Comentarios

Indica qué función va a controlar un mensaje de comando de un objeto de interfaz de usuario de comando como un botón de barra de herramientas o elemento de menú.

Cuando un objeto de destino del comando recibe un mensaje WM_COMMAND de Windows con el identificador especificado, ON_COMMAND llamará a la función miembro `memberFxn` para controlar el mensaje.

Utilice ON_COMMAND para asignar un único comando a una función miembro. Use [ON_COMMAND_RANGE](#on_command_range) para asignar un intervalo de identificadores de comando a la función miembro de uno. Sólo una entrada de mapa de mensajes puede coincidir con un identificador de comando especificado. Es decir, no se puede asignar un comando a más de un controlador. Para obtener más información y ejemplos, vea [de mensajes y asignación de temas](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Ejemplo

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_command_ex"></a>  ON_COMMAND_EX

Extiende la función miembro de controlador de comandos.

### <a name="syntax"></a>Sintaxis

```
ON_COMMAND_EX(id, memberFxn);
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
Identificador del comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

### <a name="remarks"></a>Comentarios

Un formulario extendido de controladores de mensajes de comando está disponible para los usos avanzados. La macro ON_COMMAND_EX se usa para dichos controladores de mensajes y proporciona un superconjunto de la funcionalidad [ON_COMMAND] (#on_command).  Las funciones miembro de controlador de comandos extendido toman un único parámetro, un tipo UINT que contiene el identificador de comando y devuelven un valor booleano. El valor devuelto debe ser TRUE para

Esta macro asigna un mensaje de comando a una función miembro extendido de controlador de comandos.

### <a name="syntax"></a>Sintaxis

```
ON_COMMAND_EX(id,  memberFxn);
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
Identificador del comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

### <a name="remarks"></a>Comentarios

Un formulario extendido de controladores de mensajes de comando está disponible para los usos avanzados. La macro ON_COMMAND_EX se usa para dichos controladores de mensajes y proporciona un superconjunto de la [ON_COMMAND](message-map-macros-mfc.md#on_command) funcionalidad. Las funciones miembro de controlador de comandos extendido toman un único parámetro, un tipo UINT que contiene el identificador de comando y devuelven un valor booleano. El valor devuelto debe ser TRUE para indicar que el comando se ha controlado; enrutamiento en caso contrario, continuará a otros objetos de destino del comando.
Para obtener más información, vea la nota técnica [TN006: mapas de mensajes] tm006-message-maps.md).

### <a name="requirements"></a>Requisitos

Archivo de encabezado: afxmsg_.h

### <a name="see-also"></a>Vea también

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006: Mapas de mensajes](../tn006-message-maps.md)

## <a name="on_control"></a>  ON_CONTROL

Indica qué función va a controlar un mensaje de notificación de control personalizado.

### <a name="syntax"></a>Sintaxis

```
ON_CONTROL( wNotifyCode, id, memberFxn )
```

### <a name="parameters"></a>Parámetros

*wNotifyCode*<br/>
El código de notificación del control.

*identificador*<br/>
Identificador del comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el comando.

### <a name="remarks"></a>Comentarios

Mensajes de notificación de control son aquellos enviados desde un control a su ventana primaria.

Debe haber exactamente una instrucción de macro ON_CONTROL en el mapa de mensajes para cada mensaje de notificación de control que se debe asignar a una función de controlador de mensajes.

Para obtener más información y ejemplos, vea [de mensajes y asignación de temas](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_message"></a>  ON_MESSAGE

Indica qué función va a controlar un mensaje definido por el usuario.

### <a name="syntax"></a>Sintaxis

```
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parámetros

*message*<br/>
El id. del mensaje.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el mensaje.

El tipo de la función debe ser `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.

### <a name="remarks"></a>Comentarios

Mensajes definidos por el usuario son los mensajes que no son mensajes WM_MESSAGE Windows estándar. Al seleccionar un identificador de mensaje, debe usar valores dentro del intervalo de WM_USER (0 x 0400) a 0x7FFF o WM_APP (0 x 8000) para 0xBFFF. Para obtener más información sobre identificadores de mensaje, consulte [WM_APP](/windows/desktop/winmsg/wm-app).

Debe haber exactamente una instrucción de macro ON_MESSAGE en el mapa de mensajes para cada mensaje definido por el usuario que debe asignarse a una función de controlador de mensajes.

> [!NOTE]
>  Además de los mensajes definidos por el usuario, ON_MESSAGE controla los mensajes de Windows menos comunes. Para obtener más información, consulte [mapas de mensajes](../../mfc/tn006-message-maps.md).

Para obtener más información y ejemplos, vea [de mensajes y asignación de temas](../../mfc/message-handling-and-mapping.md) y [controladores definidos por el usuario](user-defined-handlers.md)

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

## <a name="on_olecmd"></a>  ON_OLECMD

Enruta los comandos a través de la interfaz de envío de comandos `IOleCommandTarget`.

### <a name="syntax"></a>Sintaxis

```
ON_OLECMD( pguid, olecmdid, id )
```

### <a name="parameters"></a>Parámetros

*pguid*<br/>
Identificador del grupo de comandos al que pertenece el comando. Utilice NULL para el grupo estándar.

*olecmdid*<br/>
El identificador del comando OLE.

*identificador*<br/>
El identificador de menú, Id. de la barra de herramientas, identificador de botón u otro Id. del recurso o el comando de objeto.

### <a name="remarks"></a>Comentarios

`IOleCommandTarget` permite que un contenedor recibir comandos que se originan en la interfaz de usuario de DocObject y permite al contenedor enviar los mismos comandos (como nuevo, abrir, guardar como e imprimir en el menú archivo; y copiar, pegar, deshacer, y así sucesivamente en el menú Editar) para DocObject.

`IOleCommandTarget` es más sencillo que de OLE Automation `IDispatch`. `IOleCommandTarget` se basa completamente en un conjunto estándar de comandos que rara vez tienen argumentos, y no está implicada ninguna información de tipo (seguridad de tipos se reduce para los argumentos de comando). Si es necesario enviar comandos con argumentos, use [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

El `IOleCommandTarget` comandos de menú estándar se han implementado por MFC en las macros siguientes:

**(DE ON_OLECMD_CLEARSELECTION)**

Envía el comando Editar Clear. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**(DE ON_OLECMD_COPY)**

Envía el comando Editar una copia. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**(DE ON_OLECMD_CUT)**

Envía el comando Editar Cortar. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**(DE ON_OLECMD_NEW)**

Envía el comando nuevo archivo. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**(DE ON_OLECMD_OPEN)**

Envía el comando Abrir archivo. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**(DE ON_OLECMD_PAGESETUP)**

Envía el comando Configurar página de archivo. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**(DE ON_OLECMD_PASTE)**

Envía el comando Pegar del menú. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**(DE ON_OLECMD_PASTESPECIAL)**

Envía el comando Editar Pegado especial. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**(DE ON_OLECMD_PRINT)**

Envía el comando Imprimir del archivo. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**(DE ON_OLECMD_PRINTPREVIEW)**

Envía el comando Vista previa de impresión de archivos. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**(DE ON_OLECMD_REDO)**

Envía el comando Editar de puesta al día. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**(DE ON_OLECMD_SAVE)**

Envía el comando Guardar archivo. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**(DE ON_OLECMD_SAVE_AS)**

Envía el comando Guardar como. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**(DE ON_OLECMD_SAVE_COPY_AS)**

Envía el comando Guardar copia como. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**(DE ON_OLECMD_SELECTALL)**

Envía el comando Editar Seleccionar todo. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**(DE ON_OLECMD_UNDO)**

Envía el comando Editar deshacer. Se implementa como:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Requisitos

**Encabezado:** afxdocob.h

### <a name="see-also"></a>Vea también

[COleCmdUI (clase)](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)

## <a name="on_registered_message"></a>  ON_REGISTERED_MESSAGE

El Windows `RegisterWindowMessage` función se utiliza para definir un nuevo mensaje de ventana que se garantiza que sea único en todo el sistema.

### <a name="syntax"></a>Sintaxis

```
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parámetros

*nMessageVariable*<br/>
La variable de identificador de mensaje de ventana registrada.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el mensaje.

### <a name="remarks"></a>Comentarios

Esta macro indica qué función va a controlar el mensaje registrado.

Para obtener más información y ejemplos, vea [de mensajes y asignación de temas](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Ejemplo

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

### <a name="see-also"></a>Vea también

[RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947)<br/>
[Controladores definidos por el usuario](user-defined-handlers.md)

## <a name="on_registered_thread_message"></a>  ON_REGISTERED_THREAD_MESSAGE

Indica qué función va a controlar el mensaje registrado por la función RegisterWindowMessage de Windows.

### <a name="syntax"></a>Sintaxis

```
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parámetros

*nMessageVariable*<br/>
La variable de identificador de mensaje de ventana registrada.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes CWinThread al que está asignado el mensaje.

### <a name="remarks"></a>Comentarios

RegisterWindowMessage se usa para definir un nuevo mensaje de ventana que se garantiza que sea único en todo el sistema. ON_REGISTERED_THREAD_MESSAGE debe usarse en lugar de ON_REGISTERED_MESSAGE cuando haya una CWinThread (clase).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_thread_message"></a>  ON_THREAD_MESSAGE

Indica qué función va a controlar un mensaje definido por el usuario.

### <a name="syntax"></a>Sintaxis

```
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parámetros

*message*<br/>
El id. del mensaje.

*memberFxn*<br/>
El nombre de la `CWinThread`-message-función de controlador a la que se asigna el mensaje.

### <a name="remarks"></a>Comentarios

ON_THREAD_MESSAGE debe usarse en lugar de ON_MESSAGE cuando tenga un `CWinThread` clase. Mensajes definidos por el usuario son los mensajes que no son mensajes WM_MESSAGE Windows estándar. Debe haber exactamente una instrucción de macro ON_THREAD_MESSAGE en el mapa de mensajes para cada mensaje definido por el usuario que debe asignarse a una función de controlador de mensajes.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="on_update_command_ui"></a>  ON_UPDATE_COMMAND_UI

Esta macro indica qué función va a controlar un mensaje de comando de actualización de interfaz de usuario.

### <a name="syntax"></a>Sintaxis

```
ON_UPDATE_COMMAND_UI( id, memberFxn )
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
El id. del mensaje.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asigna el mensaje.

### <a name="remarks"></a>Comentarios

Debe haber exactamente una instrucción de macro ON_UPDATE_COMMAND_UI en el mapa de mensajes para cada comando de actualización de la interfaz de usuario que debe asignarse a una función de controlador de mensajes.

Para obtener más información y ejemplos, vea [de mensajes y asignación de temas](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

### <a name="see-also"></a>Vea también

[CCmdUI (clase)](ccmdui-class.md)

## <a name="on_command_range"></a>  ON_COMMAND_RANGE

Use esta macro para asignar un intervalo contiguo de identificadores de comando a una función de controlador de mensaje único.

### <a name="syntax"></a>Sintaxis

```
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parámetros

*Id1*<br/>
Identificador de comando al principio de un intervalo contiguo de identificadores de comando.

*Id2*<br/>
Identificador de comando al final de un intervalo contiguo de identificadores de comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asignan los comandos.

### <a name="remarks"></a>Comentarios

Comienza el intervalo de identificadores con *id1* y termina con *id2*.

Utilice ON_COMMAND_RANGE para asignar un intervalo de identificadores de comando a la función miembro de uno. Use [ON_COMMAND](#on_command) para asignar un único comando a una función miembro. Sólo una entrada de mapa de mensajes puede coincidir con un identificador de comando especificado. Es decir, no se puede asignar un comando a más de un controlador. Para obtener más información sobre los intervalos de mensaje de asignación, consulte [controladores para intervalos de mapa de mensajes de](../../mfc/handlers-for-message-map-ranges.md).

No hay ninguna compatibilidad automática de intervalos de mapa de mensajes, por lo que debe colocar la macro.

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

## <a name="on_update_command_ui_range"></a>  ON_UPDATE_COMMAND_UI_RANGE

Asigna un intervalo contiguo de identificadores de comando a una función de controlador de mensaje de actualización individual.

### <a name="syntax"></a>Sintaxis

```
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parámetros

*Id1*<br/>
Identificador de comando al principio de un intervalo contiguo de identificadores de comando.

*Id2*<br/>
Identificador de comando al final de un intervalo contiguo de identificadores de comando.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes de actualización al que se asignan los comandos.

### <a name="remarks"></a>Comentarios

Controladores de mensajes de actualización de actualización el estado de los elementos de menú y los botones de barra de herramientas asociados con el comando. Comienza el intervalo de identificadores con *id1* y termina con *id2*.

No hay ninguna compatibilidad automática de intervalos de mapa de mensajes, por lo que debe colocar la macro.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h

## <a name="on_control_range"></a>  ON_CONTROL_RANGE

Use esta macro para asignar un intervalo contiguo de identificadores de control a una función de controlador de mensaje único para un mensaje de notificación de Windows especificado, como BN_CLICKED.

### <a name="syntax"></a>Sintaxis

```
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Parámetros

*wNotifyCode*<br/>
El código de notificación a la que el controlador está respondiendo.

*Id1*<br/>
Identificador de comando al principio de un intervalo contiguo de identificadores de control.

*Id2*<br/>
Identificador de comando al final de un intervalo contiguo de identificadores de control.

*memberFxn*<br/>
El nombre de la función de controlador de mensajes a la que se asignan los controles.

### <a name="remarks"></a>Comentarios

Comienza el intervalo de identificadores con *id1* y termina con *id2*. Se llama al controlador para la notificación especificada procedentes de cualquiera de los controles asignados.

No hay ninguna compatibilidad automática de intervalos de mapa de mensajes, por lo que debe colocar la macro.

Para obtener más información sobre cómo implementar funciones de controlador para un intervalo de identificadores de control, consulte [controladores para intervalos de mapa de mensajes de](../../mfc/handlers-for-message-map-ranges.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmsg_.h
