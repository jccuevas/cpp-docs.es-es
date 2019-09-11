---
title: Interfaz ICommandUI
ms.date: 09/07/2019
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
ms.openlocfilehash: a7bb3ab5ed292cef8108e937e67bc9e2ccc1ebce
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907884"
---
# <a name="icommandui-interface"></a>Interfaz ICommandUI

Administra los comandos de la interfaz de usuario.

## <a name="syntax"></a>Sintaxis

```
interface class ICommandUI
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[icommandui__Check](#check)|Establece el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado.|
|[ICommandUI::ContinueRouting](#continuerouting)|Indica al mecanismo de enrutamiento de comandos que continúe enrutando el mensaje actual hacia la cadena de controladores.|
|[ICommandUI::Enabled](#enabled)|Habilita o deshabilita el elemento de la interfaz de usuario para este comando.|
|[ICommandUI::ID](#id)|Obtiene el identificador del objeto de interfaz de usuario representado por `ICommandUI` el objeto.|
|[ICommandUI::Index](#index)|Obtiene el índice del objeto de la interfaz de usuario representado `ICommandUI` por el objeto.|
|[ICommandUI::Radio](#radio)|Establece el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado.|
|[ICommandUI::Text](#text)|Establece el texto del elemento de la interfaz de usuario para este comando.|

## <a name="remarks"></a>Comentarios

Esta interfaz proporciona métodos y propiedades que administran los comandos de la interfaz de usuario. `ICommandUI`es similar a la [clase CCmdUI](../../mfc/reference/ccmdui-class.md), excepto `ICommandUI` que se utiliza para las aplicaciones MFC que interoperan con los componentes .net.

`ICommandUI`se usa dentro de un controlador ON_UPDATE_COMMAND_UI en una clase derivada de [ICommandTarget](../../mfc/reference/icommandtarget-interface.md). Cuando un usuario de una aplicación se activa (selecciona o hace clic en) un menú, cada elemento de menú se muestra como habilitado o deshabilitado. El destino de cada comando de menú proporciona esta información implementando un controlador ON_UPDATE_COMMAND_UI. Para cada uno de los objetos de interfaz de usuario de comandos de la aplicación, use el [Asistente para clases](mfc-class-wizard.md) para crear una entrada de mapa de mensajes y un prototipo de función para cada controlador.

Para obtener más información sobre cómo `ICommandUI` se usa la interfaz en el enrutamiento de [comandos, consulte How to: Agregue el enrutamiento de comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)Windows Forms.

Para obtener más información sobre el uso de Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Para obtener más información sobre cómo se administran los comandos de la interfaz de usuario en MFC, vea [CCmdUI (clase](../../mfc/reference/ccmdui-class.md)).

## <a name="check"></a> ICommandUI::Check

Establece el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado.
```
property UICheckState Check;
```

## <a name="remarks"></a>Comentarios

Esta propiedad establece el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado. Establezca la comprobación en los valores siguientes:
- 0 desactive
- 1 comprobación
- 2 establecer indeterminados

## <a name="continuerouting"></a>ICommandUI::ContinueRouting

Indica al mecanismo de enrutamiento de comandos que continúe enrutando el mensaje actual hacia la cadena de controladores.
```
void ContinueRouting();
```

## <a name="remarks"></a>Comentarios

Se trata de una función miembro avanzada que se debe usar junto con un controlador ON_COMMAND_EX que devuelve FALSE. Para obtener más información, vea la nota técnica TN006: Mapas de mensajes.

## <a name="enabled"></a> ICommandUI::Enabled

Habilita o deshabilita el elemento de la interfaz de usuario para este comando.
```
property bool Enabled;
```

## <a name="remarks"></a>Comentarios

Esta propiedad habilita o deshabilita el elemento de la interfaz de usuario para este comando. Establezca habilitado en TRUE para habilitar el elemento y FALSE para deshabilitarlo.

## <a name="id"></a>ICommandUI:: ID

Obtiene el identificador del objeto de interfaz de usuario representado por el objeto ICommandUI.
```
property unsigned int ID;
```

## <a name="remarks"></a>Comentarios

Esta propiedad obtiene el identificador (un identificador) del elemento de menú, el botón de la barra de herramientas u otro objeto de interfaz de usuario representado por el objeto ICommandUI.

## <a name="index"></a>ICommandUI:: index

Obtiene el índice del objeto de la interfaz de usuario representado por el objeto ICommandUI.
```
property unsigned int Index;
```

## <a name="remarks"></a>Comentarios

Esta propiedad obtiene el índice (un identificador) del elemento de menú, el botón de la barra de herramientas u otro objeto de interfaz de usuario representado por el objeto ICommandUI.

## <a name="radio"></a>ICommandUI:: Radio

Establece el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado.
```
property bool Radio;
```

## <a name="remarks"></a>Comentarios

Esta propiedad establece el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado. Establezca radio en TRUE para habilitar el elemento; en caso contrario, FALSE.

## <a name="text"></a> ICommandUI::Text

Establece el texto del elemento de la interfaz de usuario para este comando.
```
property String^ Text;
```

## <a name="remarks"></a>Comentarios

Esta propiedad establece el texto del elemento de la interfaz de usuario para este comando. Establezca el texto en un identificador de cadena de texto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms. h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)

## <a name="see-also"></a>Vea también

[CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)
