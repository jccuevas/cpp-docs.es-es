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
ms.openlocfilehash: a9ebcf8827d79a9613ce14251d361dd607aa6af3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496556"
---
# <a name="csnapinitemimpl-class"></a>Clase CSnapInItemImpl

Esta clase proporciona métodos para implementar un objeto de nodo de complemento.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `CSnapInItemImpl`.

*bIsExtension*<br/>
TRUE si el objeto es una extensión de complemento; en caso contrario, FALSE.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Agrega elementos de menú a un menú contextual.|
|[CSnapInItemImpl::Command](#command)|Lo llama la consola cuando se selecciona un elemento de menú personalizado.|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Agrega páginas a la hoja de propiedades del complemento.|
|[CSnapInItemImpl::FillData](#filldata)|Copia información en el objeto de complemento en una secuencia especificada.|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Recupera la `RESULTDATAITEM` estructura del complemento.|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Determina el tipo de vista que usa el panel de resultados.|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Recupera la `SCOPEDATAITEM` estructura del complemento.|
|[CSnapInItemImpl::Notify](#notify)|La consola lo llama para notificar al complemento las acciones realizadas por el usuario.|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Se llama para ver si el nodo de complemento admite páginas de propiedades.|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Modifica las marcas de inserción de menú para un objeto de complemento.|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Establece la información del botón de barra de herramientas especificado.|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Actualiza el estado de un elemento de menú contextual.|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Actualiza el estado del botón de la barra de herramientas especificado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Nombre del objeto de complemento.|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Estructura de `RESULTDATAITEM` Windows utilizada por el `CSnapInItemImpl` objeto.|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Estructura de `SCOPEDATAITEM` Windows utilizada por el `CSnapInItemImpl` objeto.|

## <a name="remarks"></a>Comentarios

`CSnapInItemImpl`proporciona una implementación básica para un objeto de nodo de complementos, como agregar elementos de menú y barras de herramientas, y reenviar comandos para el nodo de complemento a la función de controlador adecuada. Estas características se implementan mediante varias interfaces y tipos de mapa diferentes. La implementación predeterminada administra las notificaciones enviadas al objeto de nodo determinando la instancia correcta de la clase derivada y reenviando el mensaje a la instancia correcta.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsnap. h

##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems

Este método implementa la función de Win32 [IExtendContextMenu:: AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems).

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parámetros

*piCallback*<br/>
de Puntero a `IContextMenuCallback` que puede agregar elementos al menú contextual.

*pInsertionAllowed*<br/>
[in, out] Identifica los puntos de inserción de elementos de menú definidos por Microsoft Management Console (MMC) que se pueden usar. Puede ser una combinación de las marcas siguientes:

- Los elementos CCM_INSERTIONALLOWED_TOP se pueden insertar en la parte superior de un menú contextual.

- Los elementos CCM_INSERTIONALLOWED_NEW se pueden insertar en el submenú crear nuevo.

- Los elementos CCM_INSERTIONALLOWED_TASK se pueden insertar en el submenú tarea.

- Los elementos de CCM_INSERTIONALLOWED_VIEW se pueden insertar en el menú de vista de la barra de herramientas o en el submenú vista del menú contextual del panel de resultados.

*type*<br/>
de Especifica el tipo de objeto. Puede tener uno de los siguientes valores:

- Objeto de datos CCT_SCOPE para el contexto del panel de ámbito.

- Objeto de datos CCT_RESULT para el contexto del panel de resultados.

- Objeto de datos CCT_SNAPIN_MANAGER para el contexto del administrador de complementos.

- El objeto de datos CCT_UNINITIALIZED tiene un tipo no válido.

##  <a name="command"></a>  CSnapInItemImpl::Command

Este método implementa la función [IExtendContextMenu:: Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command)de Win32.

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parámetros

*lCommandID*<br/>
de Especifica el identificador de comando del elemento de menú.

*type*<br/>
de Especifica el tipo de objeto. Puede tener uno de los siguientes valores:

- Objeto de datos CCT_SCOPE para el contexto del panel de ámbito.

- Objeto de datos CCT_RESULT para el contexto del panel de resultados.

- Objeto de datos CCT_SNAPIN_MANAGER para el contexto del administrador de complementos.

- El objeto de datos CCT_UNINITIALIZED tiene un tipo no válido.

##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages

Este método implementa la función de Win32 [IExtendPropertySheet:: CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2).

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parámetros

*lpProvider*<br/>
de Puntero a la `IPropertySheetCallback` interfaz.

*handle*<br/>
de Especifica el identificador que se usa para enrutar el mensaje de notificación MMCN_PROPERTY_CHANGE a la clase de datos adecuada.

*pUnk*<br/>
de Puntero a la `IExtendPropertySheet` interfaz del objeto que contiene información de contexto sobre el nodo.

*type*<br/>
de Especifica el tipo de objeto. Puede tener uno de los siguientes valores:

- Objeto de datos CCT_SCOPE para el contexto del panel de ámbito.

- Objeto de datos CCT_RESULT para el contexto del panel de resultados.

- Objeto de datos CCT_SNAPIN_MANAGER para el contexto del administrador de complementos.

- El objeto de datos CCT_UNINITIALIZED tiene un tipo no válido.

##  <a name="csnapinitemimpl"></a>  CSnapInItemImpl::CSnapInItemImpl

Construye un objeto `CSnapInItemImpl`.

```
CSnapInItemImpl();
```

##  <a name="filldata"></a>  CSnapInItemImpl::FillData

Se llama a esta función para recuperar información sobre el elemento.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>Parámetros

*cf*<br/>
de El formato (texto, texto enriquecido o texto enriquecido con elementos OLE) del portapapeles.

*pStream*<br/>
de Puntero a la secuencia que contiene los datos del objeto.

### <a name="remarks"></a>Comentarios

Para implementar esta función correctamente, copie la información correcta en la secuencia (*pStream*), en función del formato del portapapeles indicado por *CF*.

##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType

Llame a esta función para recuperar el tipo de vista del panel de resultados del objeto de complemento.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>Parámetros

*ppViewType*<br/>
enuncia Puntero a la dirección del tipo de vista devuelto.

*pViewOptions*<br/>
enuncia Puntero a la enumeración MMC_VIEW_OPTIONS, que proporciona a la consola opciones especificadas por el complemento propietario. Este valor puede ser uno de los siguientes:

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 indica a la consola que no presente opciones de vista de lista estándar en el menú **Ver** . Permite que el complemento muestre sus propias vistas personalizadas solo en el panel vista de resultados. Esta es la única marca de opción definida en este momento.

- MMC_VIEW_OPTIONS_NONE = 0 permite las opciones de vista predeterminada.

##  <a name="getscopepaneinfo"></a>  CSnapInItemImpl::GetScopePaneInfo

Llame a esta función para recuperar `SCOPEDATAITEM` la estructura del complemento.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>Parámetros

*pScopeDataItem*<br/>
enuncia Puntero a la `SCOPEDATAITEM` estructura `CSnapInItemImpl` del objeto.

##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo

Llame a esta función para recuperar `RESULTDATAITEM` la estructura del complemento.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>Parámetros

*pResultDataItem*<br/>
enuncia Puntero a la `RESULTDATAITEM` estructura `CSnapInItemImpl` del objeto.

##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName

Contiene la cadena que se muestra para el elemento de nodo.

```
CComBSTR m_bstrDisplayName;
```

##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem

`SCOPEDATAITEM` Estructura del objeto de datos del complemento.

```
SCOPEDATAITEM m_scopeDataItem;
```

##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem

Estructura [RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem) del objeto de datos del complemento.

```
RESULTDATAITEM m_resultDataItem;
```

##  <a name="notify"></a>  CSnapInItemImpl::Notify

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
de Identifica una acción realizada por un usuario. Las siguientes notificaciones son posibles:

- MMCN_ACTIVATE se envía cuando una ventana se está activando y desactivando.

- MMCN_ADD_IMAGES enviado para agregar imágenes al panel de resultados.

- MMCN_BTN_CLICK se envía cuando el usuario hace clic en uno de los botones de la barra de herramientas.

- MMCN_CLICK se envía cuando un usuario hace clic en un botón del mouse en un elemento de vista de lista.

- MMCN_DBLCLICK se envía cuando un usuario hace doble clic en un botón del mouse en un elemento de vista de lista.

- MMCN_DELETE enviado para informar al complemento de que se debe eliminar el objeto.

- MMCN_EXPAND se envía cuando es necesario expandir o contraer una carpeta.

- MMCN_MINIMIZED se envía cuando se minimiza o maximiza una ventana.

- MMCN_PROPERTY_CHANGE enviado para notificar a un objeto de complemento que está a punto de cambiar la vista del objeto de complemento.

- MMCN_REMOVE_CHILDREN se envía cuando el complemento debe eliminar todo el subárbol que ha agregado debajo del nodo especificado.

- MMCN_RENAME se envía la primera vez para consultar un cambio de nombre y la segunda vez para realizar el cambio de nombre.

- MMCN_SELECT se envía cuando se selecciona un elemento en el panel de la vista de ámbito o de resultados.

- MMCN_SHOW se envía cuando se selecciona o se anula la selección de un elemento de ámbito por primera vez.

- MMCN_VIEW_CHANGE se envía cuando el complemento puede actualizar todas las vistas cuando se produce un cambio.

*arg*<br/>
de Depende del tipo de notificación.

*param*<br/>
de Depende del tipo de notificación.

*pComponentData*<br/>
enuncia Puntero al objeto que implementa `IComponentData`. Este parámetro es NULL si no se reenvía `IComponentData::Notify`la notificación.

*pComponent*<br/>
enuncia Puntero al objeto que implementa `IComponent`. Este parámetro es NULL si no se reenvía `IComponent::Notify`la notificación.

*type*<br/>
de Especifica el tipo de objeto. Puede tener uno de los siguientes valores:

- Objeto de datos CCT_SCOPE para el contexto del panel de ámbito.

- Objeto de datos CCT_RESULT para el contexto del panel de resultados.

- Objeto de datos CCT_SNAPIN_MANAGER para el contexto del administrador de complementos.

- El objeto de datos CCT_UNINITIALIZED tiene un tipo no válido.

##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor

Se llama para ver si el nodo de complemento admite páginas de propiedades.

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags

Llame a esta función para modificar las marcas de inserción de menú, especificadas por *pInsertionAllowed*, para el objeto de complemento.

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>Parámetros

*bBeforeInsertion*<br/>
de Distinto de cero si se debe llamar a la función antes de que se agreguen elementos al menú contextual; de lo contrario, es 0.

*pInsertionAllowed*<br/>
[in, out] Identifica los puntos de inserción de elementos de menú definidos por Microsoft Management Console (MMC) que se pueden usar. Puede ser una combinación de las marcas siguientes:

- Los elementos CCM_INSERTIONALLOWED_TOP se pueden insertar en la parte superior de un menú contextual.

- Los elementos CCM_INSERTIONALLOWED_NEW se pueden insertar en el submenú crear nuevo.

- Los elementos CCM_INSERTIONALLOWED_TASK se pueden insertar en el submenú tarea.

- Los elementos de CCM_INSERTIONALLOWED_VIEW se pueden insertar en el menú de vista de la barra de herramientas o en el submenú vista del menú contextual del panel de resultados.

### <a name="remarks"></a>Comentarios

Si está desarrollando un complemento principal, puede restablecer cualquiera de las marcas de inserción como una forma de restringir el tipo de elementos de menú que puede Agregar una extensión de terceros. Por ejemplo, el complemento principal puede borrar la marca CCM_INSERTIONALLOWED_NEW para evitar que las extensiones agreguen sus propios elementos de menú crear nuevos.

No debe intentar establecer bits en *pInsertionAllowed* que originalmente se borraron. Las versiones futuras de MMC pueden utilizar bits no definidos actualmente, por lo que no debe cambiar los bits que no están definidos actualmente.

##  <a name="settoolbarbuttoninfo"></a>  CSnapInItemImpl::SetToolbarButtonInfo

Llame a esta función para modificar los estilos de botón de la barra de herramientas, del objeto de complemento, antes de que se cree la barra de herramientas.

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>Parámetros

*id*<br/>
de IDENTIFICADOR del botón de la barra de herramientas que se va a establecer.

*fsState*<br/>
de Marcas de estado del botón. Puede ser uno o varios de los siguientes:

- TBSTATE_CHECKED el botón tiene el estilo TBSTYLE_CHECKED y se presiona.

- TBSTATE_ENABLED el botón acepta datos proporcionados por el usuario. Un botón que no tiene este estado no acepta datos proporcionados por el usuario y está atenuado.

- TBSTATE_HIDDEN el botón no está visible y no puede recibir datos proporcionados por el usuario.

- TBSTATE_INDETERMINATE el botón está atenuado.

- TBSTATE_PRESSED se está presionando el botón.

- TBSTATE_WRAP un salto de línea sigue el botón. El botón también debe tener TBSTATE_ENABLED.

*fsType*<br/>
de Marcas de estado del botón. Puede ser uno o varios de los siguientes:

- TBSTYLE_BUTTON crea un botón de tecla de preinstalación estándar.

- TBSTYLE_CHECK crea un botón que alterna entre los Estados presionado y no presionado cada vez que el usuario hace clic en él. El botón tiene un color de fondo diferente cuando está en estado presionado.

- TBSTYLE_CHECKGROUP crea un botón de verificación que permanece presionado hasta que se presiona otro botón del grupo.

- TBSTYLE_GROUP crea un botón que permanece presionado hasta que se presiona otro botón del grupo.

- TBSTYLE_SEP crea un separador, lo que proporciona un pequeño espacio entre los grupos de botones. Un botón que tiene este estilo no recibe datos proporcionados por el usuario.

##  <a name="updatemenustate"></a>  CSnapInItemImpl::UpdateMenuState

Llame a esta función para modificar un elemento de menú antes de insertarlo en el menú contextual del objeto de complemento.

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>Parámetros

*id*<br/>
de IDENTIFICADOR del elemento de menú que se va a establecer.

*pBuf*<br/>
de Puntero a la cadena del elemento de menú que se va a actualizar.

*flags*<br/>
de Especifica las nuevas marcas de estado. Puede ser una combinación de las marcas siguientes:

- MF_POPUP especifica que se trata de un submenú del menú contextual. Los elementos de menú, los puntos de inserción y otros submenús pueden agregarse a este submenú usando `IInsertionPointID`su `lCommandID` como.

- MF_BITMAP y MF_OWNERDRAW estas marcas no se permiten y dará como resultado un valor devuelto de E_INVALIDARG.

- MF_SEPARATOR dibuja una línea de división horizontal. Solo `IContextMenuProvider` se permite agregar elementos de menú con MF_SEPARATOR establecido.

- MF_CHECKED coloca una marca de verificación junto al elemento de menú.

- MF_DISABLED deshabilita el elemento de menú para que no se pueda seleccionar, pero la marca no lo atenúa.

- MF_ENABLED habilita el elemento de menú para que se pueda seleccionar y restaurar desde su estado atenuado.

- MF_GRAYED deshabilita el elemento de menú y lo atenúa de modo que no se puede seleccionar.

- MF_MENUBARBREAK funciona igual que la marca MF_MENUBREAK para una barra de menús. En un menú desplegable, un submenú o un menú contextual, la nueva columna se separa de la antigua en una línea vertical.

- MF_MENUBREAK coloca el elemento en una nueva línea (para una barra de menús) o en una nueva columna (para un menú desplegable, un submenú o un menú contextual) sin separar las columnas.

- MF_UNCHECKED no coloca una marca de verificación junto al elemento (valor predeterminado).

Los siguientes grupos de marcas no se pueden usar juntos:

- MF_DISABLED, MF_ENABLED y MF_GRAYED.

- MF_MENUBARBREAK y MF_MENUBREAK.

- MF_CHECKED y MF_UNCHECKED.

##  <a name="updatetoolbarbutton"></a>  CSnapInItemImpl::UpdateToolbarButton

Llame a esta función para modificar un botón de la barra de herramientas, del objeto de complemento, antes de que se muestre.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>Parámetros

*id*<br/>
Especifica el identificador del botón del botón de la barra de herramientas que se va a actualizar.

*fsState*<br/>
Especifica el estado de un botón de la barra de herramientas. Si se va a establecer este estado, se devuelve TRUE. Puede ser una combinación de las marcas siguientes:

- HABILITAdo el botón acepta datos proporcionados por el usuario. Un botón que no tiene este estado no acepta datos proporcionados por el usuario y está atenuado.

- ACTIVADO el botón tiene el estilo activado y se presiona.

- OCULTO el botón no está visible y no puede recibir datos proporcionados por el usuario.

- Indeterminado el botón está atenuado.

- BUTTONPRESSED se está presionando el botón.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
