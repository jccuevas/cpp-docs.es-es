---
title: IPropertyPageImpl (clase)
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
ms.openlocfilehash: 69842e77aecaa94be66432e5fbba437a6fa3c5a4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423073"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl (clase)

Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la interfaz [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) .

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IPropertyPageImpl`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPropertyPageImpl:: IPropertyPageImpl](#ipropertypageimpl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPropertyPageImpl:: Activate](#activate)|Crea la ventana de cuadro de diálogo para la página de propiedades.|
|[IPropertyPageImpl:: Apply](#apply)|Aplica los valores actuales de la página de propiedades a los objetos subyacentes especificados a través de `SetObjects`. La implementación de ATL Devuelve S_OK.|
|[IPropertyPageImpl::D eactivate](#deactivate)|Destruye la ventana creada con `Activate`.|
|[IPropertyPageImpl:: GetPageInfo](#getpageinfo)|Recupera información sobre la página de propiedades.|
|[IPropertyPageImpl:: help](#help)|Invoca la ayuda de Windows para la página de propiedades.|
|[IPropertyPageImpl:: IsPageDirty](#ispagedirty)|Indica si la página de propiedades ha cambiado desde que se activó.|
|[IPropertyPageImpl:: Move](#move)|Coloca y cambia el tamaño del cuadro de diálogo Página de propiedades.|
|[IPropertyPageImpl:: SetDirty](#setdirty)|Marca el estado de la página de propiedades como cambiado o sin modificar.|
|[IPropertyPageImpl:: SetObjects](#setobjects)|Proporciona una matriz de punteros de `IUnknown` para los objetos asociados a la página de propiedades. Estos objetos reciben los valores actuales de la página de propiedades a través de una llamada a `Apply`.|
|[IPropertyPageImpl:: SetPageSite](#setpagesite)|Proporciona la página de propiedades con un puntero `IPropertyPageSite`, a través del cual la página de propiedades se comunica con el marco de propiedad.|
|[IPropertyPageImpl:: show](#show)|Hace que el cuadro de diálogo de la página de propiedades sea visible o invisible.|
|[IPropertyPageImpl:: TranslateAccelerator](#translateaccelerator)|Procesa una pulsación de tecla especificada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPropertyPageImpl:: m_bDirty](#m_bdirty)|Especifica si el estado de la página de propiedades ha cambiado.|
|[IPropertyPageImpl:: m_dwDocString](#m_dwdocstring)|Almacena el identificador de recursos asociado a la cadena de texto que describe la página de propiedades.|
|[IPropertyPageImpl:: m_dwHelpContext](#m_dwhelpcontext)|Almacena el identificador de contexto para el tema de ayuda asociado a la página de propiedades.|
|[IPropertyPageImpl:: m_dwHelpFile](#m_dwhelpfile)|Almacena el identificador de recurso asociado al nombre del archivo de ayuda que describe la página de propiedades.|
|[IPropertyPageImpl:: m_dwTitle](#m_dwtitle)|Almacena el identificador de recursos asociado a la cadena de texto que aparece en la pestaña de la página de propiedades.|
|[IPropertyPageImpl:: m_nObjects](#m_nobjects)|Almacena el número de objetos asociados a la página de propiedades.|
|[IPropertyPageImpl:: m_pPageSite](#m_ppagesite)|Apunta a la interfaz `IPropertyPageSite` a través de la cual la página de propiedades se comunica con el marco de propiedad.|
|[IPropertyPageImpl:: m_ppUnk](#m_ppunk)|Apunta a una matriz de `IUnknown` punteros a los objetos asociados a la página de propiedades.|
|[IPropertyPageImpl:: m_size](#m_size)|Almacena el alto y el ancho del cuadro de diálogo de la página de propiedades, en píxeles.|

## <a name="remarks"></a>Observaciones

La interfaz [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) permite a un objeto administrar una determinada página de propiedades dentro de una hoja de propiedades. La clase `IPropertyPageImpl` proporciona una implementación predeterminada de esta interfaz e implementa `IUnknown` enviando información al dispositivo de volcado en las compilaciones de depuración.

**Artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="activate"></a>IPropertyPageImpl:: Activate

Crea la ventana de cuadro de diálogo para la página de propiedades.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, el cuadro de diálogo siempre es no modal, independientemente del valor del parámetro *bModal* .

Vea [IPropertyPage:: Activate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) en el Windows SDK.

##  <a name="apply"></a>IPropertyPageImpl:: Apply

Aplica los valores actuales de la página de propiedades a los objetos subyacentes especificados a través de `SetObjects`.

```
HRESULT Apply();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Vea [IPropertyPage:: Apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) en el Windows SDK.

##  <a name="deactivate"></a>IPropertyPageImpl::D eactivate

