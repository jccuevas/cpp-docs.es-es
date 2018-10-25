---
title: COleCmdUI (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
dev_langs:
- C++
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb4d71f66add8e0462141acf74342c429eb81379
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071289"
---
# <a name="colecmdui-class"></a>COleCmdUI (clase)

Implementa un método para que MFC actualice el estado de los objetos relacionados con características de la aplicación orientadas a `IOleCommandTarget`.

## <a name="syntax"></a>Sintaxis

```
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|Construye un objeto `COleCmdUI`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleCmdUI::Enable](#enable)|Establece o borra la marca de habilitación de comando.|
|[COleCmdUI::SetCheck](#setcheck)|Establece el estado de un botón de alternancia activar/desactivar comando.|
|[COleCmdUI::SetText](#settext)|Devuelve una cadena de texto de nombre o el estado de un comando.|

## <a name="remarks"></a>Comentarios

En una aplicación que no está habilitada para DocObjects, cuando el usuario vea un menú en la aplicación, MFC procesa notificaciones UPDATE_COMMAND_UI. Cada notificación se proporciona un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto que se puede manipular para reflejar el estado de un comando concreto. Sin embargo, cuando la aplicación está habilitada para DocObjects, MFC procesa las notificaciones de UPDATE_OLE_COMMAND_UI y asigna `COleCmdUI` objetos.

`COleCmdUI` permite DocObject recibir comandos que se originan en la interfaz de usuario de su contenedor (por ejemplo, FileNew, abrir, imprimir y así sucesivamente), y un contenedor recibir comandos que se originan en la interfaz de usuario de DocObject. Aunque `IDispatch` podría usarse para enviar los mismos comandos, `IOleCommandTarget` proporciona una manera más sencilla para consultar y ejecutar porque depende de un conjunto estándar de comandos, por lo general, sin argumentos, y no está implicada ninguna información de tipo. `COleCmdUI` puede utilizarse para habilitar, actualizar y establecer otras propiedades de DocObject comandos de la interfaz de usuario. Cuando desea invocar el comando, llame a [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).

Para obtener más información sobre DocObjects, consulte [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) y [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[Compatibilidad de CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdocobj.h

##  <a name="colecmdui"></a>  COleCmdUI::COleCmdUI

Construye un `COleCmdUI` objeto asociado con un comando de la interfaz de usuario concreta.

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Parámetros

*rgCmds*<br/>
Una lista de comandos admitidos asociado con el GUID especificado. El `OLECMD` estructura asocia los comandos con marcadores de comando.

*cCmds*<br/>
El recuento de comandos de *rgCmds*.

*pGroup*<br/>
Un puntero a un GUID que identifica un conjunto de comandos.

### <a name="remarks"></a>Comentarios

La `COleCmdUI` objeto proporciona una interfaz de programación para actualizar los objetos de interfaz de usuario de DocObject como botones de barra de controles o elementos de menú. Los objetos de interfaz de usuario se pueden habilitados, deshabilitados, activados o desactivados a través de la `COleCmdUI` objeto.

##  <a name="enable"></a>  COleCmdUI::Enable

Llame a esta función para establecer el indicador de comando de la `COleCmdUI` objeto para OLECOMDF_ENABLED, lo que indica la interfaz que el comando está disponible y habilitada, o para borrar el indicador de comando.

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Parámetros

*Ben*<br/>
Indica si el comando asociado a la `COleCmdUI` objeto debe habilitarse o deshabilitarse. Distinto de cero permite que el comando; 0 deshabilita el comando.

##  <a name="setcheck"></a>  COleCmdUI::SetCheck

Llame a esta función para establecer el estado de un botón de alternancia activar/desactivar comando.

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parámetros

*nCompruebe*<br/>
Un valor que determina el estado para establecer un botón de alternancia activar/desactivar comando. Los valores son:

|Valor|Descripción|
|-----------|-----------------|
|**1**|El comando se establece en on.|
|**2**|Establece el comando a indeterminado; no se puede determinar el estado porque el atributo de este comando está en tanto en Estados de la selección pertinente.|
|cualquier otro valor|Establece el comando en off.|

##  <a name="settext"></a>  COleCmdUI::SetText

Llame a esta función para devolver una cadena de texto de nombre o el estado de un comando.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Un puntero al texto que se usará con el comando.

## <a name="see-also"></a>Vea también

[CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

