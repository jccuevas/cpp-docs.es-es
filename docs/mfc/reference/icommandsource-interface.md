---
title: Interfaz ICommandSource
ms.date: 03/27/2019
f1_keywords:
- ICommandSource
- AFXWINFORMS/ICommandSource
- AFXWINFORMS/ICommandSource::AddCommandHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::AddCommandUIHandler
- AFXWINFORMS/ICommandSource::PostCommand
- AFXWINFORMS/ICommandSource::RemoveCommandHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::RemoveCommandUIHandler
- AFXWINFORMS/ICommandSource::SendCommand
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
ms.openlocfilehash: 6a03c46c972f7746f39a3c5c65ca9b5509983d59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356986"
---
# <a name="icommandsource-interface"></a>Interfaz ICommandSource

Administra los comandos enviados desde un objeto de origen de comandos a un control de usuario.

## <a name="syntax"></a>Sintaxis

```cpp
interface class ICommandSource
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Agrega un controlador de comandos a un objeto de origen de comandos.|
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Agrega un grupo de controladores de comandos a un objeto de origen de comandos.|
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Agrega un grupo de controladores de mensajes de comandos de interfaz de usuario a un objeto de origen de comandos.|
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Agrega un controlador de mensajes de comando de interfaz de usuario a un objeto de origen de comandos.|
|[ICommandSource::PostCommand](#postcommand)|Publica un mensaje sin esperar a que se procese.|
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Quita un controlador de comandos de un objeto de origen de comandos.|
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Quita un grupo de controladores de comandos de un objeto de origen de comandos.|
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Quita un grupo de controladores de mensajes de comandos de interfaz de usuario de un objeto de origen de comandos.|
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Quita un controlador de mensajes de comando de interfaz de usuario de un objeto de origen de comandos.|
|[ICommandSource::SendCommand](#sendcommand)|Envía un mensaje y espera a que se procese antes de devolverlo.|

### <a name="remarks"></a>Observaciones

Al hospedar un control de usuario en una vista MFC, [CWinFormsView clase](../../mfc/reference/cwinformsview-class.md) enruta comandos y actualizar mensajes de interfaz de usuario de comandos al control de usuario para permitirle controlar comandos MFC (por ejemplo, elementos de menú de marco y botones de barra de herramientas). Mediante la implementación de [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md), `ICommandSource` se proporciona al control de usuario una referencia al objeto.

Consulte Cómo: Agregar enrutamiento de [comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) de `ICommandTarget`formularios Windows Forms para obtener un ejemplo de cómo usar .

Para obtener más información sobre el uso de formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc-lib-mfcmifc80.dll)

## <a name="icommandsourceaddcommandhandler"></a><a name="addcommandhandler"></a>ICommandSource::AddCommandHandler

Agrega un controlador de comandos a un objeto de origen de comandos.

```cpp
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parámetros

*Cmdid*<br/>
Identificador del comando.
*cmdHandler*<br/>
Identificador del método del controlador de comandos.

### <a name="remarks"></a>Observaciones

Este método agrega el controlador de comandos cmdHandler al objeto de origen de comandos y asigna el controlador a cmdID.
Consulte Cómo: Agregar enrutamiento de [comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) de formularios Windows Forms para obtener un ejemplo de cómo usar AddCommandHandler.

## <a name="icommandsourceaddcommandrangehandler"></a><a name="addcommandrangehandler"></a>ICommandSource::AddCommandRangeHandler

Agrega un grupo de controladores de comandos a un objeto de origen de comandos.

```cpp
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
El índice inicial del intervalo de ID de comando.
*cmdIDMax*<br/>
El índice final del intervalo de ID de comando.
*cmdHandler*<br/>
Identificador del método de controlador de mensajes al que se asignan los comandos.

### <a name="remarks"></a>Observaciones

Este método asigna un intervalo contiguo de identificadores de comando a un único controlador de mensajes y lo agrega al objeto de origen de comandos. Esto se utiliza para controlar un grupo de botones relacionados con un método.

## <a name="icommandsourceaddcommandrangeuihandler"></a><a name="addcommandrangeuihandler"></a>ICommandSource::AddCommandRangeUIHandler

Agrega un grupo de controladores de mensajes de comandos de interfaz de usuario a un objeto de origen de comandos.

```cpp
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
El índice inicial del intervalo de ID de comando.
*cmdIDMax*<br/>
El índice final del intervalo de ID de comando.
*cmdHandler*<br/>
Identificador del método de controlador de mensajes al que se asignan los comandos.

