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
ms.openlocfilehash: b75509beb7287fad5e51dc9d15fc3e47cacf6854
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751312"
---
# <a name="icommandui-interface"></a>Interfaz ICommandUI

Administra los comandos de la interfaz de usuario.

## <a name="syntax"></a>Sintaxis

```
interface class ICommandUI
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[icommandui__Check](#check)|Establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuado.|
|[ICommandUI::ContinueRouting](#continuerouting)|Indica al mecanismo de enrutamiento de comandos que continúe enrutando el mensaje actual en la cadena de controladores.|
|[ICommandUI::Habilitado](#enabled)|Habilita o deshabilita el elemento de interfaz de usuario para este comando.|
|[ICommandUI::ID](#id)|Obtiene el identificador del objeto de interfaz de usuario representado por el `ICommandUI` objeto.|
|[ICommandUI::Index](#index)|Obtiene el índice del objeto de interfaz de usuario representado por el `ICommandUI` objeto.|
|[ICommandUI::Radio](#radio)|Establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuado.|
|[ICommandUI::Texto](#text)|Establece el texto del elemento de interfaz de usuario para este comando.|

## <a name="remarks"></a>Observaciones

Esta interfaz proporciona métodos y propiedades que administran los comandos de la interfaz de usuario. `ICommandUI`es similar a [CCmdUI (clase),](../../mfc/reference/ccmdui-class.md)excepto que `ICommandUI` se utiliza para aplicaciones MFC que interoperan con componentes .NET.

`ICommandUI`se utiliza dentro de un controlador de ON_UPDATE_COMMAND_UI en una clase derivada [de ICommandTarget.](../../mfc/reference/icommandtarget-interface.md) Cuando un usuario de una aplicación activa (selecciona o hace clic) un menú, cada elemento de menú se muestra como habilitado o deshabilitado. El destino de cada comando de menú proporciona esta información mediante la implementación de un controlador de ON_UPDATE_COMMAND_UI. Para cada uno de los objetos de interfaz de usuario de comando de la aplicación, utilice el [Asistente para](mfc-class-wizard.md) clases para crear una entrada de mapa de mensajes y un prototipo de función para cada controlador.

Para obtener más `ICommandUI` información sobre cómo se usa la interfaz en el enrutamiento de comandos, vea Cómo: Agregar enrutamiento de [comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)de formularios Windows Forms .

Para obtener más información sobre el uso de formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Para obtener más información sobre cómo se administran los comandos de interfaz de usuario en MFC, vea [CCmdUI (Clase)](../../mfc/reference/ccmdui-class.md).

## <a name="icommanduicheck"></a><a name="check"></a>ICommandUI::Check

Establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuado.

```
property UICheckState Check;
```

## <a name="remarks"></a>Observaciones

Esta propiedad establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuado. Establezca Comprobar en los siguientes valores:

- 0 Desmarcar
- 1 Comprobar
- 2 Conjunto indeterminado

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a>ICommandUI::ContinueRouting

Indica al mecanismo de enrutamiento de comandos que continúe enrutando el mensaje actual en la cadena de controladores.

```cpp
void ContinueRouting();
```

## <a name="remarks"></a>Observaciones

Se trata de una función miembro avanzada que se debe usar junto con un controlador de ON_COMMAND_EX que devuelve FALSE. Para obtener más información, consulte Nota técnica TN006: Mapas de mensajes.

## <a name="icommanduienabled"></a><a name="enabled"></a>ICommandUI::Habilitado

Habilita o deshabilita el elemento de interfaz de usuario para este comando.

```
property bool Enabled;
```

## <a name="remarks"></a>Observaciones

Esta propiedad habilita o deshabilita el elemento de interfaz de usuario para este comando. Establezca Habilitado en TRUE para habilitar el elemento, FALSE para deshabilitarlo.

## <a name="icommanduiid"></a><a name="id"></a>ICommandUI::ID

Obtiene el identificador del objeto de interfaz de usuario representado por el ICommandUI objeto.

```
property unsigned int ID;
```

## <a name="remarks"></a>Observaciones

Esta propiedad obtiene el identificador (un identificador) del elemento de menú, botón de barra de herramientas u otro objeto de interfaz de usuario representado por el ICommandUI objeto.

## <a name="icommanduiindex"></a><a name="index"></a>ICommandUI::Index

Obtiene el índice del objeto de interfaz de usuario representado por el ICommandUI objeto.

```
property unsigned int Index;
```

## <a name="remarks"></a>Observaciones

Esta propiedad obtiene el índice (un identificador) del elemento de menú, botón de barra de herramientas u otro objeto de interfaz de usuario representado por el ICommandUI objeto.

## <a name="icommanduiradio"></a><a name="radio"></a>ICommandUI::Radio

Establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuado.

```
property bool Radio;
```

## <a name="remarks"></a>Observaciones

Esta propiedad establece el elemento de interfaz de usuario para este comando en el estado de comprobación adecuado. Establezca Radio en TRUE para habilitar el elemento; de lo contrario FALSO.

## <a name="icommanduitext"></a><a name="text"></a>ICommandUI::Texto

Establece el texto del elemento de interfaz de usuario para este comando.

```
property String^ Text;
```

## <a name="remarks"></a>Observaciones

Esta propiedad establece el texto del elemento de interfaz de usuario para este comando. Establezca Texto en un identificador de cadena de texto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc-lib-mfcmifc80.dll)

## <a name="see-also"></a>Vea también

[CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)
