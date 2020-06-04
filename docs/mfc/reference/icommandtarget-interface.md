---
title: Interfaz ICommandTarget
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: be64f4e0367b9ecc1b24fa96f067f4acd45a9978
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751454"
---
# <a name="icommandtarget-interface"></a>Interfaz ICommandTarget

Proporciona un control de usuario con una interfaz para recibir comandos de un objeto de origen de comandos.

## <a name="syntax"></a>Sintaxis

```
interface class ICommandTarget
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ICommandTarget::Initialize](#initialize)|Inicializa el objeto de destino del comando.|

## <a name="remarks"></a>Observaciones

Al hospedar un control de usuario en una vista MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) enruta comandos y actualizar los mensajes de interfaz de usuario de comandos al control de usuario para permitirle controlar comandos MFC (por ejemplo, elementos de menú de marco y botones de barra de herramientas). Mediante `ICommandTarget`la implementación de , se proporciona al control de usuario una referencia a la [ICommandSource](../../mfc/reference/icommandsource-interface.md) objeto.

Consulte Cómo: Agregar enrutamiento de [comandos al control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) de `ICommandTarget`formularios Windows Forms para obtener un ejemplo de cómo usar .

Para obtener más información sobre el uso de formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc-lib-mfcmifc80.dll)

## <a name="icommandtargetinitialize"></a><a name="initialize"></a>ICommandTarget::Initialize

Inicializa el objeto de destino del comando.

```cpp
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parámetros

*cmdSource*<br/>
Identificador del objeto de origen de comandos.

### <a name="remarks"></a>Observaciones

Cuando se hospeda un control de usuario en una vista MFC, CWinFormsView enruta comandos y actualizar los mensajes de interfaz de usuario de comandos al control de usuario para permitirle controlar los comandos MFC.

Este método inicializa el objeto de destino del comando y lo asocia con el objeto de origen de comando especificado cmdSource. Debe llamarse en la implementación de la clase de control de usuario. En la inicialización, debe registrar controladores de comandos con el objeto de origen de comandos mediante una llamada a ICommandSource::AddCommandHandler en el Initialize implementación. Consulte Cómo: Agregar enrutamiento de comandos al control de formularios Windows Forms para obtener un ejemplo de cómo usar Initialize para hacerlo.

## <a name="see-also"></a>Vea también

[Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Interfaz ICommandSource](../../mfc/reference/icommandsource-interface.md)
