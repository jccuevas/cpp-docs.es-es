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
ms.openlocfilehash: a57ca6f36546a17b9a35ebea875ff01b43de1332
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445712"
---
# <a name="icommandsource-interface"></a>Interfaz ICommandSource

Administra los comandos enviados desde un objeto de origen de comando a un control de usuario.

## <a name="syntax"></a>Sintaxis

```
interface class ICommandSource
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ICommandSource:: AddCommandHandler](#addcommandhandler)|Agrega un controlador de comandos a un objeto de origen de comando.|
|[ICommandSource:: AddCommandRangeHandler](#addcommandrangehandler)|Agrega un grupo de controladores de comandos a un objeto de origen de comando.|
|[ICommandSource:: AddCommandRangeUIHandler](#addcommandrangeuihandler)|Agrega un grupo de controladores de mensajes de comandos de la interfaz de usuario a un objeto de origen de comando.|
|[ICommandSource:: AddCommandUIHandler](#addcommandrangeuihandler)|Agrega un controlador de mensajes de comandos de la interfaz de usuario a un objeto de origen de comando.|
|[ICommandSource::P ostCommand](#postcommand)|Envía un mensaje sin esperar a que se procese.|
|[ICommandSource:: RemoveCommandHandler](#removecommandhandler)|Quita un controlador de comandos de un objeto de origen de comando.|
|[ICommandSource:: RemoveCommandRangeHandler](#removecommandrangehandler)|Quita un grupo de controladores de comandos de un objeto de origen de comando.|
|[ICommandSource:: RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Quita un grupo de controladores de mensajes de comandos de la interfaz de usuario de un objeto de origen de comando.|
|[ICommandSource:: RemoveCommandUIHandler](#removecommandrangeuihandler)|Quita un controlador de mensajes de comando de la interfaz de usuario de un objeto de origen de comando.|
|[ICommandSource:: SendCommand](#sendcommand)|Envía un mensaje y espera a que se procese antes de que se devuelva.|

### <a name="remarks"></a>Observaciones

Al hospedar un control de usuario en una vista MFC, la [clase CWinFormsView](../../mfc/reference/cwinformsview-class.md) enruta comandos y actualizan los mensajes de la interfaz de usuario del comando al control de usuario para que pueda controlar los comandos de MFC (por ejemplo, los elementos de menú de marco y los botones de barra de herramientas). Mediante la implementación de la [interfaz ICommandTarget](../../mfc/reference/icommandtarget-interface.md), se asigna al usuario una referencia al objeto `ICommandSource`.

Vea [Cómo: agregar enrutamiento de comandos al Control Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar `ICommandTarget`.

Para obtener más información sobre el uso de Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms. h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)

## <a name="addcommandhandler"></a>ICommandSource:: AddCommandHandler

Agrega un controlador de comandos a un objeto de origen de comando.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parámetros

*Idcmd*<br/>
Identificador del comando.
*cmdHandler*<br/>
Identificador del método de controlador de comandos.

### <a name="remarks"></a>Observaciones

Este método agrega el controlador de comandos cmdHandler al objeto de origen del comando y asigna el controlador a cmdID.
Vea [Cómo: agregar enrutamiento de comandos al Control Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar AddCommandHandler.

## <a name="addcommandrangehandler"></a>ICommandSource:: AddCommandRangeHandler

Agrega un grupo de controladores de comandos a un objeto de origen de comando.

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
Índice inicial del intervalo de IDENTIFICADOres de comando.
*cmdIDMax*<br/>
Índice final del intervalo de IDENTIFICADOres de comando.
*cmdHandler*<br/>
Identificador del método de control de mensajes al que se asignan los comandos.
### <a name="remarks"></a>Observaciones

Este método asigna un intervalo contiguo de identificadores de comando a un solo controlador de mensajes y lo agrega al objeto de origen del comando. Se utiliza para controlar un grupo de botones relacionados con un método.

## <a name="addcommandrangeuihandler"></a>ICommandSource:: AddCommandRangeUIHandler

Agrega un grupo de controladores de mensajes de comandos de la interfaz de usuario a un objeto de origen de comando.

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
Índice inicial del intervalo de IDENTIFICADOres de comando.
*cmdIDMax*<br/>
Índice final del intervalo de IDENTIFICADOres de comando.
*cmdHandler*<br/>
Identificador del método de control de mensajes al que se asignan los comandos.

### <a name="remarks"></a>Observaciones

Este método asigna un intervalo contiguo de identificadores de comando a un solo controlador de mensajes de comandos de interfaz de usuario y lo agrega al objeto de origen del comando. Se utiliza para controlar un grupo de botones relacionados con un método.

## <a name="addcommanduihandler"></a>ICommandSource:: AddCommandUIHandler

Agrega un controlador de mensajes de comandos de la interfaz de usuario a un objeto de origen de comando.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parámetros

*Idcmd*<br/>
Identificador del comando.
*cmdUIHandler*<br/>
Identificador del método de controlador de mensajes de comandos de la interfaz de usuario.

### <a name="remarks"></a>Observaciones

Este método agrega el controlador de mensajes de comando de la interfaz de usuario cmdHandler al objeto de origen del comando y asigna el controlador a cmdID.

## <a name="postcommand"></a>ICommandSource::P ostCommand

Envía un mensaje sin esperar a que se procese.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parámetros

*command*<br/>
IDENTIFICADOR de comando del mensaje que se va a exponer.
### <a name="remarks"></a>Observaciones

Este método envía de forma asincrónica el mensaje asignado al identificador especificado por el comando. Llama a CWnd::P ostMessage para colocar el mensaje en la cola de mensajes de la ventana y, a continuación, devuelve sin esperar a que la ventana correspondiente procese el mensaje.

## <a name="removecommandhandler"></a>ICommandSource:: RemoveCommandHandler

Quita un controlador de comandos de un objeto de origen de comando.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parámetros

*Idcmd*<br/>
Identificador del comando.
### <a name="remarks"></a>Observaciones

Este método quita el controlador de comandos asignado a cmdID desde el objeto de origen del comando.

## <a name="removecommandrangehandler"></a>ICommandSource:: RemoveCommandRangeHandler

Quita un grupo de controladores de comandos de un objeto de origen de comando.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
Índice inicial del intervalo de IDENTIFICADOres de comando.
*cmdIDMax*<br/>
Índice final del intervalo de IDENTIFICADOres de comando.
### <a name="remarks"></a>Observaciones

Este método quita un grupo de controladores de mensajes asignados a los identificadores de comando especificados por cmdIDMin y cmdIDMax, del objeto de origen del comando.

## <a name="removecommandrangeuihandler"></a>ICommandSource:: RemoveCommandRangeUIHandler

Quita un grupo de controladores de mensajes de comandos de la interfaz de usuario de un objeto de origen de comando.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
Índice inicial del intervalo de IDENTIFICADOres de comando.
*cmdIDMax*<br/>
Índice final del intervalo de IDENTIFICADOres de comando.
### <a name="remarks"></a>Observaciones

Este método quita un grupo de controladores de mensajes de comandos de la interfaz de usuario, asignados a los identificadores de comando especificados por cmdIDMin y cmdIDMax, del objeto de origen del comando.

## <a name="removecommanduihandler"></a>ICommandSource:: RemoveCommandUIHandler

Quita un controlador de mensajes de comando de la interfaz de usuario de un objeto de origen de comando.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parámetros

*Idcmd*<br/>
Identificador del comando.
### <a name="remarks"></a>Observaciones

Este método quita el controlador de mensajes de comando de la interfaz de usuario asignado a cmdID desde el objeto de origen del comando.

## <a name="sendcommand"></a>ICommandSource:: SendCommand

Envía un mensaje y espera a que se procese antes de que se devuelva.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parámetros

*command*<br/>
IDENTIFICADOR de comando del mensaje que se va a enviar.
### <a name="remarks"></a>Observaciones

Este método envía sincrónicamente el mensaje asignado al identificador especificado por el comando. Llama a CWnd:: SendMessage para colocar el mensaje en la cola de mensajes de la ventana y espera hasta que ese procedimiento de ventana haya procesado el mensaje antes de volver.
## <a name="see-also"></a>Consulte también

[Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget (interfaz)](../../mfc/reference/icommandtarget-interface.md)
