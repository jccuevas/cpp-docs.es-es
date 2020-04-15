---
title: Clase IPropertyPageImpl
ms.date: 11/04/2016
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
ms.openlocfilehash: ac8fcb3b8b2bd0f876cf28d58e195000112373f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329583"
---
# <a name="ipropertypageimpl-class"></a>Clase IPropertyPageImpl

Esta clase `IUnknown` implementa y proporciona una implementación predeterminada de la [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) interfaz.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IPropertyPageImpl`de .

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPropertyPageImpl::Activate](#activate)|Crea la ventana del cuadro de diálogo para la página de propiedades.|
|[IPropertyPageImpl::Aplicar](#apply)|Aplica los valores de página de propiedades `SetObjects`actuales a los objetos subyacentes especificados a través de . La implementación de ATL devuelve S_OK.|
|[IPropertyPageImpl::Deactivate](#deactivate)|Destruye la ventana `Activate`creada con .|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Recupera información sobre la página de propiedades.|
|[IPropertyPageImpl::Ayuda](#help)|Invoca la ayuda de Windows para la página de propiedades.|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Indica si la página de propiedades ha cambiado desde que se activó.|
|[IPropertyPageImpl::Move](#move)|Coloca y cambia el tamaño del cuadro de diálogo de la página de propiedades.|
|[IPropertyPageImpl::SetDirty](#setdirty)|Marca el estado de la página de propiedades como cambiado o sin cambios.|
|[IPropertyPageImpl::SetObjects](#setobjects)|Proporciona una `IUnknown` matriz de punteros para los objetos asociados a la página de propiedades. Estos objetos reciben los valores `Apply`de página de propiedades actuales a través de una llamada a .|
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Proporciona la página `IPropertyPageSite` de propiedades con un puntero, a través del cual la página de propiedades se comunica con el marco de propiedades.|
|[IPropertyPageImpl::Show](#show)|Hace que el cuadro de diálogo de la página de propiedades sea visible o invisible.|
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Procesa una pulsación de tecla especificada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Especifica si el estado de la página de propiedades ha cambiado.|
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Almacena el identificador de recurso asociado a la cadena de texto que describe la página de propiedades.|
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Almacena el identificador de contexto para el tema de ayuda asociado a la página de propiedades.|
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Almacena el identificador de recurso asociado con el nombre del archivo de ayuda que describe la página de propiedades.|
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Almacena el identificador de recurso asociado a la cadena de texto que aparece en la pestaña de la página de propiedades.|
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Almacena el número de objetos asociados a la página de propiedades.|
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Apunta a `IPropertyPageSite` la interfaz a través de la cual la página de propiedades se comunica con el marco de propiedad.|
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Apunta a una `IUnknown` matriz de punteros a los objetos asociados a la página de propiedades.|
|[IPropertyPageImpl::m_size](#m_size)|Almacena el alto y el ancho del cuadro de diálogo de la página de propiedades, en píxeles.|

## <a name="remarks"></a>Observaciones

El [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) interfaz permite a un objeto para administrar una página de propiedades determinada dentro de una hoja de propiedades. Clase `IPropertyPageImpl` proporciona una implementación predeterminada `IUnknown` de esta interfaz e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="ipropertypageimplactivate"></a><a name="activate"></a>IPropertyPageImpl::Activate

Crea la ventana del cuadro de diálogo para la página de propiedades.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, el cuadro de diálogo siempre es no modal, independientemente del valor del parámetro *bModal.*

Consulte [IPropertyPage::Activate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) en el Windows SDK.

## <a name="ipropertypageimplapply"></a><a name="apply"></a>IPropertyPageImpl::Aplicar

Aplica los valores de página de propiedades `SetObjects`actuales a los objetos subyacentes especificados a través de .

```
HRESULT Apply();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IPropertyPage::Apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) en el Windows SDK.

## <a name="ipropertypageimpldeactivate"></a><a name="deactivate"></a>IPropertyPageImpl::Deactivate

