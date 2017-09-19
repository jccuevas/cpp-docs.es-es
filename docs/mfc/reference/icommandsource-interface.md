---
title: Interfaz de ICommandSource | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- ICommandSource interface
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f923a8a42327cb74ce9323f72aae90c7411da27c
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="icommandsource-interface"></a>Interfaz de ICommandSource
Administra los comandos enviados desde un objeto de origen de comando a un control de usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
interface class ICommandSource  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Agrega un controlador de comandos a un objeto de origen de comando.|  
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Agrega un grupo de controladores de comandos a un objeto de origen de comando.|  
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Agrega un grupo de controladores de mensajes de comandos de interfaz de usuario a un objeto de origen de comando.|  
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Agrega un controlador de mensajes de comandos de interfaz de usuario a un objeto de origen de comando.|  
|[ICommandSource::PostCommand](#postcommand)|Envía un mensaje sin tener que esperar a que se procese.|  
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Quita un controlador de comandos de un objeto de origen de comando.|  
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Quita un grupo de controladores de comandos de un objeto de origen de comando.|  
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Quita un grupo de controladores de mensajes de comandos de interfaz de usuario de un objeto de origen de comando.|  
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Quita un controlador de mensajes de comandos de interfaz de usuario de un objeto de origen de comando.|  
|[ICommandSource::SendCommand](#sendcommand)|Envía un mensaje y espera a que se procese antes de devolver.|  
  
### <a name="remarks"></a>Comentarios  
 Al hospedar un control de usuario en una vista de MFC, [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md) rutas comandos y actualizar mensajes de interfaz de usuario para el control de usuario para que pueda controlar los comandos MFC (por ejemplo, elementos de menú de marcos y botones de barra de herramientas) del comando. Implementando [ICommandTarget interfaz](../../mfc/reference/icommandtarget-interface.md), asigne el control de usuario de una referencia a la `ICommandSource` objeto.  
  
 Consulte [Cómo: agregar el enrutamiento de comandos para el Control Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar `ICommandTarget`.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)  
  
## <a name="addcommandhandler"></a>ICommandSource::AddCommandHandler
Agrega un controlador de comandos a un objeto de origen de comando.
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parámetros  
`cmdID`  
Identificador del comando.  
`cmdHandler`  
Un identificador para el método de controlador de comandos.

### <a name="remarks"></a>Comentarios
Este método agrega la cmdHandler del controlador de comando para el objeto de origen de comando y el controlador asigna a cmdID.
Consulte [Cómo: agregar el enrutamiento de comandos para el Control Windows Forms](https://msdn.microsoft.com/library/y33d8624.aspx) para obtener un ejemplo de cómo usar AddCommandHandler.

## <a name="addcommandrangehandler"></a>ICommandSource::AddCommandRangeHandler

Agrega un grupo de controladores de comandos a un objeto de origen de comando.
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```
### <a name="parameters"></a>Parámetros  
`cmdIDMin`  
El índice inicial del intervalo de Id. de comando.
`cmdIDMax`  
El índice final del intervalo de Id. de comando.
`cmdHandler`  
Un identificador para el método de controlador de mensajes a los que se asignan los comandos.
### <a name="remarks"></a>Comentarios
Este método asigna un intervalo contiguo de identificadores de comando a un controlador de mensaje y lo agrega al objeto de origen de comando. Se utiliza para administrar un grupo de botones relacionados con un método.

## <a name="addcommandrangeuihandler"></a>ICommandSource::AddCommandRangeUIHandler
Agrega un grupo de controladores de mensajes de comandos de interfaz de usuario a un objeto de origen de comando.
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin, 
    unsigned int cmdIDMax, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Parámetros  
`cmdIDMin`  
El índice inicial del intervalo de Id. de comando.
`cmdIDMax`  
El índice final del intervalo de Id. de comando.
`cmdHandler`  
Un identificador para el método de controlador de mensajes a los que se asignan los comandos.

### <a name="remarks"></a>Comentarios
Este método asigna un intervalo contiguo de identificadores de comando a un controlador de mensajes de comandos de interfaz de usuario único y lo agrega al objeto de origen de comando. Se utiliza para administrar un grupo de botones relacionados con un método.

## <a name="addcommanduihandler"></a>ICommandSource::AddCommandUIHandler
Agrega un controlador de mensajes de comandos de interfaz de usuario a un objeto de origen de comando.
```
void AddCommandUIHandler(
    unsigned int cmdID, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Parámetros
`cmdID`  
Identificador del comando.  
`cmdUIHandler`  
Un identificador para el método de controlador de mensaje de comando de usuario (interfaz).

### <a name="remarks"></a>Comentarios
Este método agrega el cmdHandler de controlador de mensaje de comando de usuario interfaz al objeto de origen de comando y el controlador asigna a cmdID.

## <a name="postcommand"></a>ICommandSource::PostCommand
Envía un mensaje sin tener que esperar a que se procese.
```
void PostCommand(unsigned int command);
```
### <a name="parameters"></a>Parámetros
`command`  
El identificador de comando del mensaje se registre.
### <a name="remarks"></a>Comentarios
Este método de forma asincrónica envía el mensaje asignado al identificador especificado por el comando. Llama a CWnd::PostMessage para colocar el mensaje en cola de mensajes de la ventana y, a continuación, se devuelve sin esperar a la ventana correspondiente procesar el mensaje.


## <a name="removecommandhandler"></a>ICommandSource::RemoveCommandHandler
Quita un controlador de comandos de un objeto de origen de comando.
```
void RemoveCommandHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Parámetros
`cmdID`  
Identificador del comando.
### <a name="remarks"></a>Comentarios
Este método quita el controlador de comandos que se asignan a cmdID desde el objeto de origen de comando.


## <a name="removecommandrangecommandhandler"></a>ICommandSource::RemoveCommandRangeHandler 
Quita un grupo de controladores de comandos de un objeto de origen de comando.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>Parámetros
`cmdIDMin`  
El índice inicial del intervalo de Id. de comando.
`cmdIDMax`  
El índice final del intervalo de Id. de comando.
### <a name="remarks"></a>Comentarios
Este método quita un grupo de controladores de mensajes, asignado al comando identificadores especificado por cmdIDMin y cmdIDMax, desde el objeto de origen de comando.

## <a name="removecommandrangeuihandler"></a>ICommandSource::RemoveCommandRangeUIHandler 
Quita un grupo de controladores de mensajes de comandos de interfaz de usuario de un objeto de origen de comando.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>Parámetros
`cmdIDMin`  
El índice inicial del intervalo de Id. de comando.
`cmdIDMax`  
El índice final del intervalo de Id. de comando.
### <a name="remarks"></a>Comentarios
Este método quita un grupo de controladores de mensajes de comando de interfaz usuario, asignado al comando identificadores especificado por cmdIDMin y cmdIDMax, desde el objeto de origen de comando.

## <a name="removecommanduihandler"></a>ICommandSource::RemoveCommandUIHandler 
Quita un controlador de mensajes de comandos de interfaz de usuario de un objeto de origen de comando.
```
void RemoveCommandUIHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Parámetros
`cmdID`  
Identificador del comando.
### <a name="remarks"></a>Comentarios
Este método quita el controlador de mensajes de comando de interfaz de usuario asignado al cmdID desde el objeto de origen de comando.

## <a name="sendcommand"></a>ICommandSource::SendCommand 
Envía un mensaje y espera a que se procese antes de devolver.
```
void SendCommand(unsigned int command);
```
### <a name="parameters"></a>Parámetros
`command`  
El identificador de comando del que se envíe el mensaje.
### <a name="remarks"></a>Comentarios
Este método envía de forma sincrónica el mensaje asignado al identificador especificado por el comando. Llama a CWnd:: SendMessage para colocar el mensaje en cola de mensajes de la ventana y espera hasta que este procedimiento de ventana ha procesado el mensaje antes de devolver.
## <a name="see-also"></a>Vea también  
 [Cómo: agregar comandos enrutamiento a Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [Interfaz ICommandTarget](../../mfc/reference/icommandtarget-interface.md)

