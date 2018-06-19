---
title: Clase CSnapInItemImpl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 759917497f06f80cde97f4e1bba9f3711add94a8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366463"
---
# <a name="csnapinitemimpl-class"></a>Clase CSnapInItemImpl
Esta clase proporciona métodos para implementar un objeto de nodo del complemento.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T, BOOL bIsExtension = FALSE>  
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `CSnapInItemImpl`.  
  
 *bIsExtension*  
 **TRUE** si el objeto es una extensión de complemento; en caso contrario, **FALSE**.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Agrega elementos de menú a un menú contextual.|  
|[CSnapInItemImpl::Command](#command)|Llamado por la consola cuando se selecciona un elemento de menú personalizado.|  
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Agrega páginas a la hoja de propiedades del complemento.|  
|[CSnapInItemImpl::FillData](#filldata)|Copia la información en el objeto de complemento en una secuencia especificada.|  
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Recupera el **RESULTDATAITEM** estructura del complemento.|  
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Determina el tipo de vista que se usa el panel de resultados.|  
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Recupera el **SCOPEDATAITEM** estructura del complemento.|  
|[CSnapInItemImpl::Notify](#notify)|Llama a la consola para notificar el complemento de las acciones realizadas por el usuario.|  
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Se llama para ver si el nodo en el complemento admite páginas de propiedades.|  
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Modifica las marcas de inserción de menú de un objeto de complemento.|  
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Establece la información del botón de barra de herramientas especificada.|  
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Actualiza el estado de un elemento de menú contextual.|  
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Actualiza el estado del botón de barra de herramientas especificada.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|El nombre del objeto de complemento.|  
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Las ventanas **RESULTDATAITEM** estructura usada por la `CSnapInItemImpl` objeto.|  
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Las ventanas **SCOPEDATAITEM** estructura usada por la `CSnapInItemImpl` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CSnapInItemImpl` Proporciona una implementación básica de un objeto de nodo del complemento, como agregar barras de herramientas y elementos de menú y el reenvío de comandos para el nodo de complemento a la función de controlador adecuado. Estas características se implementan utilizando varias interfaces distintas y asignan los tipos. La implementación predeterminada controla las notificaciones enviadas al objeto de nodo mediante la determinación de la instancia correcta de la clase derivada y, a continuación, reenviar el mensaje a la instancia correcta.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsnap.h  
  
##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems  
 Este método implementa la función de Win32 [IExtendContextMenu::AddMenuItems](http://msdn.microsoft.com/library/aa814841).  
  
```
AddMenuItems(  
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parámetros  
 *piCallback*  
 [in] Puntero a la **IContextMenuCallback** que puede agregar elementos al menú contextual.  
  
 `pInsertionAllowed`  
 [entrada, salida] Identifica definido de Microsoft Management Console MMC, elemento de menú puntos de inserción que se pueden usar. Esto puede ser una combinación de los siguientes indicadores:  
  
- **CCM_INSERTIONALLOWED_TOP** elementos se pueden insertar en la parte superior de un menú contextual.  
  
- **CCM_INSERTIONALLOWED_NEW** se pueden insertar elementos en el submenú Crear nuevo.  
  
- **CCM_INSERTIONALLOWED_TASK** se pueden insertar elementos en el submenú de la tarea.  
  
- **CCM_INSERTIONALLOWED_VIEW** se pueden insertar elementos en el menú de vista de la barra de herramientas o en el submenú de la vista del menú contextual de panel de resultados.  
  
 `type`  
 [in] Especifica el tipo de objeto. Puede tener uno de los valores siguientes:  
  
- **CCT_SCOPE** objeto de datos para el contexto del panel de ámbito.  
  
- **CCT_RESULT** objeto de datos para el contexto del panel de resultados.  
  
- **CCT_SNAPIN_MANAGER** objeto de datos para el contexto de administrador de complementos.  
  
- **CCT_UNINITIALIZED** objeto de datos tiene un tipo no válido.  
  
##  <a name="command"></a>  CSnapInItemImpl::Command  
 Este método implementa la función de Win32 [IExtendContextMenu::Command](http://msdn.microsoft.com/library/aa814842).  
  
```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parámetros  
 *lCommandID*  
 [in] Especifica el identificador de comando del elemento de menú.  
  
 `type`  
 [in] Especifica el tipo de objeto. Puede tener uno de los valores siguientes:  
  
- **CCT_SCOPE** objeto de datos para el contexto del panel de ámbito.  
  
- **CCT_RESULT** objeto de datos para el contexto del panel de resultados.  
  
- **CCT_SNAPIN_MANAGER** objeto de datos para el contexto de administrador de complementos.  
  
- **CCT_UNINITIALIZED** objeto de datos tiene un tipo no válido.  
  
##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages  
 Este método implementa la función de Win32 [IExtendPropertySheet::CreatePropertyPages](http://msdn.microsoft.com/library/aa814846).  
  
```
CreatePropertyPages(  
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpProvider*  
 [in] Puntero a la **IPropertySheetCallback** interfaz.  
  
 *Identificador*  
 [in] Especifica el identificador usado para enrutar la **MMCN_PROPERTY_CHANGE** mensaje de notificación a la clase de datos adecuado.  
  
 *pUnk*  
 [in] Puntero a la **IExtendPropertySheet** interfaz en el objeto que contiene información contextual sobre el nodo.  
  
 `type`  
 [in] Especifica el tipo de objeto. Puede tener uno de los valores siguientes:  
  
- **CCT_SCOPE** objeto de datos para el contexto del panel de ámbito.  
  
- **CCT_RESULT** objeto de datos para el contexto del panel de resultados.  
  
- **CCT_SNAPIN_MANAGER** objeto de datos para el contexto de administrador de complementos.  
  
- **CCT_UNINITIALIZED** objeto de datos tiene un tipo no válido.  
  
##  <a name="csnapinitemimpl"></a>  CSnapInItemImpl::CSnapInItemImpl  
 Construye un objeto `CSnapInItemImpl`.  
  
```
CSnapInItemImpl();
```  
  
##  <a name="filldata"></a>  CSnapInItemImpl::FillData  
 Esta función se invoca para recuperar información sobre el elemento.  
  
```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```  
  
### <a name="parameters"></a>Parámetros  
 `cf`  
 [in] El formato (texto, texto enriquecido o texto enriquecido con elementos OLE) del Portapapeles.  
  
 `pStream`  
 [in] Un puntero a la secuencia que contiene los datos del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Para implementar correctamente esta función, copie la información correcta en la secuencia ( `pStream`), según el formato de Portapapeles indicado por `cf`.  
  
##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType  
 Llame a esta función para recuperar el tipo de vista para el panel de resultados del objeto de complemento.  
  
```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```  
  
### <a name="parameters"></a>Parámetros  
 *ppViewType*  
 [out] Puntero a la dirección del tipo de vista devuelta.  
  
 *pViewOptions*  
 [out] Puntero a la **MMC_VIEW_OPTIONS** enumeración, que proporciona la consola con las opciones especificadas por el complemento de propietario. Este valor puede ser uno de los siguientes:  
  
- **MMC_VIEW_OPTIONS_NOLISTVIEWS** = 0 x 00000001 indica a la consola abstenerse de presentar opciones de vista de lista estándar en el **vista** menú. Permite que el complemento de mostrar sus propias vistas personalizadas sólo en el panel de vista de resultados. Se trata de la única marca de opción definida en este momento.  
  
- **MMC_VIEW_OPTIONS_NONE** = 0 permite las opciones de vista predeterminada.  
  
##  <a name="getscopepaneinfo"></a>  CSnapInItemImpl::GetScopePaneInfo  
 Llame a esta función para recuperar el **SCOPEDATAITEM** estructura del complemento.  
  
```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```  
  
### <a name="parameters"></a>Parámetros  
 *pScopeDataItem*  
 [out] Un puntero a la **SCOPEDATAITEM** estructura de la `CSnapInItemImpl` objeto.  
  
##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo  
 Llame a esta función para recuperar el **RESULTDATAITEM** estructura del complemento.  
  
```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```  
  
### <a name="parameters"></a>Parámetros  
 *pResultDataItem*  
 [out] Un puntero a la **RESULTDATAITEM** estructura de la `CSnapInItemImpl` objeto.  
  
##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName  
 Contiene la cadena que se muestra para el elemento del nodo.  
  
```
CComBSTR m_bstrDisplayName;
```  
  
##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem  
 El `SCOPEDATAITEM` estructura del objeto de complemento de datos.  
  
```
SCOPEDATAITEM m_scopeDataItem;
```  
  
##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem  
 El [RESULTDATAITEM](http://msdn.microsoft.com/library/aa815165) estructura del objeto de complemento de datos.  
  
```
RESULTDATAITEM m_resultDataItem;
```  
  
##  <a name="notify"></a>  CSnapInItemImpl::Notify  
 Se llama cuando el objeto de complemento se actúa sobre el usuario.  
  
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
 `event`  
 [in] Identifica una acción realizada por un usuario. Son posibles las siguientes notificaciones:  
  
- **MMCN_ACTIVATE** enviados cuando una ventana es está activado y desactivado.  
  
- **MMCN_ADD_IMAGES** enviado para agregar imágenes al panel de resultados.  
  
- **MMCN_BTN_CLICK** se envía cuando el usuario hace clic en uno de los botones de barra de herramientas.  
  
- **MMCN_CLICK** se envía cuando un usuario hace clic en un botón del mouse en un elemento de vista de lista.  
  
- **MMCN_DBLCLICK** se envía cuando un usuario hace doble clic en un botón del mouse en un elemento de vista de lista.  
  
- **MMCN_DELETE** envía para informar al complemento de que el objeto debe ser eliminado.  
  
- **MMCN_EXPAND** envía cuando es necesario expandir o contraer una carpeta.  
  
- **MMCN_MINIMIZED** enviados cuando una ventana es está minimizada o maximizada.  
  
- **MMCN_PROPERTY_CHANGE** enviado para notificar a un objeto de complemento que el complemento de vista de objeto que se va a cambiar.  
  
- **MMCN_REMOVE_CHILDREN** se envía cuando el complemento debe eliminar todo el subárbol agregada por debajo del nodo especificado.  
  
- **MMCN_RENAME** envía la primera vez que se consulta un cambio de nombre y la segunda vez para realizar el cambio de nombre.  
  
- **MMCN_SELECT** se envía cuando se selecciona un elemento en el panel de vista de ámbito o resultado.  
  
- **MMCN_SHOW** se envía cuando se selecciona un elemento de ámbito o se anula la selección por primera vez.  
  
- **MMCN_VIEW_CHANGE** se envía cuando el complemento puede actualizar todas las vistas cuando se produce un cambio.  
  
 `arg`  
 [in] Depende del tipo de notificación.  
  
 `param`  
 [in] Depende del tipo de notificación.  
  
 *pComponentData*  
 [out] Un puntero al objeto que implementa **IComponentData**. Este parámetro es **NULL** si la notificación no se reenvían desde **IComponentData:: Notify**.  
  
 *pComponent*  
 [out] Un puntero al objeto que implementa **IComponent**. Este parámetro es **NULL** si la notificación no se reenvían desde **IComponent::Notify**.  
  
 `type`  
 [in] Especifica el tipo de objeto. Puede tener uno de los valores siguientes:  
  
- **CCT_SCOPE** objeto de datos para el contexto del panel de ámbito.  
  
- **CCT_RESULT** objeto de datos para el contexto del panel de resultados.  
  
- **CCT_SNAPIN_MANAGER** objeto de datos para el contexto de administrador de complementos.  
  
- **CCT_UNINITIALIZED** objeto de datos tiene un tipo no válido.  
  
##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor  
 Se llama para ver si el nodo en el complemento admite páginas de propiedades.  
  
```
QueryPagesFor(DATA_OBJECT_TYPES type);
```  
  
##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags  
 Llame a esta función para modificar las marcas de inserción de menú, especificadas por `pInsertionAllowed`, para el objeto de complemento.  
  
```
void SetMenuInsertionFlags(  
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```  
  
### <a name="parameters"></a>Parámetros  
 *bBeforeInsertion*  
 [in] Es distinto de cero si la función se debe llamar antes de que se agregan elementos al menú contextual; en caso contrario es 0.  
  
 `pInsertionAllowed`  
 [entrada, salida] Identifica definido de Microsoft Management Console MMC, elemento de menú puntos de inserción que se pueden usar. Esto puede ser una combinación de los siguientes indicadores:  
  
- **CCM_INSERTIONALLOWED_TOP** elementos se pueden insertar en la parte superior de un menú contextual.  
  
- **CCM_INSERTIONALLOWED_NEW** se pueden insertar elementos en el submenú Crear nuevo.  
  
- **CCM_INSERTIONALLOWED_TASK** se pueden insertar elementos en el submenú de la tarea.  
  
- **CCM_INSERTIONALLOWED_VIEW** se pueden insertar elementos en el menú de vista de la barra de herramientas o en el submenú de la vista del menú contextual de panel de resultados.  
  
### <a name="remarks"></a>Comentarios  
 Si está desarrollando un complemento principal, puede restablecer cualquiera de las marcas de inserción como una forma de restringir el tipo de elementos de menú que se puede agregar una extensión de otro fabricante. Por ejemplo, puede desactivar el complemento principal de la **CCM_INSERTIONALLOWED_NEW** marca para impedir que las extensiones de agregar sus propios elementos de menú Crear nuevo.  
  
 No debería intentar establecer los bits `pInsertionAllowed` que originalmente se borraron. Futuras versiones de MMC pueden utilizar bits no actualmente definidas por lo que no debería cambiar bits que no están definidos actualmente.  
  
##  <a name="settoolbarbuttoninfo"></a>  CSnapInItemImpl::SetToolbarButtonInfo  
 Llame a esta función para modificar los estilos de botón de barra de herramientas del objeto de complemento, antes de crea la barra de herramientas.  
  
```
void SetToolbarButtonInfo(  
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] El identificador del botón de barra de herramientas se establezca.  
  
 `fsState`  
 [in] Los indicadores de estado del botón. Puede tener uno o varios de los siguientes:  
  
- `TBSTATE_CHECKED` El botón tiene el **TBSTYLE_CHECKED** el estilo y se presiona.  
  
- `TBSTATE_ENABLED` El botón acepta proporcionados por el usuario. Un botón que no tiene este estado no acepta proporcionados por el usuario y está deshabilitado.  
  
- `TBSTATE_HIDDEN` El botón no está visible y no puede recibir proporcionados por el usuario.  
  
- `TBSTATE_INDETERMINATE` El botón está atenuado.  
  
- `TBSTATE_PRESSED` Se presiona el botón.  
  
- `TBSTATE_WRAP` Un salto de línea sigue el botón. El botón también debe tener la `TBSTATE_ENABLED`.  
  
 *fsType*  
 [in] Los indicadores de estado del botón. Puede tener uno o varios de los siguientes:  
  
- `TBSTYLE_BUTTON` Crea un botón de comando estándar.  
  
- `TBSTYLE_CHECK` Crea un botón que alterne entre los Estados presionados y presiona no cada vez que el usuario hace clic en él. El botón tiene un color de fondo diferente cuando se encuentra en estado presionado.  
  
- `TBSTYLE_CHECKGROUP` Crea un botón para comprobar que se mantiene presionado hasta que se presiona el botón otra en el grupo.  
  
- `TBSTYLE_GROUP` Crea un botón que permanece presionado hasta que se presiona el botón otra en el grupo.  
  
- `TBSTYLE_SEP` Crea un separador, proporcionando un pequeño espacio entre los grupos de botones. Un botón que tiene este estilo no recibe proporcionados por el usuario.  
  
##  <a name="updatemenustate"></a>  CSnapInItemImpl::UpdateMenuState  
 Llame a esta función para modificar un elemento de menú antes de que éste se inserta en el menú contextual del objeto de complemento.  
  
```
void UpdateMenuState(  
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] El identificador del elemento de menú se establezca.  
  
 `pBuf`  
 [in] Un puntero a la cadena para el elemento de menú para actualizarse.  
  
 `flags`  
 [in] Especifica las marcas de estado nuevo. Esto puede ser una combinación de los siguientes indicadores:  
  
- **MF_POPUP** especifica que se trata de un submenú en el menú contextual. Elementos de menú y puntos de inserción, más submenús pueden agregarse a este submenú mediante su **lCommandID** como sus **IInsertionPointID**.  
  
- **MF_BITMAP** y `MF_OWNERDRAW` estas marcas no se permiten y dará como resultado un valor devuelto de `E_INVALIDARG`.  
  
- **MF_SEPARATOR** dibuja una línea divisoria horizontal. Solo **IContextMenuProvider** tiene permiso para agregar elementos de menú con **MF_SEPARATOR** establecido.  
  
- **MF_CHECKED** coloca una marca de verificación situada junto al elemento de menú.  
  
- **MF_DISABLED** deshabilita el elemento de menú para que no se puede seleccionar, pero el indicador no gris.  
  
- `MF_ENABLED` Permite que el elemento de menú para poder seleccionarlo, restaurarla a partir de su estado en gris.  
  
- **MF_GRAYED** deshabilita el elemento de menú se atenúa por lo que no se pueden seleccionar.  
  
- **MF_MENUBARBREAK** funciona igual que el **MF_MENUBREAK** marca para una barra de menús. Para un menú desplegable, un submenú o un menú contextual, se separa la nueva columna de la columna antigua con una línea vertical.  
  
- **MF_MENUBREAK** el elemento se coloca en una nueva línea (para una barra de menús) o en una nueva columna (para un menú desplegable, un submenú o un menú contextual) sin separación de columnas.  
  
- **MF_UNCHECKED** no colocar una marca de verificación situada junto al elemento (valor predeterminado).  
  
 Los siguientes grupos de marcas no pueden usarse juntos:  
  
- **MF_DISABLED**, `MF_ENABLED`, y **MF_GRAYED**.  
  
- **MF_MENUBARBREAK** y **MF_MENUBREAK**.  
  
- **MF_CHECKED** y **MF_UNCHECKED**.  
  
##  <a name="updatetoolbarbutton"></a>  CSnapInItemImpl::UpdateToolbarButton  
 Llame a esta función para modificar un botón de barra de herramientas del objeto de complemento, antes de que se muestre.  
  
```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 Especifica el identificador de botón del botón de barra de herramientas debe actualizarse.  
  
 `fsState`  
 Especifica un estado de botón de barra de herramientas. Si este estado se va a establecer, devolver **TRUE**. Esto puede ser una combinación de los siguientes indicadores:  
  
- **HABILITADO** el botón acepta proporcionados por el usuario. Un botón que no tiene este estado no acepta proporcionados por el usuario y está deshabilitado.  
  
- **COMPROBAR** el botón tiene el **COMPRUEBAN** el estilo y se presiona.  
  
- **HIDDEN** el botón no está visible y no puede recibir proporcionados por el usuario.  
  
- **INDETERMINADO** el botón está atenuado.  
  
- **BUTTONPRESSED** se presiona el botón.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
