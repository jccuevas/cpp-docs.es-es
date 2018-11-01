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
ms.openlocfilehash: bf97699917732f8ce94d1541b6a93e00325b28c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605821"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl (clase)

Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) interfaz.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IPropertyPageImpl`.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IPropertyPageImpl](#activate)|Crea la ventana del cuadro de diálogo para la página de propiedades.|
|[IPropertyPageImpl:: Apply](#apply)|Se aplica a valores de la página de propiedad actuales para los objetos subyacentes especificados a través de `SetObjects`. La implementación de ATL devuelve S_OK.|
|[IPropertyPageImpl::Deactivate](#deactivate)|Destruye la ventana creada con `Activate`.|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Recupera información acerca de la página de propiedades.|
|[IPropertyPageImpl::Help](#help)|Invoca la Ayuda de Windows para la página de propiedades.|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Indica si la página de propiedad ha cambiado desde que se activó.|
|[IPropertyPageImpl::Move](#move)|Coloca y cambia el tamaño del cuadro de diálogo de la página de propiedades.|
|[IPropertyPageImpl:: SetDirty](#setdirty)|Marcas de estado de la página de propiedad como modificada o sin cambios.|
|[SetObjects](#setobjects)|Proporciona una matriz de `IUnknown` punteros para los objetos asociados a la página de propiedades. Estos objetos reciben los valores de página de propiedad actual a través de una llamada a `Apply`.|
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Proporciona la página de propiedades con un `IPropertyPageSite` puntero, a través del cual la página de propiedades se comunica con el marco de propiedad.|
|[IPropertyPageImpl::Show](#show)|Hace que el cuadro de diálogo página de propiedad visible o invisible.|
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Procesa una pulsación de tecla especificada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Especifica si el estado de la página de propiedad ha cambiado.|
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Almacena el identificador de recurso asociado con la cadena de texto que describe la página de propiedades.|
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Almacena el identificador de contexto para el tema de ayuda asociado a la página de propiedades.|
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Almacena el identificador de recurso asociado con el nombre del archivo de ayuda que describe la página de propiedades.|
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Almacena el identificador de recurso asociado con la cadena de texto que aparece en la pestaña de la página de propiedades.|
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Almacena el número de objetos asociados a la página de propiedades.|
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Apunta a la `IPropertyPageSite` interfaz a través del cual la página de propiedades se comunica con el marco de propiedad.|
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Señala a una matriz de `IUnknown` punteros a los objetos asociados a la página de propiedades.|
|[IPropertyPageImpl::m_size](#m_size)|Almacena el alto y ancho de la página de propiedades cuadro de diálogo, en píxeles.|

## <a name="remarks"></a>Comentarios

El [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) interfaz permite que un objeto administrar una determinada página de propiedades dentro de una hoja de propiedades. Clase `IPropertyPageImpl` proporciona una implementación predeterminada de esta interfaz e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="activate"></a>  IPropertyPageImpl

Crea la ventana del cuadro de diálogo para la página de propiedades.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, el cuadro de diálogo siempre es no modal, independientemente del valor de la *bModal* parámetro.

Consulte [IPropertyPage::Activate](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-activate) en el SDK de Windows.

##  <a name="apply"></a>  IPropertyPageImpl:: Apply

Se aplica a valores de la página de propiedad actuales para los objetos subyacentes especificados a través de `SetObjects`.

```
HRESULT Apply();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Consulte [IPropertyPage::Apply](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-apply) en el SDK de Windows.

##  <a name="deactivate"></a>  IPropertyPageImpl::Deactivate

