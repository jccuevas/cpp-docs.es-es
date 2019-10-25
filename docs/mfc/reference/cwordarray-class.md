---
title: Clase CWordArray
ms.date: 09/07/2019
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
ms.openlocfilehash: c136bbb14e0d7cffc604813731b6f87ba18063cf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907912"
---
# <a name="cwordarray-class"></a>Clase CWordArray

Admite matrices de palabras de 16 bits.

## <a name="syntax"></a>Sintaxis

```
class CWordArray : public CObject
```

## <a name="members"></a>Miembros

Las funciones miembro de `CWordArray` son similares a las funciones miembro de la [cobarra](../../mfc/reference/cobarray-class.md)de clases. Debido a esta similitud, puede utilizar la documentación de referencia de `CObArray` para obtener información específica de la función miembro. Siempre que vea un puntero [CObject](../../mfc/reference/cobject-class.md) como un parámetro de función o un valor devuelto, sustituya una palabra.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

por ejemplo, se traduce en

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Construye una matriz vacía.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Anexa otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libera toda la memoria no usada por encima del límite superior actual.|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Devuelve el valor en un índice dado.|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtiene el número de elementos de esta matriz.|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Permite el acceso a los elementos de la matriz. Puede ser NULL.|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Obtiene el número de elementos de esta matriz.|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Devuelve el índice válido de mayor tamaño.|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Determina si la matriz está vacía.|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Quita todos los elementos de esta matriz.|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Quita un elemento en un índice específico.|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Establece el número de elementos que contendrá esta matriz.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CObArray::operator &#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Establece u obtiene el elemento en el índice especificado.|

## <a name="remarks"></a>Comentarios

`CWordArray`incorpora la macro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) para admitir la serialización y el volcado de sus elementos. Si una matriz de palabras se almacena en un archivo, ya sea con un operador de inserción sobrecargado o con la función miembro [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) , cada elemento se serializa, a su vez,.

> [!NOTE]
>  Antes de usar una matriz, use `SetSize` para establecer su tamaño y asignarle memoria. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.

Si necesita un volcado de elementos individuales en la matriz, debe establecer la profundidad del contexto de volcado en 1 o más.

Para obtener más información sobre `CWordArray`el uso de, vea las [colecciones](../../mfc/collections.md)de artículos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll. h

##  <a name="icommandsource_interface"></a>Interfaz ICommandSource

Administra los comandos enviados desde un objeto de origen de comando a un control de usuario.

```
interface class ICommandSource
```

### <a name="remarks"></a>Comentarios

Al hospedar un control de usuario en una vista MFC, la [clase CWinFormsView](../../mfc/reference/cwinformsview-class.md) enruta comandos y actualizan los mensajes de la interfaz de usuario del comando al control de usuario para que pueda controlar los comandos de MFC (por ejemplo, los elementos de menú de marco y los botones de barra de herramientas). Al implementar, se proporciona al usuario una referencia al `ICommandSource` objeto.

