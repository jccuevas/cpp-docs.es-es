---
title: Clase COleCmdUI
ms.date: 09/12/2018
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
ms.openlocfilehash: 1b7a6b21a3ad778b4a5ca345b1aaf42875810e4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376266"
---
# <a name="colecmdui-class"></a>Clase COleCmdUI

Implementa un método para que MFC actualice el estado de los objetos relacionados con características de la aplicación orientadas a `IOleCommandTarget`.

## <a name="syntax"></a>Sintaxis

```
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|Construye un objeto `COleCmdUI`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleCmdUI::Habilitar](#enable)|Establece o borra el indicador de comando enable.|
|[COleCmdUI::SetCheck](#setcheck)|Establece el estado de un comando de alternancia de encendido/apagado.|
|[COleCmdUI::SetText](#settext)|Devuelve un nombre de texto o una cadena de estado para un comando.|

## <a name="remarks"></a>Observaciones

En una aplicación que no está habilitada para DocObjects, cuando el usuario ve un menú en la aplicación, MFC procesa UPDATE_COMMAND_UI notificas. Cada notificación recibe un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto que se puede manipular para reflejar el estado de un comando determinado. Sin embargo, cuando la aplicación está habilitada para DocObjects, MFC procesa UPDATE_OLE_COMMAND_UI notificaciones y asigna objetos. `COleCmdUI`

`COleCmdUI`Permite a un DocObject recibir comandos que se originan en la interfaz de usuario de su contenedor (como FileNew, Open, Print, etc.) y permite que un contenedor reciba comandos que se originan en la interfaz de usuario de DocObject. Aunque `IDispatch` se podría usar para `IOleCommandTarget` distribuir los mismos comandos, proporciona una forma más sencilla de consultar y ejecutar porque se basa en un conjunto estándar de comandos, normalmente sin argumentos, y no hay información de tipo implicada. `COleCmdUI`se puede utilizar para habilitar, actualizar y establecer otras propiedades de los comandos de la interfaz de usuario de DocObject. Cuando desee invocar el comando, llame a [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).

Para obtener más información sobre DocObjects, vea [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) y [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdocobj.h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI::COleCmdUI

Construye un `COleCmdUI` objeto asociado a un comando de interfaz de usuario determinado.

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Parámetros

*rgCmds*<br/>
Una lista de comandos admitidos asociados con el GUID especificado. La `OLECMD` estructura asocia comandos con indicadores de comando.

*cCmds*<br/>
El recuento de comandos en *rgCmds*.

*pGroup*<br/>
Puntero a un GUID que identifica un conjunto de comandos.

### <a name="remarks"></a>Observaciones

El `COleCmdUI` objeto proporciona una interfaz de programación para actualizar objetos de interfaz de usuario DocObject, como elementos de menú o botones de barra de control. Los objetos de interfaz de usuario se pueden habilitar, `COleCmdUI` deshabilitar, comprobar y/o borrar a través del objeto.

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI::Habilitar

Llame a esta función para `COleCmdUI` establecer el indicador de comando del objeto en OLECOMDF_ENABLED, que indica a la interfaz que el comando está disponible y habilitado, o para borrar el indicador de comando.

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Parámetros

*Bon*<br/>
Indica si el comando `COleCmdUI` asociado al objeto debe estar habilitado o deshabilitado. Distinto de cero habilita el comando; 0 deshabilita el comando.

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI::SetCheck

Llame a esta función para establecer el estado de un comando de alternancia de encendido/apagado.

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parámetros

*nCheck*<br/>
Valor que determina el estado para establecer un comando de alternancia de encendido/apagado. Los valores son:

|Value|Descripción|
|-----------|-----------------|
|**1**|Establece el comando en on.|
|**2**|Establece el comando en indeterminado; el estado no se puede determinar porque el atributo de este comando está en los estados de encendido y apagado en la selección relevante.|
|cualquier otro valor|Establece el comando en desactivado.|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI::SetText

Llame a esta función para devolver un nombre de texto o una cadena de estado para un comando.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Un puntero al texto que se va a utilizar con el comando.

## <a name="see-also"></a>Consulte también

[CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
