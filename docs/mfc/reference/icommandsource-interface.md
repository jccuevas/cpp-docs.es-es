---
title: ICommandSource (interfaz) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4908566a80fcad2350023f2306a952b2d97b2e62
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060681"
---
# <a name="icommandsource-interface"></a>ICommandSource (interfaz)

Administra los comandos enviados desde un objeto de origen de comando a un control de usuario.

## <a name="syntax"></a>Sintaxis

```
interface class ICommandSource
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Agrega un controlador de comandos a un objeto de origen del comando.|
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Agrega un grupo de controladores de comandos a un objeto de origen del comando.|
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Agrega un grupo de controladores de mensajes de comando de interfaz de usuario a un objeto de origen del comando.|
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Agrega un controlador de mensajes de comando de interfaz de usuario a un objeto de origen del comando.|
|[ICommandSource::PostCommand](#postcommand)|Envía un mensaje sin esperar a que se procese.|
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Quita un controlador de comandos de un objeto de origen del comando.|
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Quita un grupo de controladores de comandos de un objeto de origen del comando.|
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Quita un grupo de controladores de mensajes de comando de interfaz de usuario de un objeto de origen del comando.|
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Quita un controlador de mensajes de comando de interfaz de usuario de un objeto de origen del comando.|
|[ICommandSource::SendCommand](#sendcommand)|Envía un mensaje y espera a que se procese antes de devolver.|

### <a name="remarks"></a>Comentarios

Al hospedar un control de usuario en una vista de MFC, [CWinFormsView (clase)](../../mfc/reference/cwinformsview-class.md) comandos de rutas y actualización de comandos mensajes de interfaz de usuario para el control de usuario para que pueda controlar los comandos MFC (por ejemplo, los elementos de menú del marco y botones de barra de herramientas). Implementando [ICommandTarget (interfaz)](../../mfc/reference/icommandtarget-interface.md), asigne el control de usuario de una referencia a la `ICommandSource` objeto.

Consulte [Cómo: agregar el enrutamiento de comandos para el Control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar `ICommandTarget`.

Para obtener más información sobre el uso de Windows Forms, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)

## <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

Agrega un controlador de comandos a un objeto de origen del comando.
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
Identificador del comando.
*cmdHandler*<br/>
Un identificador para el método de controlador de comandos.

### <a name="remarks"></a>Comentarios

Este método agrega el cmdHandler del controlador de comando al objeto de origen de comando y el controlador asigna a cmdID.
Consulte [Cómo: agregar el enrutamiento de comandos para el Control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar AddCommandHandler.

## <a name="addcommandrangehandler"></a> ICommandSource::AddCommandRangeHandler

Agrega un grupo de controladores de comandos a un objeto de origen del comando.
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
El índice inicial del intervalo de Id. de comando.
*cmdIDMax*<br/>
El índice final del intervalo de Id. de comando.
*cmdHandler*<br/>
Un identificador para el método de controlador de mensaje a la que se asignan los comandos.
### <a name="remarks"></a>Comentarios

Este método asigna un intervalo contiguo de identificadores de comando a un controlador de mensajes único y lo agrega al objeto de origen de comando. Esto se usa para administrar un grupo de botones relacionados con un método.

## <a name="addcommandrangeuihandler"></a> ICommandSource::AddCommandRangeUIHandler

Agrega un grupo de controladores de mensajes de comando de interfaz de usuario a un objeto de origen del comando.
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
El índice inicial del intervalo de Id. de comando.
*cmdIDMax*<br/>
El índice final del intervalo de Id. de comando.
*cmdHandler*<br/>
Un identificador para el método de controlador de mensaje a la que se asignan los comandos.

### <a name="remarks"></a>Comentarios

Este método asigna un intervalo contiguo de identificadores de comando a un controlador de mensajes de comando de interfaz de usuario único y lo agrega al objeto de origen de comando. Esto se usa para administrar un grupo de botones relacionados con un método.

## <a name="addcommanduihandler"></a> ICommandSource::AddCommandUIHandler

Agrega un controlador de mensajes de comando de interfaz de usuario a un objeto de origen del comando.
```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
Identificador del comando.
*cmdUIHandler*<br/>
Un identificador para el método de controlador de mensaje de comando de usuario interfaz.

### <a name="remarks"></a>Comentarios

Este método agrega el cmdHandler de controlador de mensaje de comando de usuario interfaz al objeto de origen de comando y el controlador asigna a cmdID.

## <a name="postcommand"></a> ICommandSource::PostCommand

Envía un mensaje sin esperar a que se procese.
```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parámetros

*command*<br/>
El identificador de comando del mensaje que se publicará.
### <a name="remarks"></a>Comentarios

Este método de forma asincrónica envía el mensaje asignado al identificador especificado por el comando. Se llama a CWnd::PostMessage para colocar el mensaje en cola de mensajes de la ventana y, a continuación, se devuelve sin esperar a la ventana correspondiente procesar el mensaje.

## <a name="removecommandhandler"></a> ICommandSource::RemoveCommandHandler

Quita un controlador de comandos de un objeto de origen del comando.
```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
Identificador del comando.
### <a name="remarks"></a>Comentarios

Este método quita el controlador de comando asignado al cmdID desde el objeto de origen del comando.

## <a name="removecommandrangecommandhandler"></a> ICommandSource::RemoveCommandRangeHandler

Quita un grupo de controladores de comandos de un objeto de origen del comando.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
El índice inicial del intervalo de Id. de comando.
*cmdIDMax*<br/>
El índice final del intervalo de Id. de comando.
### <a name="remarks"></a>Comentarios

Este método quita un grupo de controladores de mensajes, asignado para el especificado de identificadores de comando cmdIDMin y cmdIDMax, desde el objeto de origen del comando.

## <a name="removecommandrangeuihandler"></a> ICommandSource::RemoveCommandRangeUIHandler

Quita un grupo de controladores de mensajes de comando de interfaz de usuario de un objeto de origen del comando.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parámetros

*cmdIDMin*<br/>
El índice inicial del intervalo de Id. de comando.
*cmdIDMax*<br/>
El índice final del intervalo de Id. de comando.
### <a name="remarks"></a>Comentarios

Este método quita un grupo de controladores de mensajes de comando de interfaz usuario, asignado para el especificado de identificadores de comando cmdIDMin y cmdIDMax, desde el objeto de origen del comando.

## <a name="removecommanduihandler"></a> ICommandSource::RemoveCommandUIHandler

Quita un controlador de mensajes de comando de interfaz de usuario de un objeto de origen del comando.
```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
Identificador del comando.
### <a name="remarks"></a>Comentarios

Este método quita el controlador de mensajes de comando de interfaz de usuario asignado al cmdID desde el objeto de origen del comando.

## <a name="sendcommand"></a> ICommandSource::SendCommand

Envía un mensaje y espera a que se procese antes de devolver.
```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parámetros

*command*<br/>
El identificador de comando del que se envíe el mensaje.
### <a name="remarks"></a>Comentarios

Este método envía el mensaje asignado al identificador especificado por el comando de forma sincrónica. Se llama a CWnd:: SendMessage para colocar el mensaje en cola de mensajes de la ventana y espera hasta que dicho procedimiento de ventana ha procesado el mensaje antes de devolver.
## <a name="see-also"></a>Vea también

[Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget (interfaz)](../../mfc/reference/icommandtarget-interface.md)
