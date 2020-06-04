---
title: Macros de mapa de delegado e interfaz (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: e08597d024f5e3a74dcf47363ad3de0aa60cf6c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365835"
---
# <a name="delegate-and-interface-map-macros"></a>Macros de mapa de interfaz y delegado

MFC admite estas macros para asignaciones de delegados e interfaces:

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Comienza un mapa delegado.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Comienza la definición del mapa interconectado.|
|[Delegado CommandHandler](#commandhandler)|Registra los métodos de devolución de llamada con un origen de comandos.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Finaliza un mapa delegado.|
|[END_INTERFACE_MAP](#end_interface_map)|Finaliza el mapa de interfaz en el archivo de implementación. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Crea una entrada en el mapa delegado.|
|[INTERFACE_PART](#interface_part)|Se utiliza entre la macro BEGIN_INTERFACE_MAP y la macro END_INTERFACE_MAP para cada interfaz que admitirá el objeto.|
|[MAKE_DELEGATE](#make_delegate)|Asocia un controlador de eventos a un control administrado.|

## <a name="begin_delegate_map"></a><a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

Comienza un mapa delegado.

### <a name="syntax"></a>Sintaxis

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
La clase en la que se hospeda el control administrado.

### <a name="remarks"></a>Observaciones

Esta macro marca el principio de una lista de entradas de delegado, que componen un mapa delegado. Para obtener un ejemplo de cómo se utiliza esta macro, consulte [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr-event.h

## <a name="begin_interface_map"></a><a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Comienza la definición del mapa interinterfaz cuando se utiliza en el archivo de implementación.

### <a name="syntax"></a>Sintaxis

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase en la que se debe definir el mapa de interfaz.

*baseClass*<br/>
La clase de la que deriva *theClass.*

### <a name="remarks"></a>Observaciones

Para cada interfaz que se implementa, hay una o más invocaciones de macros INTERFACE_PART. Para cada agregado que utiliza la clase, hay una INTERFACE_AGGREGATE invocación de macro.

Para obtener más información sobre los mapas de interfaz, consulte [la Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="commandhandler-delegate"></a><a name="commandhandler"></a>Delegado CommandHandler

Registra los métodos de devolución de llamada con un origen de comandos.

### <a name="syntax"></a>Sintaxis

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Parámetros

*Cmdid*<br/>
Identificador del comando.

### <a name="remarks"></a>Observaciones

Este delegado registra los métodos de devolución de llamada con un origen de comandos. Cuando se agrega un delegado al objeto de origen de comandos, el método de devolución de llamada se convierte en un controlador para los comandos procedentes del origen especificado.

Para obtener más información, vea Cómo: Agregar enrutamiento de [comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)de formularios Windows Forms .

Para obtener más información sobre el uso de formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc-lib-mfcmifc80.dll)

## <a name="commanduihandler"></a><a name="commanduihandler"></a>CommandUIHandler

Registra los métodos de devolución de llamada con un mensaje de comando de actualización de la interfaz de usuario.

### <a name="syntax"></a>Sintaxis

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Parámetros

*Cmdid*<br/>
Identificador del comando.

*cmdUI*<br/>
El identificador del mensaje de comando.

### <a name="remarks"></a>Observaciones

Este delegado registra los métodos de devolución de llamada con un mensaje de comando de actualización de la interfaz de usuario. `CommandUIHandler`es similar a [CommandHandler,](#commandhandler) excepto que este delegado se utiliza con los comandos de actualización de objetos de interfaz de usuario. Los comandos de actualización de la interfaz de usuario se deben asignar uno a uno con métodos de controlador de mensajes.

Para obtener más información sobre el uso de formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc-lib-mfcmifc80.dll)

## <a name="end_delegate_map"></a><a name="end_delegate_map"></a>END_DELEGATE_MAP

Finaliza un mapa delegado.

### <a name="syntax"></a>Sintaxis

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Observaciones

Esta macro marca el final de una lista de entradas de delegado, que componen un mapa delegado. Para obtener un ejemplo de cómo se utiliza esta macro, consulte [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr-event.h

## <a name="end_interface_map"></a><a name="end_interface_map"></a>END_INTERFACE_MAP

Finaliza el mapa de interfaz en el archivo de implementación.

### <a name="syntax"></a>Sintaxis

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de los mapas de interfaz, consulte [la Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="event_delegate_entry"></a><a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Crea una entrada en el mapa delegado.

### <a name="syntax"></a>Sintaxis

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Parámetros

*Miembro*<br/>
El método de controlador de eventos que se va a asociar al control.

*ARG0*<br/>
El primer argumento del método de `Object^`controlador de eventos administrados, como .

*ARG1*<br/>
El segundo argumento del método de `EventArgs^`controlador de eventos administrados, como .

### <a name="remarks"></a>Observaciones

Cada entrada del mapa delegado corresponde a un delegado de controlador de eventos administrado creado por [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra cómo utilizar `OnClick` EVENT_DELEGATE_ENTRY para crear una entrada en el mapa delegado para el controlador de eventos; también vea el ejemplo de código en MAKE_DELEGATE. Para obtener más información, vea [Cómo: sumider eventos de formularios Windows Forms desde clases C++ nativas](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr-event.h

## <a name="interface_part"></a><a name="interface_part"></a>INTERFACE_PART

Se utiliza entre la macro BEGIN_INTERFACE_MAP y la macro END_INTERFACE_MAP para cada interfaz que admitirá el objeto.

### <a name="syntax"></a>Sintaxis

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
El nombre de la clase que contiene el mapa de interfaz.
*Iid*<br/>
El IID que se va a asignar a la clase incrustada.
*localClass*<br/>
El nombre de la clase local.

### <a name="remarks"></a>Observaciones

Permite asignar un IID a un miembro de la clase indicada por *theClass* y *localClass*.

Para obtener más información sobre los mapas de interfaz, consulte [la Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="make_delegate"></a><a name="make_delegate"></a>MAKE_DELEGATE

Asocia un controlador de eventos a un control administrado.

### <a name="syntax"></a>Sintaxis

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Parámetros

*Delegado*<br/>
El tipo del delegado del controlador de eventos administrados, como [EventHandler](/dotnet/api/system.eventhandler).

*Miembro*<br/>
El nombre del método de controlador de eventos que se va a asociar al control.

### <a name="remarks"></a>Observaciones

Esta macro crea un delegado de controlador de eventos administrado de tipo *DELEGATE* y del nombre *MEMBER*. El delegado del controlador de eventos administrados permite que una clase nativa controle los eventos administrados.

### <a name="example"></a>Ejemplo

En el ejemplo de `MAKE_DELEGATE` código siguiente `OnClick` se muestra cómo `MyControl`llamar a adjuntar un controlador de eventos a un control MFC . Para obtener una explicación más detallada de cómo funciona esta macro en una aplicación MFC, vea [Cómo: sumido eventos de formularios Windows Forms desde clases nativas de C++.](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr-event.h

## <a name="see-also"></a>Consulte también

[Cómo: Recibir eventos de Windows Forms de clases nativas de C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Macros y variables globales](mfc-macros-and-globals.md)<br/>
