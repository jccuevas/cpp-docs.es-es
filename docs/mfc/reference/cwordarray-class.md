---
title: Clase CWordArray | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf19865b4c11bb8305bea62b3682faebe39bef74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cwordarray-class"></a>Clase CWordArray
Admite matrices de palabras de 16 bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CWordArray : public CObject  
```  
  
## <a name="members"></a>Miembros  
 Las funciones miembro de `CWordArray` son similares a las funciones miembro de clase [CObArray](../../mfc/reference/cobarray-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CObArray` para obtener información específica de la función miembro. Siempre que vea un [CObject](../../mfc/reference/cobject-class.md) puntero como un parámetro de función o un valor devuelto, sustituir un **WORD**.  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 por ejemplo, se traduce en  
  
 `WORD CWordArray::GetAt( int <nIndex> ) const;`  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Construye una matriz vacía.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Anexa otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|  
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libera toda la memoria no usada por encima del límite superior actual.|  
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Devuelve el valor en un índice dado.|  
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtiene el número de elementos de esta matriz.|  
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Permite el acceso a los elementos de la matriz. Puede ser **NULL**.|  
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
  
|Name|Descripción|  
|----------|-----------------|  
|[CObArray::operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Establece u obtiene el elemento en el índice especificado.|  
  
## <a name="remarks"></a>Comentarios  
 `CWordArray` incorpora la [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro para admitir la serialización y el volcado de sus elementos. Si una matriz de palabras se almacena en un archivo, con un operador de inserción sobrecargado o con el [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) función miembro, cada elemento es, a su vez, serializar.  
  
> [!NOTE]
>  Antes de usar una matriz, use `SetSize` para establecer su tamaño y asignarle memoria. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.  
  
 Si se necesita un volcado de los elementos individuales de la matriz, debe establecer la profundidad del contexto de volcado en 1 o mayor.  
  
 Para obtener más información sobre el uso de `CWordArray`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CWordArray`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcoll.h  
  
##  <a name="icommandsource_interface"></a>  Interfaz ICommandSource  
 Administra los comandos enviados de un objeto de origen de comando a un control de usuario.  
  
```  
interface class ICommandSource  
```  
  
### <a name="remarks"></a>Comentarios  
 Al hospedar un control de usuario en una vista de MFC, [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md) comandos de rutas y actualización de comandos mensajes de interfaz de usuario para el control de usuario para que pueda controlar los comandos MFC (por ejemplo, elementos de menú de marco y botones de barra de herramientas). Cuando se implementan, asigne el control de usuario una referencia a la `ICommandSource` objeto.  
  
 Vea [Cómo: agregar el enrutamiento de comandos para el Control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar `ICommandTarget`.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler  
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
 Este método agrega el controlador de comandos `cmdHandler` para el objeto de origen de comando y el controlador que se asigna `cmdID`.  
  
 Vea [Cómo: agregar el enrutamiento de comandos para el Control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar `AddCommandHandler`.  
  
##  <a name="addcommandrangehandler"></a>  ICommandSource::AddCommandRangeHandler  
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
 Un identificador para el método de controlador de mensaje a la que se asignan los comandos.  
  
### <a name="remarks"></a>Comentarios  
 Este método asigna un intervalo contiguo de identificadores de comando a un controlador único mensaje y lo agrega al objeto de origen de comando. Esto se usa para administrar un grupo de botones relacionados con un método.  
  
##  <a name="addcommandrangeuihandler"></a>  ICommandSource::AddCommandRangeUIHandler  
 Agrega un grupo de controladores de mensajes de comando de interfaz de usuario a un objeto de origen de comando.  
  
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
 Un identificador para el método de controlador de mensaje a la que se asignan los comandos.  
  
### <a name="remarks"></a>Comentarios  
 Este método asigna un intervalo contiguo de identificadores de comando a un controlador de mensajes de comando de interfaz de usuario único y lo agrega al objeto de origen de comando. Esto se usa para administrar un grupo de botones relacionados con un método.  
  
##  <a name="addcommanduihandler"></a>  ICommandSource::AddCommandUIHandler  
 Agrega un controlador de mensajes de comando de interfaz de usuario a un objeto de origen de comando.  
  
```  
void AddCommandUIHandler(
    unsigned int cmdID,   
    CommandUIHandler^ cmdUIHandler);
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 Identificador del comando.  
  
 `cmdUIHandler`  
 Un identificador para el método de controlador de mensajes de usuario interfaz comando.  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega el controlador de mensajes de comando de interfaz de usuario `cmdHandler` para el objeto de origen de comando y el controlador que se asigna `cmdID`.  
  
##  <a name="postcommand"></a>  ICommandSource::PostCommand  
 Envía un mensaje sin tener que esperar a que se procese.  
  
```  
void PostCommand(unsigned int command);
```  
  
### <a name="parameters"></a>Parámetros  
 `command`  
 El identificador de comando del mensaje que se va a registrar.  
  
### <a name="remarks"></a>Comentarios  
 Este método de forma asincrónica envía el mensaje asignado al identificador especificado por `command`. Llama [CWnd::PostMessage](../../mfc/reference/cwnd-class.md#postmessage) para colocar el mensaje en la ventana de la cola de mensajes y, a continuación, devuelve sin esperar a la ventana correspondiente procesar el mensaje.  
  
##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler  
 Quita un controlador de comandos de un objeto de origen de comando.  
  
```  
void RemoveCommandHandler(unsigned int cmdID);
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 Identificador del comando.  
  
### <a name="remarks"></a>Comentarios  
 Este método quita el controlador de comandos que se asignan a `cmdID` desde el objeto de origen de comando.  
  
##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler  
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
 Este método quita un grupo de controladores de mensajes, asignado a la especificada de identificadores de comando por `cmdIDMin` y `cmdIDMax`, desde el objeto de origen de comando.  
  
##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler  
 Quita un grupo de controladores de mensajes de comando de interfaz de usuario de un objeto de origen de comando.  
  
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
 Este método quita un grupo de controladores de mensajes de comando de interfaz usuario, asignado a la especificada de identificadores de comando por `cmdIDMin` y `cmdIDMax`, desde el objeto de origen de comando.  
  
##  <a name="removecommanduihandler"></a>  ICommandSource::RemoveCommandUIHandler  
 Quita un controlador de mensajes de comando de interfaz de usuario de un objeto de origen de comando.  
  
```  
void RemoveCommandUIHandler(unsigned int cmdID);
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 Identificador del comando.  
  
### <a name="remarks"></a>Comentarios  
 Este método quita el controlador de mensajes de comando de interfaz de usuario asignado a `cmdID` desde el objeto de origen de comando.  
  
##  <a name="sendcommand"></a>  ICommandSource::SendCommand  
 Envía un mensaje y espera a que se procese antes de devolver.  
  
```  
void SendCommand(unsigned int command);
```  
  
### <a name="parameters"></a>Parámetros  
 `command`  
 El identificador de comando del que se envíe el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía de forma sincrónica el mensaje asignado al identificador especificado por `command`. Llama [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) para colocar el mensaje en la ventana de la cola de mensajes y espera hasta que dicho procedimiento de ventana haya procesado el mensaje antes de devolver.  
  
##  <a name="icommandtarget_interface"></a>  Interfaz ICommandTarget  
 Proporciona un control de usuario con una interfaz para recibir comandos de un objeto de origen de comando.  
  
```  
interface class ICommandTarget  
```  
  
### <a name="remarks"></a>Comentarios  
 Al hospedar un control de usuario en una vista de MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) comandos de rutas y actualización de comandos mensajes de interfaz de usuario para el control de usuario para que pueda controlar los comandos MFC (por ejemplo, elementos de menú de marco y botones de barra de herramientas). Implementando `ICommandTarget`, asigne el control de usuario de una referencia al objeto.  
  
 Vea [Cómo: agregar el enrutamiento de comandos para el Control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar `ICommandTarget`.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="initialize"></a>  ICommandTarget:: Initialize  
 Inicializa el objeto de destino del comando.  
  
```  
void Initialize(ICommandSource^ cmdSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdSource`  
 Un identificador para el objeto de origen de comando.  
  
### <a name="remarks"></a>Comentarios  
 Al hospedar un control de usuario en una vista de MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) comandos de rutas y actualización de comandos mensajes de interfaz de usuario para el control de usuario para permitirle controlar comandos MFC.  
  
 Este método inicializa el objeto de destino del comando y lo asocia con el objeto de origen de comando especificado `cmdSource`. Se debe llamar en la implementación de la clase de control de usuario. En la inicialización, debe registrar los controladores de comandos con el objeto de origen de comando mediante una llamada a [ICommandSource::AddCommandHandler](../../mfc/reference/icommandsource-interface.md) en el `Initialize` implementación. Vea [Cómo: agregar el enrutamiento de comandos para el Control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar `Initialize` para ello.  
  
##  <a name="icommandui_interface"></a>  Interfaz ICommandUI  
 Administra los comandos de la interfaz de usuario.  
  
```  
interface class ICommandUI  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta interfaz proporciona métodos y propiedades que administran los comandos de la interfaz de usuario. `ICommandUI` es similar a [CCmdUI (clase)](../../mfc/reference/ccmdui-class.md), salvo que `ICommandUI` se utiliza para aplicaciones MFC que interoperan con los componentes. NET.  
  
 `ICommandUI` se utiliza dentro de un `ON_UPDATE_COMMAND_UI` controlador en una - clase derivada. Cuando un usuario de una aplicación activa (activa o clics) se muestra un menú, cada elemento de menú como habilitado o deshabilitado. El destino de cada comando de menú proporciona esta información mediante la implementación de un `ON_UPDATE_COMMAND_UI` controlador. Para cada uno de los objetos de interfaz de usuario de comandos en la aplicación, utilice la ventana Propiedades para crear una entrada de mapa de mensajes y el prototipo de función para cada controlador.  
  
 Para obtener más información sobre cómo las `ICommandUI` interfaz se utiliza en el enrutamiento de comandos, consulte [Cómo: agregar el enrutamiento de comandos para el Control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Para obtener más información sobre cómo se administran los comandos de la interfaz de usuario en MFC, vea [CCmdUI (clase)](../../mfc/reference/ccmdui-class.md).  
  
##  <a name="check"></a>  ICommandUI::Check  
 Establece el elemento de la interfaz de usuario para este comando en el estado de activación adecuada.  
  
```  
property UICheckState Check;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta propiedad establece el elemento de la interfaz de usuario para este comando en el estado de activación adecuada. Establecer `Check` en los siguientes valores:  
  
|Término|de esquema JSON|  
|----------|----------------|  
|0|Desactive la opción|  
|1|de Azure Functions|  
|2|Conjunto indeterminado|  
  
##  <a name="continuerouting"></a>  ICommandUI::ContinueRouting  
 Indica al mecanismo de enrutamiento de comandos para continuar enrutar el mensaje actual hacia abajo de la cadena de controladores.  
  
```  
void ContinueRouting();
```  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una función miembro avanzado que debe usarse junto con un [ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex) controlador que devuelve `FALSE`. Para obtener más información, vea la nota técnica [TN006: mapas de mensajes](../../mfc/tn006-message-maps.md).  
  
##  <a name="enabled"></a>  ICommandUI::Enabled  
 Habilita o deshabilita el elemento de la interfaz de usuario para este comando.  
  
```  
property bool Enabled;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta propiedad habilita o deshabilita el elemento de la interfaz de usuario para este comando. Establecer `Enabled` a `TRUE` para habilitar el elemento `FALSE` para deshabilitarlo.  
  
##  <a name="id"></a>  ICommandUI::ID  
 Obtiene el identificador de objeto de interfaz de usuario representado por la `ICommandUI` objeto.  
  
```  
property unsigned int ID;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta propiedad obtiene el identificador (un identificador) del elemento de menú, botón de barra de herramientas, o de otro objeto de interfaz de usuario representado por la `ICommandUI` objeto.  
  
##  <a name="index"></a>  ICommandUI::Index  
 Obtiene el índice del objeto de interfaz de usuario representado por la `ICommandUI` objeto.  
  
```  
property unsigned int Index;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta propiedad obtiene el índice (un identificador) del elemento de menú, botón de barra de herramientas, o de otro objeto de interfaz de usuario representado por la `ICommandUI` objeto.  
  
##  <a name="radio"></a>  ICommandUI::Radio  
 Establece el elemento de la interfaz de usuario para este comando en el estado de activación adecuada.  
  
```  
property bool Radio;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta propiedad establece el elemento de la interfaz de usuario para este comando en el estado de activación adecuada. Establecer `Radio` a `TRUE` para habilitar el elemento; en caso contrario, `FALSE`.  
  
##  <a name="text"></a>  ICommandUI::Text  
 Establece el texto del elemento de interfaz de usuario para este comando.  
  
```  
property String^ Text;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta propiedad establece el texto del elemento de interfaz de usuario para este comando. Establecer `Text` a un identificador de cadena de texto.  
  
##  <a name="iview_interface"></a>  Interfaz de IView  
 Implementa varios métodos que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utiliza para enviar notificaciones de vista para un control administrado.  
  
```  
interface class IView  
```  
  
### <a name="remarks"></a>Comentarios  
 `IView` implementa varios métodos que `CWinFormsView` usa para enviar notificaciones de vista comunes para un control hospedado administrado. Se trata de [OnInitialUpdate](../../mfc/reference/iview-interface.md), [OnUpdate](../../mfc/reference/iview-interface.md) y [OnActivateView](../../mfc/reference/iview-interface.md).  
  
 `IView` es similar a [CView](../../mfc/reference/cview-class.md), pero solo se usa con vistas administradas y controles.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="onactivateview"></a>  IView::OnActivateView  
 Llamado por MFC cuando se activa o desactiva una vista.  
  
```  
void OnActivateView(bool activate);
```  
  
### <a name="parameters"></a>Parámetros  
 `activate`  
 Indica si la vista se está activando o desactivando.  
  
##  <a name="oninitialupdate"></a>  IView:: OnInitialUpdate  
 Lo llama el marco de trabajo después de la vista se adjunta al documento en primer lugar, pero antes de la vista se muestra inicialmente.  
  
```  
void OnInitialUpdate();
```  
  
##  <a name="onupdate"></a>  IView::OnUpdate  
 Llamado por MFC cuando se ha modificado el documento de la vista.  
  
```  
void OnUpdate();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función permite que la vista actualice su presentación para reflejar las modificaciones.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