Destruye la ventana de cuadro de diálogo creada con [Activar](#activate).

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Observaciones

Vea [IPropertyPage::D eactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) en el Windows SDK.

##  <a name="getpageinfo"></a>IPropertyPageImpl:: GetPageInfo

Rellena la estructura *pPageInfo* con información contenida en los miembros de datos.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Observaciones

`GetPageInfo` carga los recursos de cadena asociados a [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile)y [m_dwTitle](#m_dwtitle).

Vea [IPropertyPage:: GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) en el Windows SDK.

##  <a name="help"></a>IPropertyPageImpl:: help

Invoca la ayuda de Windows para la página de propiedades.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Observaciones

Vea [IPropertyPage:: help](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) en el Windows SDK.

##  <a name="ipropertypageimpl"></a>IPropertyPageImpl:: IPropertyPageImpl

El constructor.

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Observaciones

Inicializa todos los miembros de datos.

##  <a name="ispagedirty"></a>IPropertyPageImpl:: IsPageDirty

Indica si la página de propiedades ha cambiado desde que se activó.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Observaciones

`IsPageDirty` Devuelve S_OK si la página ha cambiado desde que se activó.

##  <a name="m_bdirty"></a>IPropertyPageImpl:: m_bDirty

Especifica si el estado de la página de propiedades ha cambiado.

```
BOOL m_bDirty;
```

##  <a name="m_nobjects"></a>IPropertyPageImpl:: m_nObjects

Almacena el número de objetos asociados a la página de propiedades.

```
ULONG m_nObjects;
```

##  <a name="m_dwhelpcontext"></a>IPropertyPageImpl:: m_dwHelpContext

Almacena el identificador de contexto para el tema de ayuda asociado a la página de propiedades.

```
DWORD m_dwHelpContext;
```

##  <a name="m_dwdocstring"></a>IPropertyPageImpl:: m_dwDocString

Almacena el identificador de recursos asociado a la cadena de texto que describe la página de propiedades.

```
UINT m_dwDocString;
```

##  <a name="m_dwhelpfile"></a>IPropertyPageImpl:: m_dwHelpFile

Almacena el identificador de recurso asociado al nombre del archivo de ayuda que describe la página de propiedades.

```
UINT m_dwHelpFile;
```

##  <a name="m_dwtitle"></a>IPropertyPageImpl:: m_dwTitle

Almacena el identificador de recursos asociado a la cadena de texto que aparece en la pestaña de la página de propiedades.

```
UINT m_dwTitle;
```

##  <a name="m_ppagesite"></a>IPropertyPageImpl:: m_pPageSite

Apunta a la interfaz [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) a través de la cual la página de propiedades se comunica con el marco de propiedad.

```
IPropertyPageSite* m_pPageSite;
```

##  <a name="m_ppunk"></a>IPropertyPageImpl:: m_ppUnk

Apunta a una matriz de `IUnknown` punteros a los objetos asociados a la página de propiedades.

```
IUnknown** m_ppUnk;
```

##  <a name="m_size"></a>IPropertyPageImpl:: m_size

Almacena el alto y el ancho del cuadro de diálogo de la página de propiedades, en píxeles.

```
SIZE m_size;
```

##  <a name="move"></a>IPropertyPageImpl:: Move

Coloca y cambia el tamaño del cuadro de diálogo Página de propiedades.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Observaciones

Vea [IPropertyPage:: Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) en el Windows SDK.

##  <a name="setdirty"></a>IPropertyPageImpl:: SetDirty

Marca el estado de la página de propiedades como cambiado o sin modificar, dependiendo del valor de *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parámetros

*bDirty*<br/>
de Si es TRUE, el estado de la página de propiedades se marca como modificado. De lo contrario, se marca como sin cambios.

### <a name="remarks"></a>Observaciones

Si es necesario, `SetDirty` informa al marco de que la página de propiedades ha cambiado.

##  <a name="setobjects"></a>IPropertyPageImpl:: SetObjects

Proporciona una matriz de punteros de `IUnknown` para los objetos asociados a la página de propiedades.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Observaciones

Vea [IPropertyPage:: SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) en el Windows SDK.

##  <a name="setpagesite"></a>IPropertyPageImpl:: SetPageSite

Proporciona la página de propiedades con un puntero [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) , a través del cual la página de propiedades se comunica con el marco de propiedad.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Observaciones

Vea [IPropertyPage:: SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) en el Windows SDK.

##  <a name="show"></a>IPropertyPageImpl:: show

Hace que el cuadro de diálogo de la página de propiedades sea visible o invisible.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Observaciones

Vea [IPropertyPage:: show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) en el Windows SDK.

##  <a name="translateaccelerator"></a>IPropertyPageImpl:: TranslateAccelerator

Procesa la pulsación de tecla especificada en `pMsg`.

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Observaciones

Vea [IPropertyPage:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[IPropertyPage2Impl (clase)](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl (clase)](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl (clase)](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
