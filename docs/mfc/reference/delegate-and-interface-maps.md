---
title: Macros de asignación de interfaces y delegados (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 8f48b916f7130551fc8d4da5bb2ebc75d8d728d5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426748"
---
# <a name="delegate-and-interface-map-macros"></a>Macros de mapa de interfaz y delegado

MFC admite estas macros para los mapas de interfaces y delegados:

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Comienza una asignación de delegado.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Comienza la definición del mapa de interfaz interactiva.|
|[Delegado CommandHandler](#commandhandler)|Registra métodos de devolución de llamada con un origen de comando.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Finaliza una asignación de delegado.|
|[END_INTERFACE_MAP](#end_interface_map)|Finaliza el mapa de interfaz en el archivo de implementación. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Crea una entrada en la asignación de delegado.|
|[INTERFACE_PART](#interface_part)|Se utiliza entre la macro BEGIN_INTERFACE_MAP y la macro END_INTERFACE_MAP para cada interfaz que el objeto admitirá.|
|[MAKE_DELEGATE](#make_delegate)|Adjunta un controlador de eventos a un control administrado.|

## <a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

Comienza una asignación de delegado.

### <a name="syntax"></a>Sintaxis

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Parámetros

*LAS*<br/>
Clase en la que se hospeda el control administrado.

### <a name="remarks"></a>Observaciones

Esta macro marca el principio de una lista de entradas de delegado, que componen una asignación de delegado. Para obtener un ejemplo de cómo se usa esta macro, vea [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr\event.h

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Comienza la definición del mapa de interfaz interactiva cuando se usa en el archivo de implementación.

### <a name="syntax"></a>Sintaxis

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
La clase en la que se debe definir el mapa de interfaz.

*baseClass*<br/>
La clase de la que se deriva la *clase* .

### <a name="remarks"></a>Observaciones

Para cada interfaz que se implementa, hay una o varias llamadas a macros INTERFACE_PART. Para cada agregado que utiliza la clase, hay una INTERFACE_AGGREGATE la invocación de macro.

Para obtener más información sobre los mapas de interfaz, vea la [Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="commandhandler"></a>Delegado CommandHandler

Registra métodos de devolución de llamada con un origen de comando.

### <a name="syntax"></a>Sintaxis

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Parámetros

*Idcmd*<br/>
Identificador del comando.

### <a name="remarks"></a>Observaciones

Este delegado registra los métodos de devolución de llamada con un origen de comando. Cuando se agrega un delegado al objeto de origen del comando, el método de devolución de llamada se convierte en un controlador para los comandos que provienen del origen especificado.

Para obtener más información, vea [Cómo: agregar enrutamiento de comandos al Control Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Para obtener más información sobre el uso de Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms. h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)

##  <a name="commanduihandler"></a>Commanduihandler (

Registra métodos de devolución de llamada con un mensaje de comando de actualización de la interfaz de usuario.

### <a name="syntax"></a>Sintaxis

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Parámetros

*Idcmd*<br/>
Identificador del comando.

*cmdUI*<br/>
IDENTIFICADOR del mensaje de comando.

### <a name="remarks"></a>Observaciones

Este delegado registra los métodos de devolución de llamada con un mensaje de comando de actualización de la interfaz de usuario. `CommandUIHandler` es similar a [CommandHandler](#commandhandler) , salvo que este delegado se usa con comandos de actualización de objetos de interfaz de usuario. Los comandos de actualización de la interfaz de usuario se deben asignar uno a uno con los métodos de control de mensajes.

Para obtener más información sobre el uso de Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms. h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

Finaliza una asignación de delegado.

### <a name="syntax"></a>Sintaxis

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Observaciones

Esta macro marca el final de una lista de entradas de delegado, que componen una asignación de delegado. Para obtener un ejemplo de cómo se usa esta macro, vea [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr\event.h

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

Finaliza el mapa de interfaz en el archivo de implementación.

### <a name="syntax"></a>Sintaxis

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Observaciones

Para obtener más información sobre los mapas de interfaz, vea la [Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Crea una entrada en la asignación de delegado.

### <a name="syntax"></a>Sintaxis

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Parámetros

*MIEMBRO*<br/>
El método de controlador de eventos que se va a adjuntar al control.

*ARG0*<br/>
Primer argumento del método de controlador de eventos administrado, como `Object^`.

*ARG1*<br/>
Segundo argumento del método de controlador de eventos administrado, como `EventArgs^`.

### <a name="remarks"></a>Observaciones

Cada entrada de la asignación de delegado corresponde a un delegado de controlador de eventos administrados creado por [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra cómo utilizar EVENT_DELEGATE_ENTRY para crear una entrada en la asignación de delegado para el controlador de eventos `OnClick`; Vea también el ejemplo de código en MAKE_DELEGATE. Para obtener más información, vea [Cómo: recibir Windows Forms eventos de clases C++ nativas](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr\event.h

##  <a name="interface_part"></a>INTERFACE_PART

Se utiliza entre la macro BEGIN_INTERFACE_MAP y la macro END_INTERFACE_MAP para cada interfaz que el objeto admitirá.

### <a name="syntax"></a>Sintaxis

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
El nombre de la clase que contiene el mapa de interfaz.
*suscripto*<br/>
IID que se va a asignar a la clase incrustada.
*localClass*<br/>
Nombre de la clase local.

### <a name="remarks"></a>Observaciones

Permite asignar un IID a un miembro de la clase indicada por la *clase* y *localClass*.

Para obtener más información sobre los mapas de interfaz, vea la [Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="make_delegate"></a>MAKE_DELEGATE

Adjunta un controlador de eventos a un control administrado.

### <a name="syntax"></a>Sintaxis

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Parámetros

*Delegado*<br/>
Tipo del delegado de controlador de eventos administrado, como [EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True).

*MIEMBRO*<br/>
Nombre del método de controlador de eventos que se va a adjuntar al control.

### <a name="remarks"></a>Observaciones

Esta macro crea un delegado de controlador de eventos administrados de tipo *Delegate* y del *miembro*Name. El delegado de controlador de eventos administrados permite que una clase nativa controle los eventos administrados.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra cómo llamar a `MAKE_DELEGATE` para adjuntar un controlador de eventos `OnClick` a un `MyControl`de control MFC. Para obtener una explicación más amplia de cómo funciona esta macro en una aplicación MFC, vea [Cómo: recibir Windows Forms eventos de clases C++ nativas](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr\event.h

## <a name="see-also"></a>Consulte también

[Cómo: Recibir eventos de Windows Forms de clases nativas de C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Macros y variables globales](mfc-macros-and-globals.md)<br/>
