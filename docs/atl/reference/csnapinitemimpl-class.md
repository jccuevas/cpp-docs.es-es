---
title: Clase CSnapInItemImpl
ms.date: 11/04/2016
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: 1e4f98dabd2d27b21dbe3e197f32e27ccca9d2d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330728"
---
# <a name="csnapinitemimpl-class"></a>Clase CSnapInItemImpl

Esta clase proporciona métodos para implementar un objeto de nodo de complemento.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `CSnapInItemImpl`de .

*bIsExtension*<br/>
TRUESi el objeto es una extensión de complemento; de lo contrario FALSO.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Agrega elementos de menú a un menú contextual.|
|[CSnapInItemImpl::Command](#command)|Llamado por la consola cuando se selecciona un elemento de menú personalizado.|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Agrega páginas a la hoja de propiedades del complemento.|
|[CSnapInItemImpl::FillData](#filldata)|Copia información sobre el objeto de complemento en una secuencia especificada.|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Recupera la `RESULTDATAITEM` estructura del complemento.|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Determina el tipo de vista utilizado por el panel de resultados.|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Recupera la `SCOPEDATAITEM` estructura del complemento.|
|[CSnapInItemImpl::Notify](#notify)|Llamado por la consola para notificar al complemento de las acciones realizadas por el usuario.|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Se llama para ver si el nodo de complemento admite páginas de propiedades.|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Modifica los indicadores de inserción de menú para un objeto de complemento.|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Establece la información del botón de barra de herramientas especificado.|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Actualiza el estado de un elemento de menú contextual.|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Actualiza el estado del botón de barra de herramientas especificado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|El nombre del objeto de complemento.|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|La `RESULTDATAITEM` estructura de `CSnapInItemImpl` Windows utilizada por el objeto.|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|La `SCOPEDATAITEM` estructura de `CSnapInItemImpl` Windows utilizada por el objeto.|

## <a name="remarks"></a>Observaciones

`CSnapInItemImpl`proporciona una implementación básica para un objeto de nodo de complemento, como agregar elementos de menú y barras de herramientas, y reenviar comandos para el nodo de complemento a la función de controlador adecuada. Estas características se implementan mediante varias interfaces y tipos de mapa diferentes. La implementación predeterminada controla las notificaciones enviadas al objeto node determinando la instancia correcta de la clase derivada y, a continuación, reenviando el mensaje a la instancia correcta.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsnap.h

## <a name="csnapinitemimpladdmenuitems"></a><a name="addmenuitems"></a>CSnapInItemImpl::AddMenuItems

Este método implementa la función de Win32 [IExtendContextMenu::AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems).

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parámetros

*piCallback*<br/>
[en] Puntero al `IContextMenuCallback` que puede agregar elementos al menú contextual.

*pInsertionAllowed*<br/>
[adentro, fuera] Identifica los puntos de inserción de elementos de menú definidos por Microsoft Management Console (MMC) que se pueden usar. Esto puede ser una combinación de los siguientes indicadores:

- CCM_INSERTIONALLOWED_TOP Elementos se pueden insertar en la parte superior de un menú contextual.

- CCM_INSERTIONALLOWED_NEW elementos se pueden insertar en el submenú Crear nuevo.

- CCM_INSERTIONALLOWED_TASK Elementos se pueden insertar en el submenú Tarea.

- CCM_INSERTIONALLOWED_VIEW Elementos se pueden insertar en el menú de vista de la barra de herramientas o en el submenú Ver del menú contextual del panel de resultados.

*type*<br/>
[en] Especifica el tipo de objeto. Puede tener uno de los siguientes valores:

- CCT_SCOPE objeto Data para el contexto del panel de ámbito.

- CCT_RESULT objeto Data para el contexto del panel de resultados.

- CCT_SNAPIN_MANAGER Objeto Data para el contexto del gestor de complementos.

- CCT_UNINITIALIZED objeto Data tiene un tipo no válido.

## <a name="csnapinitemimplcommand"></a><a name="command"></a>CSnapInItemImpl::Command

Este método implementa la función de Win32 [IExtendContextMenu::Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command).

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parámetros

*lCommandID*<br/>
[en] Especifica el identificador de comando del elemento de menú.

*type*<br/>
[en] Especifica el tipo de objeto. Puede tener uno de los siguientes valores:

- CCT_SCOPE objeto Data para el contexto del panel de ámbito.

- CCT_RESULT objeto Data para el contexto del panel de resultados.

- CCT_SNAPIN_MANAGER Objeto Data para el contexto del gestor de complementos.

- CCT_UNINITIALIZED objeto Data tiene un tipo no válido.

## <a name="csnapinitemimplcreatepropertypages"></a><a name="createpropertypages"></a>CSnapInItemImpl::CreatePropertyPages

Este método implementa la función de Win32 [IExtendPropertySheet::CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2).

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parámetros

*lpProvider*<br/>
[in] Puntero en la interfaz `IPropertySheetCallback`.

*Manejar*<br/>
[en] Especifica el identificador utilizado para enrutar el mensaje de notificación MMCN_PROPERTY_CHANGE a la clase de datos adecuada.

*Punk*<br/>
[en] Puntero a `IExtendPropertySheet` la interfaz en el objeto que contiene información de contexto sobre el nodo.

*type*<br/>
[en] Especifica el tipo de objeto. Puede tener uno de los siguientes valores:

- CCT_SCOPE objeto Data para el contexto del panel de ámbito.

- CCT_RESULT objeto Data para el contexto del panel de resultados.

- CCT_SNAPIN_MANAGER Objeto Data para el contexto del gestor de complementos.

- CCT_UNINITIALIZED objeto Data tiene un tipo no válido.

## <a name="csnapinitemimplcsnapinitemimpl"></a><a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl

Construye un objeto `CSnapInItemImpl`.

```
CSnapInItemImpl();
```

## <a name="csnapinitemimplfilldata"></a><a name="filldata"></a>CSnapInItemImpl::FillData

Esta función se llama para recuperar información sobre el elemento.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>Parámetros

*Cf*<br/>
[en] El formato (texto, texto enriquecido o texto enriquecido con elementos OLE) del Portapapeles.

*pStream*<br/>
[en] Puntero a la secuencia que contiene los datos del objeto.

### <a name="remarks"></a>Observaciones

Para implementar correctamente esta función, copie la información correcta en la secuencia (*pStream*), en función del formato del Portapapeles indicado por *cf*.

## <a name="csnapinitemimplgetresultviewtype"></a><a name="getresultviewtype"></a>CSnapInItemImpl::GetResultViewType

Llame a esta función para recuperar el tipo de vista para el panel de resultados del objeto de complemento.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>Parámetros

*ppViewType*<br/>
[fuera] Puntero a la dirección del tipo de vista devuelto.

*pViewOptions*<br/>
[fuera] Puntero a la enumeración MMC_VIEW_OPTIONS, que proporciona a la consola las opciones especificadas por el complemento propietario. Este valor puede ser uno de los siguientes:

- MMC_VIEW_OPTIONS_NOLISTVIEWS 0x00000001 Indica a la consola que se abstenga de presentar opciones de vista de lista estándar en el menú **Ver.** Permite que el complemento muestre sus propias vistas personalizadas solo en el panel de vista de resultados. Este es el único indicador de opción definido en este momento.

- MMC_VIEW_OPTIONS_NONE 0 Permite las opciones de vista predeterminadas.

## <a name="csnapinitemimplgetscopepaneinfo"></a><a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo

Llame a esta `SCOPEDATAITEM` función para recuperar la estructura del complemento.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>Parámetros

*pScopeDataItem*<br/>
[fuera] Un puntero `SCOPEDATAITEM` a la `CSnapInItemImpl` estructura del objeto.

## <a name="csnapinitemimplgetresultpaneinfo"></a><a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo

Llame a esta `RESULTDATAITEM` función para recuperar la estructura del complemento.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>Parámetros

*pResultDataItem*<br/>
[fuera] Un puntero `RESULTDATAITEM` a la `CSnapInItemImpl` estructura del objeto.

## <a name="csnapinitemimplm_bstrdisplayname"></a><a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName

Contiene la cadena que se muestra para el elemento de nodo.

```
CComBSTR m_bstrDisplayName;
```

## <a name="csnapinitemimplm_scopedataitem"></a><a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem

Estructura `SCOPEDATAITEM` del objeto de datos de complemento.

```
SCOPEDATAITEM m_scopeDataItem;
```

## <a name="csnapinitemimplm_resultdataitem"></a><a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem

Estructura [RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem) del objeto de datos de complemento.

```
RESULTDATAITEM m_resultDataItem;
```

## <a name="csnapinitemimplnotify"></a><a name="notify"></a>CSnapInItemImpl::Notify

Se llama cuando el usuario actúa sobre el objeto de complemento.

```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```

### <a name="parameters"></a>Parámetros

*event*<br/>
[en] Identifica una acción realizada por un usuario. Las siguientes notificaciones son posibles:

- MMCN_ACTIVATE Se envía cuando se activa y desactiva una ventana.

- MMCN_ADD_IMAGES Enviado para agregar imágenes al panel de resultados.

- MMCN_BTN_CLICK Se envía cuando el usuario hace clic en uno de los botones de la barra de herramientas.

- MMCN_CLICK Se envía cuando un usuario hace clic en un botón del mouse en un elemento de vista de lista.

- MMCN_DBLCLICK Se envía cuando un usuario hace doble clic en un botón del mouse en un elemento de vista de lista.

- MMCN_DELETE Enviado para informar al complemento de que se debe eliminar el objeto.

- MMCN_EXPAND Se envía cuando una carpeta necesita expandirse o contraerse.

- MMCN_MINIMIZED Se envía cuando se minimiza o maximiza una ventana.

- MMCN_PROPERTY_CHANGE Enviado para notificar a un objeto de complemento que la vista del objeto de complemento está a punto de cambiar.

- MMCN_REMOVE_CHILDREN Enviado cuando el complemento debe eliminar todo el subárbol que ha agregado debajo del nodo especificado.

- MMCN_RENAME Se envía la primera vez para consultar un cambio de nombre y la segunda vez para realizar el cambio de nombre.

- MMCN_SELECT Se envía cuando se selecciona un elemento del panel de ámbito o vista de resultados.

- MMCN_SHOW Se envía cuando se selecciona o anula la selección de un elemento de ámbito por primera vez.

- MMCN_VIEW_CHANGE Se envía cuando el complemento puede actualizar todas las vistas cuando se produce un cambio.

*Arg*<br/>
[en] Depende del tipo de notificación.

*Param*<br/>
[en] Depende del tipo de notificación.

*pComponentData*<br/>
[fuera] Puntero al objeto `IComponentData`que implementa . Este parámetro es NULL si la notificación no se reenvía desde `IComponentData::Notify`.

*pComponent*<br/>
[fuera] Puntero al objeto que `IComponent`implementa . Este parámetro es NULL si la notificación no se reenvía desde `IComponent::Notify`.

*type*<br/>
[en] Especifica el tipo de objeto. Puede tener uno de los siguientes valores:

- CCT_SCOPE objeto Data para el contexto del panel de ámbito.

- CCT_RESULT objeto Data para el contexto del panel de resultados.

- CCT_SNAPIN_MANAGER Objeto Data para el contexto del gestor de complementos.

- CCT_UNINITIALIZED objeto Data tiene un tipo no válido.

## <a name="csnapinitemimplquerypagesfor"></a><a name="querypagesfor"></a>CSnapInItemImpl::QueryPagesFor

Se llama para ver si el nodo de complemento admite páginas de propiedades.

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

## <a name="csnapinitemimplsetmenuinsertionflags"></a><a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionFlags

Llame a esta función para modificar los indicadores de inserción de menú, especificados por *pInsertionAllowed*, para el objeto de complemento.

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>Parámetros

*bBeforeInsertion*<br/>
[en] Distinto de cero si se debe llamar a la función antes de que se agreguen elementos al menú contextual; de lo contrario 0.

*pInsertionAllowed*<br/>
[adentro, fuera] Identifica los puntos de inserción de elementos de menú definidos por Microsoft Management Console (MMC) que se pueden usar. Esto puede ser una combinación de los siguientes indicadores:

- CCM_INSERTIONALLOWED_TOP Elementos se pueden insertar en la parte superior de un menú contextual.

- CCM_INSERTIONALLOWED_NEW elementos se pueden insertar en el submenú Crear nuevo.

- CCM_INSERTIONALLOWED_TASK Elementos se pueden insertar en el submenú Tarea.

- CCM_INSERTIONALLOWED_VIEW Elementos se pueden insertar en el menú de vista de la barra de herramientas o en el submenú Ver del menú contextual del panel de resultados.

### <a name="remarks"></a>Observaciones

Si está desarrollando un complemento principal, puede restablecer cualquiera de las marcas de inserción como una forma de restringir el tipo de elementos de menú que puede agregar una extensión de terceros. Por ejemplo, el complemento principal puede borrar la marca CCM_INSERTIONALLOWED_NEW para evitar que las extensiones agreguen sus propios elementos de menú Crear nuevo.

No debe intentar establecer bits en *pInsertionAllowed* que se borraron originalmente. Las versiones futuras de MMC pueden utilizar bits no definidos actualmente, por lo que no debe cambiar los bits que no están definidos actualmente.

## <a name="csnapinitemimplsettoolbarbuttoninfo"></a><a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo

Llame a esta función para modificar los estilos de botón de la barra de herramientas, del objeto de complemento, antes de crear la barra de herramientas.

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] El identificador del botón de la barra de herramientas que se va a establecer.

*fsState*<br/>
[en] Las marcas de estado del botón. Puede ser uno o más de los siguientes:

- TBSTATE_CHECKED El botón tiene el estilo TBSTYLE_CHECKED y se está presionando.

- TBSTATE_ENABLED El botón acepta la entrada del usuario. Un botón que no tiene este estado no acepta la entrada del usuario y está atenuado.

- TBSTATE_HIDDEN El botón no está visible y no puede recibir la entrada del usuario.

- TBSTATE_INDETERMINATE El botón está atenuado.

- TBSTATE_PRESSED Se está pulsando el botón.

- TBSTATE_WRAP Un salto de línea sigue al botón. El botón también debe tener el TBSTATE_ENABLED.

*fsType*<br/>
[en] Las marcas de estado del botón. Puede ser uno o más de los siguientes:

- TBSTYLE_BUTTON Crea un pulsador estándar.

- TBSTYLE_CHECK Crea un botón que alterna entre los estados presionados y no presionados cada vez que el usuario hace clic en él. El botón tiene un color de fondo diferente cuando está en el estado presionado.

- TBSTYLE_CHECKGROUP Crea un botón de verificación que permanece presionado hasta que se presiona otro botón del grupo.

- TBSTYLE_GROUP Crea un botón que permanece pulsado hasta que se presiona otro botón del grupo.

- TBSTYLE_SEP Crea un separador, lo que proporciona un pequeño espacio entre los grupos de botones. Un botón que tiene este estilo no recibe la entrada del usuario.

## <a name="csnapinitemimplupdatemenustate"></a><a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState

Llame a esta función para modificar un elemento de menú antes de insertarlo en el menú contextual del objeto de complemento.

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] El identificador del elemento de menú que se va a establecer.

*pBuf*<br/>
[en] Un puntero a la cadena para el elemento de menú que se va a actualizar.

*Banderas*<br/>
[en] Especifica los nuevos indicadores de estado. Esto puede ser una combinación de los siguientes indicadores:

- MF_POPUP Especifica que se trata de un submenú dentro del menú contextual. Los elementos de menú, los puntos de inserción `IInsertionPointID`y otros submenús se pueden agregar a este submenú utilizando su `lCommandID` archivo .

- MF_BITMAP y MF_OWNERDRAW Estas marcas no están permitidas y darán como resultado un valor devuelto de E_INVALIDARG.

- MF_SEPARATOR Dibuja una línea divisoria horizontal. Solo `IContextMenuProvider` se permite agregar elementos de menú con MF_SEPARATOR establecido.

- MF_CHECKED Coloca una marca de verificación junto al elemento de menú.

- MF_DISABLED Deshabilita el elemento de menú para que no se pueda seleccionar, pero la marca no lo grisá.

- MF_ENABLED Habilita el elemento de menú para que se pueda seleccionar, restableciéndolo desde su estado atenuado.

- MF_GRAYED Deshabilita el elemento de menú, atenuandolo para que no se pueda seleccionar.

- MF_MENUBARBREAK Funciona igual que la marca MF_MENUBREAK de una barra de menús. Para un menú desplegable, submenú o menú contextual, la nueva columna está separada de la columna antigua por una línea vertical.

- MF_MENUBREAK Coloca el elemento en una nueva línea (para una barra de menús) o en una nueva columna (para un menú desplegable, submenú o menú contextual) sin separar columnas.

- MF_UNCHECKED No coloca una marca de verificación junto al elemento (predeterminado).

Los siguientes grupos de indicadores no se pueden utilizar juntos:

- MF_DISABLED, MF_ENABLED y MF_GRAYED.

- MF_MENUBARBREAK y MF_MENUBREAK.

- MF_CHECKED y MF_UNCHECKED.

## <a name="csnapinitemimplupdatetoolbarbutton"></a><a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton

Llame a esta función para modificar un botón de barra de herramientas, del objeto de complemento, antes de que se muestre.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>Parámetros

*id*<br/>
Especifica el identificador de botón del botón de barra de herramientas que se va a actualizar.

*fsState*<br/>
Especifica un estado de botón de barra de herramientas. Si se va a establecer este estado, devuelva TRUE. Esto puede ser una combinación de los siguientes indicadores:

- ENABLED El botón acepta la entrada del usuario. Un botón que no tiene este estado no acepta la entrada del usuario y está atenuado.

- CHECKED El botón tiene el estilo CHECKED y se está presionando.

- OCULTO El botón no está visible y no puede recibir la entrada del usuario.

- INDETERMINATE El botón está atenuado.

- BUTTONPRESSED Se está pulsando el botón.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