Destruye la ventana del cuadro de diálogo creada con [Activar](#activate).

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Observaciones

Consulte [IPropertyPage::Deactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) en el Windows SDK.

## <a name="ipropertypageimplgetpageinfo"></a><a name="getpageinfo"></a>IPropertyPageImpl::GetPageInfo

Rellena la estructura *pPageInfo* con información contenida en los miembros de datos.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Observaciones

`GetPageInfo`carga los recursos de cadena asociados a [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile)y [m_dwTitle](#m_dwtitle).

Vea [IPropertyPage::GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) en el Windows SDK.

## <a name="ipropertypageimplhelp"></a><a name="help"></a>IPropertyPageImpl::Ayuda

Invoca la ayuda de Windows para la página de propiedades.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Observaciones

Consulte [IPropertyPage::Help](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) en el Windows SDK.

## <a name="ipropertypageimplipropertypageimpl"></a><a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl

El constructor.

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Observaciones

Inicializa todos los miembros de datos.

## <a name="ipropertypageimplispagedirty"></a><a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty

Indica si la página de propiedades ha cambiado desde que se activó.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Observaciones

`IsPageDirty`devuelve S_OK si la página ha cambiado desde que se activó.

## <a name="ipropertypageimplm_bdirty"></a><a name="m_bdirty"></a>IPropertyPageImpl::m_bDirty

Especifica si el estado de la página de propiedades ha cambiado.

```
BOOL m_bDirty;
```

## <a name="ipropertypageimplm_nobjects"></a><a name="m_nobjects"></a>IPropertyPageImpl::m_nObjects

Almacena el número de objetos asociados a la página de propiedades.

```
ULONG m_nObjects;
```

## <a name="ipropertypageimplm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>IPropertyPageImpl::m_dwHelpContext

Almacena el identificador de contexto para el tema de ayuda asociado a la página de propiedades.

```
DWORD m_dwHelpContext;
```

## <a name="ipropertypageimplm_dwdocstring"></a><a name="m_dwdocstring"></a>IPropertyPageImpl::m_dwDocString

Almacena el identificador de recurso asociado a la cadena de texto que describe la página de propiedades.

```
UINT m_dwDocString;
```

## <a name="ipropertypageimplm_dwhelpfile"></a><a name="m_dwhelpfile"></a>IPropertyPageImpl::m_dwHelpFile

Almacena el identificador de recurso asociado con el nombre del archivo de ayuda que describe la página de propiedades.

```
UINT m_dwHelpFile;
```

## <a name="ipropertypageimplm_dwtitle"></a><a name="m_dwtitle"></a>IPropertyPageImpl::m_dwTitle

Almacena el identificador de recurso asociado a la cadena de texto que aparece en la pestaña de la página de propiedades.

```
UINT m_dwTitle;
```

## <a name="ipropertypageimplm_ppagesite"></a><a name="m_ppagesite"></a>IPropertyPageImpl::m_pPageSite

Apunta a la [interfaz IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) a través de la cual la página de propiedades se comunica con el marco de propiedades.

```
IPropertyPageSite* m_pPageSite;
```

## <a name="ipropertypageimplm_ppunk"></a><a name="m_ppunk"></a>IPropertyPageImpl::m_ppUnk

Apunta a una `IUnknown` matriz de punteros a los objetos asociados a la página de propiedades.

```
IUnknown** m_ppUnk;
```

## <a name="ipropertypageimplm_size"></a><a name="m_size"></a>IPropertyPageImpl::m_size

Almacena el alto y el ancho del cuadro de diálogo de la página de propiedades, en píxeles.

```
SIZE m_size;
```

## <a name="ipropertypageimplmove"></a><a name="move"></a>IPropertyPageImpl::Move

Coloca y cambia el tamaño del cuadro de diálogo de la página de propiedades.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Observaciones

Consulte [IPropertyPage::Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) en el Windows SDK.

## <a name="ipropertypageimplsetdirty"></a><a name="setdirty"></a>IPropertyPageImpl::SetDirty

Marca el estado de la página de propiedades como modificado o sin cambios, en función del valor de *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parámetros

*bDirty*<br/>
[en] Si es TRUE, el estado de la página de propiedades se marca como cambiado. De lo contrario, se marca como sin cambios.

### <a name="remarks"></a>Observaciones

Si es `SetDirty` necesario, informa al marco de que la página de propiedades ha cambiado.

## <a name="ipropertypageimplsetobjects"></a><a name="setobjects"></a>IPropertyPageImpl::SetObjects

Proporciona una `IUnknown` matriz de punteros para los objetos asociados a la página de propiedades.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Observaciones

Consulte [IPropertyPage::SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) en el Windows SDK.

## <a name="ipropertypageimplsetpagesite"></a><a name="setpagesite"></a>IPropertyPageImpl::SetPageSite

Proporciona la página de propiedades con un [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) puntero, a través del cual la página de propiedades se comunica con el marco de propiedad.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Observaciones

Consulte [IPropertyPage::SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) en el Windows SDK.

## <a name="ipropertypageimplshow"></a><a name="show"></a>IPropertyPageImpl::Show

Hace que el cuadro de diálogo de la página de propiedades sea visible o invisible.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Observaciones

Consulte [IPropertyPage::Show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) en el Windows SDK.

## <a name="ipropertypageimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator

Procesa la pulsación `pMsg`de tecla especificada en .

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Observaciones

Consulte [IPropertyPage::TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)<br/>
[Clase IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Clase ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