Destruye la ventana del cuadro de diálogo creada con [activar](#activate).

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Comentarios

Consulte [IPropertyPage::Deactivate](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-deactivate) en el SDK de Windows.

##  <a name="getpageinfo"></a>  IPropertyPageImpl::GetPageInfo

Rellena el *pPageInfo* estructura con la información contenida en los miembros de datos.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Comentarios

`GetPageInfo` carga los recursos de cadena asociados [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile), y [m_dwTitle](#m_dwtitle).

Consulte [IPropertyPage:: GetPageInfo](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) en el SDK de Windows.

##  <a name="help"></a>  IPropertyPageImpl::Help

Invoca la Ayuda de Windows para la página de propiedades.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Comentarios

Consulte [IPropertyPage::Help](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-help) en el SDK de Windows.

##  <a name="ipropertypageimpl"></a>  IPropertyPageImpl::IPropertyPageImpl

El constructor.

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Comentarios

Inicializa a todos los miembros de datos.

##  <a name="ispagedirty"></a>  IPropertyPageImpl::IsPageDirty

Indica si la página de propiedad ha cambiado desde que se activó.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Comentarios

`IsPageDirty` Devuelve S_OK si la página ha cambiado desde que se activó.

##  <a name="m_bdirty"></a>  IPropertyPageImpl::m_bDirty

Especifica si el estado de la página de propiedad ha cambiado.

```
BOOL m_bDirty;
```

##  <a name="m_nobjects"></a>  IPropertyPageImpl::m_nObjects

Almacena el número de objetos asociados a la página de propiedades.

```
ULONG m_nObjects;
```

##  <a name="m_dwhelpcontext"></a>  IPropertyPageImpl::m_dwHelpContext

Almacena el identificador de contexto para el tema de ayuda asociado a la página de propiedades.

```
DWORD m_dwHelpContext;
```

##  <a name="m_dwdocstring"></a>  IPropertyPageImpl::m_dwDocString

Almacena el identificador de recurso asociado con la cadena de texto que describe la página de propiedades.

```
UINT m_dwDocString;
```

##  <a name="m_dwhelpfile"></a>  IPropertyPageImpl::m_dwHelpFile

Almacena el identificador de recurso asociado con el nombre del archivo de ayuda que describe la página de propiedades.

```
UINT m_dwHelpFile;
```

##  <a name="m_dwtitle"></a>  IPropertyPageImpl::m_dwTitle

Almacena el identificador de recurso asociado con la cadena de texto que aparece en la pestaña de la página de propiedades.

```
UINT m_dwTitle;
```

##  <a name="m_ppagesite"></a>  IPropertyPageImpl::m_pPageSite

Apunta a la [IPropertyPageSite](/windows/desktop/api/ocidl/nn-ocidl-ipropertypagesite) interfaz a través del cual la página de propiedades se comunica con el marco de propiedad.

```
IPropertyPageSite* m_pPageSite;
```

##  <a name="m_ppunk"></a>  IPropertyPageImpl::m_ppUnk

Señala a una matriz de `IUnknown` punteros a los objetos asociados a la página de propiedades.

```
IUnknown** m_ppUnk;
```

##  <a name="m_size"></a>  IPropertyPageImpl::m_size

Almacena el alto y ancho de la página de propiedades cuadro de diálogo, en píxeles.

```
SIZE m_size;
```

##  <a name="move"></a>  IPropertyPageImpl::Move

Coloca y cambia el tamaño del cuadro de diálogo de la página de propiedades.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Comentarios

Consulte [IPropertyPage::Move](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-move) en el SDK de Windows.

##  <a name="setdirty"></a>  IPropertyPageImpl:: SetDirty

Marcas de estado de la página de propiedad como modificada o sin cambios, dependiendo del valor de *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parámetros

*bDirty*<br/>
[in] Si es TRUE, estado de la página de propiedad se marca como modificada. En caso contrario, se marca como sin cambios.

### <a name="remarks"></a>Comentarios

Si es necesario, `SetDirty` informa del marco que ha cambiado la página de propiedades.

##  <a name="setobjects"></a>  SetObjects

Proporciona una matriz de `IUnknown` punteros para los objetos asociados a la página de propiedades.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Comentarios

Consulte [IPropertyPage::SetObjects](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-setobjects) en el SDK de Windows.

##  <a name="setpagesite"></a>  IPropertyPageImpl::SetPageSite

Proporciona la página de propiedades con un [IPropertyPageSite](/windows/desktop/api/ocidl/nn-ocidl-ipropertypagesite) puntero, a través del cual la página de propiedades se comunica con el marco de propiedad.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Comentarios

Consulte [IPropertyPage::SetPageSite](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-setpagesite) en el SDK de Windows.

##  <a name="show"></a>  IPropertyPageImpl::Show

Hace que el cuadro de diálogo página de propiedad visible o invisible.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Comentarios

Consulte [IPropertyPage::Show](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-show) en el SDK de Windows.

##  <a name="translateaccelerator"></a>  IPropertyPageImpl::TranslateAccelerator

Procesa la pulsación de tecla especificada en `pMsg`.

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Comentarios

Consulte [IPropertyPage::TranslateAccelerator](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[IPropertyPage2Impl (clase)](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl (clase)](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl (clase)](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