Vea [Cómo: Agregue el enrutamiento de comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Windows Forms para obtener un ejemplo de cómo `ICommandTarget`usar.

Para obtener más información sobre el uso de Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

Agrega un controlador de comandos a un objeto de origen de comando.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
Identificador del comando.

*cmdHandler*<br/>
Identificador del método de controlador de comandos.

### <a name="remarks"></a>Comentarios

Este método agrega el controlador de comandos *cmdHandler* al objeto de origen del comando y asigna el controlador a *CmdID*.

Vea [Cómo: Agregue el enrutamiento de comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Windows Forms para obtener un ejemplo de cómo `AddCommandHandler`usar.

##  <a name="addcommandrangehandler"></a>  ICommandSource::AddCommandRangeHandler

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

### <a name="remarks"></a>Comentarios

Este método asigna un intervalo contiguo de identificadores de comando a un solo controlador de mensajes y lo agrega al objeto de origen del comando. Se utiliza para controlar un grupo de botones relacionados con un método.

##  <a name="addcommandrangeuihandler"></a>  ICommandSource::AddCommandRangeUIHandler

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

### <a name="remarks"></a>Comentarios

Este método asigna un intervalo contiguo de identificadores de comando a un solo controlador de mensajes de comandos de interfaz de usuario y lo agrega al objeto de origen del comando. Se utiliza para controlar un grupo de botones relacionados con un método.

##  <a name="addcommanduihandler"></a>  ICommandSource::AddCommandUIHandler

Agrega un controlador de mensajes de comandos de la interfaz de usuario a un objeto de origen de comando.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
Identificador del comando.

*cmdUIHandler*<br/>
Identificador del método de controlador de mensajes de comandos de la interfaz de usuario.

### <a name="remarks"></a>Comentarios

Este método agrega el controlador de mensajes de comando de la interfaz de usuario *cmdHandler* al objeto de origen del comando y asigna el controlador a *CmdID*.

##  <a name="postcommand"></a>  ICommandSource::PostCommand

Envía un mensaje sin esperar a que se procese.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parámetros

*command*<br/>
IDENTIFICADOR de comando del mensaje que se va a exponer.

### <a name="remarks"></a>Comentarios

Este método envía de forma asincrónica el mensaje asignado al identificador especificado por el *comando*. Llama a [CWnd::P ostmessage](../../mfc/reference/cwnd-class.md#postmessage) para colocar el mensaje en la cola de mensajes de la ventana y, a continuación, devuelve sin esperar a que la ventana correspondiente procese el mensaje.

##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler

Quita un controlador de comandos de un objeto de origen de comando.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
Identificador del comando.

### <a name="remarks"></a>Comentarios

Este método quita el controlador de comandos asignado a *CmdID* desde el objeto de origen del comando.

##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler

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

### <a name="remarks"></a>Comentarios

Este método quita un grupo de controladores de mensajes asignados a los identificadores de comando especificados por *cmdIDMin* y *cmdIDMax*, del objeto de origen del comando.

##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler

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

### <a name="remarks"></a>Comentarios

Este método quita un grupo de controladores de mensajes de comandos de la interfaz de usuario, asignados a los identificadores de comando especificados por *cmdIDMin* y *cmdIDMax*, del objeto de origen del comando.

##  <a name="removecommanduihandler"></a>  ICommandSource::RemoveCommandUIHandler

Quita un controlador de mensajes de comando de la interfaz de usuario de un objeto de origen de comando.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
Identificador del comando.

### <a name="remarks"></a>Comentarios

Este método quita el controlador de mensajes de comando de la interfaz de usuario asignado a *CmdID* desde el objeto de origen del comando.

##  <a name="sendcommand"></a>  ICommandSource::SendCommand

Envía un mensaje y espera a que se procese antes de que se devuelva.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parámetros

*command*<br/>
IDENTIFICADOR de comando del mensaje que se va a enviar.

### <a name="remarks"></a>Comentarios

Este método envía sincrónicamente el mensaje asignado al identificador especificado por el *comando*. Llama a [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) para colocar el mensaje en la cola de mensajes de la ventana y espera hasta que ese procedimiento de ventana haya procesado el mensaje antes de volver.

##  <a name="icommandtarget_interface"></a>Interfaz ICommandTarget

Proporciona un control de usuario con una interfaz para recibir comandos de un objeto de origen de comando.

```
interface class ICommandTarget
```

### <a name="remarks"></a>Comentarios

Al hospedar un control de usuario en una vista MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) enruta comandos y actualiza los mensajes de la interfaz de usuario del comando al control de usuario para que pueda controlar los comandos de MFC (por ejemplo, los elementos de menú de marco y los botones de barra de herramientas). Al implementar `ICommandTarget`, se proporciona al usuario una referencia al objeto.

Vea [Cómo: Agregue el enrutamiento de comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Windows Forms para obtener un ejemplo de cómo `ICommandTarget`usar.

Para obtener más información sobre el uso de Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="initialize"></a>ICommandTarget:: Initialize

Inicializa el objeto de destino del comando.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parámetros

*cmdSource*<br/>
Identificador del objeto de origen del comando.

### <a name="remarks"></a>Comentarios

Al hospedar un control de usuario en una vista MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) enruta comandos y actualiza los mensajes de la interfaz de usuario del comando al control de usuario para que pueda controlar los comandos de MFC.

Este método inicializa el objeto de destino del comando y lo asocia con el objeto de origen de comando *cmdSource*especificado. Se debe llamar en la implementación de la clase de control de usuario. Durante la inicialización, debe registrar los controladores de comandos con el objeto de origen de comando llamando a [ICommandSource:: AddCommandHandler](../../mfc/reference/icommandsource-interface.md) en la `Initialize` implementación. Vea [Cómo: Agregue el enrutamiento de comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Windows Forms para obtener un ejemplo de cómo `Initialize` usar para ello.

##  <a name="icommandui_interface"></a>Interfaz ICommandUI

Administra los comandos de la interfaz de usuario.

```
interface class ICommandUI
```

### <a name="remarks"></a>Comentarios

Esta interfaz proporciona métodos y propiedades que administran los comandos de la interfaz de usuario. `ICommandUI`es similar a la [clase CCmdUI](../../mfc/reference/ccmdui-class.md), excepto `ICommandUI` que se utiliza para las aplicaciones MFC que interoperan con los componentes .net.

`ICommandUI`se usa dentro de `ON_UPDATE_COMMAND_UI` un controlador en una clase derivada de. Cuando un usuario de una aplicación se activa (selecciona o hace clic en) un menú, cada elemento de menú se muestra como habilitado o deshabilitado. El destino de cada comando de menú proporciona esta información implementando `ON_UPDATE_COMMAND_UI` un controlador. Para cada uno de los objetos de interfaz de usuario de comandos de la aplicación, use el [Asistente para clases](mfc-class-wizard.md) o la ventana **propiedades** (en **vista de clases**) para crear una entrada de mapa de mensajes y un prototipo de función para cada controlador.

Para obtener más información sobre cómo `ICommandUI` se usa la interfaz en el enrutamiento de [comandos, consulte How to: Agregue el enrutamiento de comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)Windows Forms.

Para obtener más información sobre el uso de Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Para obtener más información sobre cómo se administran los comandos de la interfaz de usuario en MFC, vea [CCmdUI (clase](../../mfc/reference/ccmdui-class.md)).

##  <a name="check"></a>  ICommandUI::Check

Establece el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado.

```
property UICheckState Check;
```

### <a name="remarks"></a>Comentarios

Esta propiedad establece el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado. Establezca `Check` en los valores siguientes:

|Término|Definición|
|----------|----------------|
|0|Desactive|
|1|de Azure Functions|
|2|Establecer indeterminados|

##  <a name="continuerouting"></a>  ICommandUI::ContinueRouting

Indica al mecanismo de enrutamiento de comandos que continúe enrutando el mensaje actual hacia la cadena de controladores.

```
void ContinueRouting();
```

### <a name="remarks"></a>Comentarios

Se trata de una función miembro avanzada que se debe usar junto con un controlador [ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex) que devuelve false. Para obtener más información, vea la [Nota técnica TN006: Mapas](../../mfc/tn006-message-maps.md)de mensajes.

##  <a name="enabled"></a>  ICommandUI::Enabled

Habilita o deshabilita el elemento de la interfaz de usuario para este comando.

```
property bool Enabled;
```

### <a name="remarks"></a>Comentarios

Esta propiedad habilita o deshabilita el elemento de la interfaz de usuario para este comando. Establézcalo `Enabled` en true para habilitar el elemento y false para deshabilitarlo.

##  <a name="id"></a>  ICommandUI::ID

Obtiene el identificador del objeto de interfaz de usuario representado por `ICommandUI` el objeto.

```
property unsigned int ID;
```

### <a name="remarks"></a>Comentarios

Esta propiedad obtiene el identificador (un identificador) del elemento de menú, el botón de la barra de herramientas u otro objeto de `ICommandUI` interfaz de usuario representado por el objeto.

##  <a name="index"></a>  ICommandUI::Index

Obtiene el índice del objeto de la interfaz de usuario representado `ICommandUI` por el objeto.

```
property unsigned int Index;
```

### <a name="remarks"></a>Comentarios

Esta propiedad obtiene el índice (un identificador) del elemento de menú, el botón de la barra de herramientas u otro objeto de `ICommandUI` interfaz de usuario representado por el objeto.

##  <a name="radio"></a>  ICommandUI::Radio

Establece el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado.

```
property bool Radio;
```

### <a name="remarks"></a>Comentarios

Esta propiedad establece el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado. Establézcalo `Radio` en true para habilitar el elemento; en caso contrario, false.

##  <a name="text"></a>  ICommandUI::Text

Establece el texto del elemento de la interfaz de usuario para este comando.

```
property String^ Text;
```

### <a name="remarks"></a>Comentarios

Esta propiedad establece el texto del elemento de la interfaz de usuario para este comando. Se `Text` establece en un identificador de cadena de texto.

##  <a name="iview_interface"></a>IView (interfaz)

Implementa varios métodos que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) usa para enviar notificaciones de vista a un control administrado.

```
interface class IView
```

### <a name="remarks"></a>Comentarios

`IView`implementa varios métodos que `CWinFormsView` usa para reenviar las notificaciones de vista comunes a un control administrado hospedado. Son [OnInitialUpdate](../../mfc/reference/iview-interface.md), [ALUpdate](../../mfc/reference/iview-interface.md) y [OnActivateView](../../mfc/reference/iview-interface.md).

`IView`es similar a [CView](../../mfc/reference/cview-class.md), pero solo se usa con vistas y controles administrados.

Para obtener más información sobre el uso de Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="onactivateview"></a>  IView::OnActivateView

Lo llama MFC cuando una vista está activada o desactivada.

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>Parámetros

*activate*<br/>
Indica si la vista se está activando o desactivando.

##  <a name="oninitialupdate"></a>  IView::OnInitialUpdate

Lo llama el marco de trabajo después de adjuntar la vista por primera vez al documento, pero antes de que se muestre inicialmente la vista.

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>  IView::OnUpdate

Lo llama MFC después de modificar el documento de la vista.

```
void OnUpdate();
```

### <a name="remarks"></a>Comentarios

Esta función permite que la vista actualice su presentación para reflejar las modificaciones.

## <a name="see-also"></a>Vea también

[Ejemplo de recopilación de MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
