---
title: Delegado y Macros de mapa de interfaz (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 8f48b916f7130551fc8d4da5bb2ebc75d8d728d5
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850208"
---
# <a name="delegate-and-interface-map-macros"></a>Delegar y macros de mapa de interfaz

MFC admite estas macros de mapas de interfaz y de delegado:

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Comienza una asignación de delegado.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Inicia la definición de la asignación interfaced.|
|[CommandHandler (delegado)](#commandhandler)|Registra los métodos de devolución de llamada con un origen de comando.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Finaliza un mapa de delegado.|
|[END_INTERFACE_MAP](#end_interface_map)|Finaliza el mapa de interfaz en el archivo de implementación. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Crea una entrada en el mapa del delegado.|
|[INTERFACE_PART](#interface_part)|Se utiliza entre el begin_interface_map (macro) y la end_interface_map (macro) para cada interfaz será compatible con el objeto.|
|[MAKE_DELEGATE](#make_delegate)|Asocia un controlador de eventos a un control administrado.|

## <a name="begin_delegate_map"></a> BEGIN_DELEGATE_MAP

Comienza una asignación de delegado.

### <a name="syntax"></a>Sintaxis

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Parámetros

*CLASE*<br/>
La clase en el que se hospeda el control administrado.

### <a name="remarks"></a>Comentarios

Esta macro marca el principio de una lista de entradas de delegado, que componen un mapa de delegado. Para obtener un ejemplo de cómo se usa esta macro, consulte [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr\event.h

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Inicia la definición de la asignación interfaced cuando se utiliza en el archivo de implementación.

### <a name="syntax"></a>Sintaxis

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
La clase en la que se debe definir el mapa de interfaz.

*baseClass*<br/>
La clase de la cual *theClass* deriva.

### <a name="remarks"></a>Comentarios

Para cada interfaz que se implementa, hay uno o más llamadas de macro INTERFACE_PART. Para cada agregado que utiliza la clase, hay una llamada de macro INTERFACE_AGGREGATE.

Para obtener más información sobre los mapas de interfaz, vea [Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="commandhandler"></a>CommandHandler (delegado)

Registra los métodos de devolución de llamada con un origen de comando.

### <a name="syntax"></a>Sintaxis

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
Identificador del comando.

### <a name="remarks"></a>Comentarios

Este delegado registra los métodos de devolución de llamada con un origen de comando. Cuando se agrega un delegado para el objeto de origen del comando, el método de devolución de llamada se convierte en un controlador para los comandos procedentes del origen especificado.

Para obtener más información, vea [Cómo: Agregar comando enrutamiento a la Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Para obtener más información sobre el uso de Windows Forms, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)

##  <a name="commanduihandler"></a>CommandUIHandler

Registra los métodos de devolución de llamada con un mensaje de comando de actualización de interfaz de usuario.

### <a name="syntax"></a>Sintaxis

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Parámetros

*cmdID*<br/>
Identificador del comando.

*cmdUI*<br/>
El identificador de mensaje de comando.

### <a name="remarks"></a>Comentarios

Este delegado registra los métodos de devolución de llamada con un mensaje de comando de actualización de interfaz de usuario. `CommandUIHandler` es similar a [CommandHandler](#commandhandler) , salvo que este delegado se usa con los comandos de actualización de objeto de interfaz de usuario. Comandos de actualización de interfaz de usuario deben asignarse uno a uno con los métodos de controlador de mensaje.

Para obtener más información sobre el uso de Windows Forms, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

Finaliza un mapa de delegado.

### <a name="syntax"></a>Sintaxis

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Comentarios

Esta macro marca el final de una lista de entradas de delegado, que componen un mapa de delegado. Para obtener un ejemplo de cómo se usa esta macro, consulte [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr\event.h

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

Finaliza el mapa de interfaz en el archivo de implementación.

### <a name="syntax"></a>Sintaxis

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de los mapas de interfaz, vea [Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Crea una entrada en el mapa del delegado.

### <a name="syntax"></a>Sintaxis

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Parámetros

*MIEMBRO*<br/>
El método de controlador de eventos que se adjuntará al control.

*ARG0*<br/>
El primer argumento del método de controlador de eventos administrados, como `Object^`.

*ARG1*<br/>
El segundo argumento del método de controlador de eventos administrados, como `EventArgs^`.

### <a name="remarks"></a>Comentarios

Cada entrada en el mapa de delegado corresponde a un delegado de controlador de eventos administrados creado por [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente muestra cómo usar EVENT_DELEGATE_ENTRY para crear una entrada en el mapa de delegado para el `OnClick` controlador de eventos; vea el ejemplo de código en MAKE_DELEGATE también. Para obtener más información, vea [Cómo: Receptor de eventos de Windows Forms de clases nativas de C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Requisitos

**Encabezado:** msclr\event.h

##  <a name="interface_part"></a>INTERFACE_PART

Se utiliza entre el begin_interface_map (macro) y la end_interface_map (macro) para cada interfaz será compatible con el objeto.

### <a name="syntax"></a>Sintaxis

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
El nombre de la clase que contiene el mapa de interfaz.
*iid*<br/>
IID que va a asignarse a la clase incrustada.
*localClass*<br/>
El nombre de la clase local.

### <a name="remarks"></a>Comentarios

Permite asignar un IID a un miembro de la clase indicada por *theClass* y *localClass*.

Para obtener más información sobre los mapas de interfaz, vea [Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="make_delegate"></a>MAKE_DELEGATE

Asocia un controlador de eventos a un control administrado.

### <a name="syntax"></a>Sintaxis

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Parámetros

*DELEGATE*<br/>
Delegar el tipo del controlador de eventos administrados, como [EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True).

*MIEMBRO*<br/>
Nombre del método de controlador de eventos que se adjuntará al control.

### <a name="remarks"></a>Comentarios

Esta macro crea un delegado de controlador de eventos administrado del tipo *delegar* y del nombre *miembro*. El delegado de controlador de eventos administrado permite que una clase nativa controlar los eventos administrados.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra cómo llamar a `MAKE_DELEGATE` para adjuntar un `OnClick` controlador de eventos para un control MFC `MyControl`. Para obtener una explicación más amplia de cómo funciona esta macro en una aplicación MFC, vea [Cómo: Receptor de eventos de Windows Forms de clases nativas de C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

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

## <a name="see-also"></a>Vea también

[Cómo: Recibir eventos de Windows Forms de clases nativas de C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