### <a name="remarks"></a>Observaciones

Este método asigna un intervalo contiguo de identificadores de comando a un único controlador de mensajes de comando de interfaz de usuario y lo agrega al objeto de origen de comandos. Esto se utiliza para controlar un grupo de botones relacionados con un método.

## <a name="icommandsourceaddcommanduihandler"></a><a name="addcommanduihandler"></a>ICommandSource::AddCommandUIHandler

Agrega un controlador de mensajes de comando de interfaz de usuario a un objeto de origen de comandos.

```cpp
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parámetros

*Cmdid*<br/>
Identificador del comando.
*cmdUIHandler*<br/>
Identificador del método de controlador de mensajes de comandos de la interfaz de usuario.

### <a name="remarks"></a>Observaciones

Este método agrega el controlador de mensajes de comando de interfaz de usuario cmdHandler al objeto de origen de comandos y asigna el controlador a cmdID.

## <a name="icommandsourcepostcommand"></a><a name="postcommand"></a>ICommandSource::PostCommand

Publica un mensaje sin esperar a que se procese.

```cpp
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parámetros

*Comando*<br/>
El identificador de comando del mensaje que se va a publicar.

### <a name="remarks"></a>Observaciones

Este método publica de forma asincrónica el mensaje asignado al identificador especificado por el comando. Llama a CWnd::PostMessage para colocar el mensaje en la cola de mensajes de la ventana y, a continuación, devuelve sin esperar a que la ventana correspondiente procese el mensaje.

## <a name="icommandsourceremovecommandhandler"></a><a name="removecommandhandler"></a>ICommandSource::RemoveCommandHandler

Quita un controlador de comandos de un objeto de origen de comandos.

```cpp
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parámetros

*Cmdid*<br/>
Identificador del comando.

### <a name="remarks"></a>Observaciones

Este método quita el controlador de comandos asignado a cmdID desde el objeto de origen del comando.

## <a name="icommandsourceremovecommandrangehandler"></a><a name="removecommandrangehandler"></a>ICommandSource::RemoveCommandRangeHandler

Quita un grupo de controladores de comandos de un objeto de origen de comandos.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
El índice inicial del intervalo de ID de comando.
*cmdIDMax*<br/>
El índice final del intervalo de ID de comando.

### <a name="remarks"></a>Observaciones

Este método quita un grupo de controladores de mensajes, asignados a los identificadores de comando especificados por cmdIDMin y cmdIDMax, del objeto de origen de comando.

## <a name="icommandsourceremovecommandrangeuihandler"></a><a name="removecommandrangeuihandler"></a>ICommandSource::RemoveCommandRangeUIHandler

Quita un grupo de controladores de mensajes de comandos de interfaz de usuario de un objeto de origen de comandos.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
El índice inicial del intervalo de ID de comando.
*cmdIDMax*<br/>
El índice final del intervalo de ID de comando.

### <a name="remarks"></a>Observaciones

Este método quita un grupo de controladores de mensajes de comandos de interfaz de usuario, asignados a los identificadores de comando especificados por cmdIDMin y cmdIDMax, del objeto de origen de comandos.

## <a name="icommandsourceremovecommanduihandler"></a><a name="removecommanduihandler"></a>ICommandSource::RemoveCommandUIHandler

Quita un controlador de mensajes de comando de interfaz de usuario de un objeto de origen de comandos.

```cpp
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parámetros

*Cmdid*<br/>
Identificador del comando.

### <a name="remarks"></a>Observaciones

Este método quita el controlador de mensajes de comando de interfaz de usuario asignado a cmdID desde el objeto de origen del comando.

## <a name="icommandsourcesendcommand"></a><a name="sendcommand"></a>ICommandSource::SendCommand

Envía un mensaje y espera a que se procese antes de devolverlo.

```cpp
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parámetros

*Comando*<br/>
El identificador de comando del mensaje que se va a enviar.

### <a name="remarks"></a>Observaciones

Este método envía sincrónicamente el mensaje asignado al identificador especificado por el comando. Llama a CWnd::SendMessage para colocar el mensaje en la cola de mensajes de la ventana y espera hasta que el procedimiento de ventana haya procesado el mensaje antes de devolverlo.

## <a name="see-also"></a>Consulte también

[Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Interfaz ICommandTarget](../../mfc/reference/icommandtarget-interface.md)
