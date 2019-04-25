---
title: ICommandTarget (interfaz)
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: a224b868ea1923bb4f84b0d682c71fadb63da572
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322074"
---
# <a name="icommandtarget-interface"></a>ICommandTarget (interfaz)

Proporciona un control de usuario con una interfaz y recibe comandos desde un objeto de origen del comando.

## <a name="syntax"></a>Sintaxis

```
interface class ICommandTarget
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[ICommandTarget::Initialize](#initialize)|Inicializa el objeto de destino del comando.|

## <a name="remarks"></a>Comentarios

Al hospedar un control de usuario en una vista de MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) comandos de rutas y actualización de comandos mensajes de interfaz de usuario para el control de usuario para que pueda controlar los comandos MFC (por ejemplo, los elementos de menú del marco y botones de barra de herramientas). Implementando `ICommandTarget`, proporciona control de usuario de una referencia a la [ICommandSource](../../mfc/reference/icommandsource-interface.md) objeto.

Vea [Cómo: Agregar el enrutamiento de comandos para el Control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar `ICommandTarget`.

Para obtener más información sobre el uso de Windows Forms, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)

##  <a name="initialize"></a> ICommandTarget::Initialize

Inicializa el objeto de destino del comando.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parámetros

*cmdSource*<br/>
Un identificador al objeto de origen de comando.

### <a name="remarks"></a>Comentarios

Al hospedar un control de usuario en una vista de MFC, CWinFormsView enruta los comandos y mensajes de interfaz de usuario de comandos de actualización para el control de usuario para que pueda controlar los comandos MFC.

Este método inicializa el objeto de destino de comando y lo asocia con el cmdSource de objeto de origen de comando especificado. Se debe llamar en la implementación de clase del control de usuario. Durante la inicialización, debe registrar controladores de comandos con el objeto de origen de comando mediante la llamada ICommandSource::AddCommandHandler en la implementación de Initialize. Vea Cómo: Agregue el enrutamiento de comandos para el Control de Windows Forms para obtener un ejemplo de cómo usar Initialize para hacer esto.

## <a name="see-also"></a>Vea también

[Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource (interfaz)](../../mfc/reference/icommandsource-interface.md)
