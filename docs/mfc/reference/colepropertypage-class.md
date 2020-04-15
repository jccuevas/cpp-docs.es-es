---
title: COlePropertyPage (clase)
ms.date: 11/04/2016
f1_keywords:
- COlePropertyPage
- AFXCTL/COlePropertyPage
- AFXCTL/COlePropertyPage::COlePropertyPage
- AFXCTL/COlePropertyPage::GetControlStatus
- AFXCTL/COlePropertyPage::GetObjectArray
- AFXCTL/COlePropertyPage::GetPageSite
- AFXCTL/COlePropertyPage::OVERWRITEApply
- AFXCTL/COlePropertyPage::IsModified
- AFXCTL/COlePropertyPage::OnEditProperty
- AFXCTL/COlePropertyPage::OnHelp
- AFXCTL/COlePropertyPage::OnInitDialog
- AFXCTL/COlePropertyPage::OnObjectsChanged
- AFXCTL/COlePropertyPage::OnSetPageSite
- AFXCTL/COlePropertyPage::SetControlStatus
- AFXCTL/COlePropertyPage::SetDialogResource
- AFXCTL/COlePropertyPage::SetHelpInfo
- AFXCTL/COlePropertyPage::SetModifiedFlag
- AFXCTL/COlePropertyPage::SetPageName
helpviewer_keywords:
- COlePropertyPage [MFC], COlePropertyPage
- COlePropertyPage [MFC], GetControlStatus
- COlePropertyPage [MFC], GetObjectArray
- COlePropertyPage [MFC], GetPageSite
- COlePropertyPage [MFC], IgnoreApply
- COlePropertyPage [MFC], IsModified
- COlePropertyPage [MFC], OnEditProperty
- COlePropertyPage [MFC], OnHelp
- COlePropertyPage [MFC], OnInitDialog
- COlePropertyPage [MFC], OnObjectsChanged
- COlePropertyPage [MFC], OnSetPageSite
- COlePropertyPage [MFC], SetControlStatus
- COlePropertyPage [MFC], SetDialogResource
- COlePropertyPage [MFC], SetHelpInfo
- COlePropertyPage [MFC], SetModifiedFlag
- COlePropertyPage [MFC], SetPageName
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
ms.openlocfilehash: dbdc889e244b33365756bcbae5b37cf657a6d900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374875"
---
# <a name="colepropertypage-class"></a>COlePropertyPage (clase)

Se utiliza para mostrar las propiedades de un control personalizado en una interfaz gráfica, similar a un cuadro de diálogo.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|Construye un objeto `COlePropertyPage`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|Indica si el usuario ha modificado el valor en el control.|
|[COlePropertyPage::GetObjectArray](#getobjectarray)|Devuelve la matriz de objetos que está editando la página de propiedades.|
|[COlePropertyPage::GetPageSite](#getpagesite)|Devuelve un puntero a la `IPropertyPageSite` interfaz de la página de propiedades.|
|[COlePropertyPage::IgnoreApply](#ignoreapply)|Determina qué controles no habilitan el botón Aplicar.|
|[COlePropertyPage::IsModified](#ismodified)|Indica si el usuario ha modificado la página de propiedades.|
|[COlePropertyPage::OnEditProperty](#oneditproperty)|Llamado por el marco de trabajo cuando el usuario edita una propiedad.|
|[COlePropertyPage::OnHelp](#onhelp)|Llamado por el marco de trabajo cuando el usuario invoca help.|
|[COlePropertyPage::OnInitDialog](#oninitdialog)|Llamado por el marco de trabajo cuando se inicializa la página de propiedades.|
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|Llamado por el marco de trabajo cuando se elige otro control OLE, con nuevas propiedades.|
|[COlePropertyPage::OnSetPageSite](#onsetpagesite)|Llamado por el marco de trabajo cuando el marco de propiedad proporciona el sitio de la página.|
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|Establece un indicador que indica si el usuario ha modificado el valor en el control.|
|[COlePropertyPage::SetDialogResource](#setdialogresource)|Establece el recurso de cuadro de diálogo de la página de propiedades.|
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|Establece el breve texto de ayuda de la página de propiedades, el nombre de su archivo de ayuda y su contexto de ayuda.|
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|Establece una marca que indica si el usuario ha modificado la página de propiedades.|
|[COlePropertyPage::SetPageName](#setpagename)|Establece el nombre de la página de propiedades (título).|

## <a name="remarks"></a>Observaciones

Por ejemplo, una página de propiedades puede incluir un control de edición que permite al usuario ver y modificar la propiedad de título del control.

Cada propiedad de control personalizado o de stock puede tener un control de cuadro de diálogo que permite al usuario del control ver el valor de propiedad actual y modificar ese valor si es necesario.

Para obtener más `COlePropertyPage`información sobre el uso , vea el artículo [Controles ActiveX: Páginas](../../mfc/mfc-activex-controls-property-pages.md)de propiedades .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="colepropertypagecolepropertypage"></a><a name="colepropertypage"></a>COlePropertyPage::COlePropertyPage

Construye un objeto `COlePropertyPage`.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Parámetros

*idDlg*<br/>
Identificador de recurso de la plantilla de cuadro de diálogo.

*idCaption*<br/>
Identificador de recurso del título de la página de propiedades.

### <a name="remarks"></a>Observaciones

Al implementar una subclase de `COlePropertyPage`, el constructor `COlePropertyPage` de la subclase debe usar el constructor para identificar el recurso de plantilla de cuadro de diálogo en el que se basa la página de propiedades y el recurso de cadena que contiene su título.

## <a name="colepropertypagegetcontrolstatus"></a><a name="getcontrolstatus"></a>COlePropertyPage::GetControlStatus

Determina si el usuario ha modificado el valor del control de página de propiedades con el identificador de recurso especificado.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador de recurso de un control de página de propiedades.

### <a name="return-value"></a>Valor devuelto

TRUESi se ha modificado el valor del control; de lo contrario FALSO.

## <a name="colepropertypagegetobjectarray"></a><a name="getobjectarray"></a>COlePropertyPage::GetObjectArray

Devuelve la matriz de objetos que está editando la página de propiedades.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Parámetros

*pnObjects*<br/>
Puntero a un entero largo sin signo que recibirá el número de objetos que está editando la página.

### <a name="return-value"></a>Valor devuelto

Puntero a una `IDispatch` matriz de punteros, que se usan para tener acceso a las propiedades de cada control en la página de propiedades. El autor de la llamada no debe liberar estos punteros de interfaz.

### <a name="remarks"></a>Observaciones

Cada objeto de página de propiedades mantiene `IDispatch` una matriz de punteros a las interfaces de los objetos que está editando la página. Esta función establece su argumento *pnObjects* en el número de elementos de esa matriz y devuelve un puntero al primer elemento de la matriz.

## <a name="colepropertypagegetpagesite"></a><a name="getpagesite"></a>COlePropertyPage::GetPageSite

Obtiene un puntero a la `IPropertyPageSite` interfaz de la página de propiedades.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la `IPropertyPageSite` interfaz de la página de propiedades.

### <a name="remarks"></a>Observaciones

Los controles y contenedores cooperan para que los usuarios puedan examinar y editar las propiedades de control. El control proporciona páginas de propiedades, cada una de las cuales es un objeto OLE que permite al usuario editar un conjunto relacionado de propiedades. El contenedor proporciona un marco de propiedades que muestra las páginas de propiedades. Para cada página, el marco de propiedades `IPropertyPageSite` proporciona un sitio de página, que admite la interfaz.

## <a name="colepropertypageignoreapply"></a><a name="ignoreapply"></a>COlePropertyPage::IgnoreApply

Determina qué controles no habilitan el botón Aplicar.

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
ID del control que se va a omitir.

### <a name="remarks"></a>Observaciones

El botón Aplicar de la página de propiedades solo está habilitado cuando se han cambiado los valores de los controles de página de propiedades. Utilice esta función para especificar controles que no hacen que el botón Aplicar se habilite cuando cambien sus valores.

## <a name="colepropertypageismodified"></a><a name="ismodified"></a>COlePropertyPage::IsModified

Determina si el usuario ha cambiado los valores de la página de propiedades.

```
BOOL IsModified();
```

### <a name="return-value"></a>Valor devuelto

TRUESi se ha modificado la página de propiedades.

## <a name="colepropertypageoneditproperty"></a><a name="oneditproperty"></a>COlePropertyPage::OnEditProperty

El marco de trabajo llama a esta función cuando se va a editar una propiedad específica.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
ID de envío de la propiedad que se está editando.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve FALSE. Las invalidaciones de esta función deben devolver TRUE.

### <a name="remarks"></a>Observaciones

Puede invalidarlo para establecer el foco en el control adecuado en la página. La implementación predeterminada no hace nada y devuelve FALSE.

## <a name="colepropertypageonhelp"></a><a name="onhelp"></a>COlePropertyPage::OnHelp

El marco de trabajo llama a esta función cuando el usuario solicita ayuda en línea.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Parámetros

*lpszHelpDir*<br/>
Directorio que contiene el archivo de ayuda de la página de propiedades.

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve FALSE.

### <a name="remarks"></a>Observaciones

Invalide si la página de propiedades debe realizar cualquier acción especial cuando el usuario tiene acceso a la ayuda. La implementación predeterminada no hace nada y devuelve FALSE, que indica al marco de trabajo que llame a WinHelp.

## <a name="colepropertypageoninitdialog"></a><a name="oninitdialog"></a>COlePropertyPage::OnInitDialog

El marco de trabajo llama a esta función cuando se inicializa el cuadro de diálogo de la página de propiedades.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve FALSE.

### <a name="remarks"></a>Observaciones

Invalide si se requiere alguna acción especial cuando se inicializa el cuadro de diálogo. La implementación `CDialog::OnInitDialog` predeterminada llama y devuelve FALSE.

## <a name="colepropertypageonobjectschanged"></a><a name="onobjectschanged"></a>COlePropertyPage::OnObjectsChanged

Llamado por el marco de trabajo cuando se elige otro control OLE, con nuevas propiedades.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Observaciones

Al ver las propiedades de un control OLE en el entorno de desarrollador, se usa un cuadro de diálogo no adecuado para mostrar sus páginas de propiedades. Si se selecciona otro control, se debe mostrar un conjunto diferente de páginas de propiedades para el nuevo conjunto de propiedades. El marco de trabajo llama a esta función para notificar a la página de propiedades del cambio.

Reemplace esta función para recibir una notificación de esta acción y realizar cualquier acción especial.

## <a name="colepropertypageonsetpagesite"></a><a name="onsetpagesite"></a>COlePropertyPage::OnSetPageSite

El marco de trabajo llama a esta función cuando el marco de propiedades proporciona el sitio de página de la página de propiedades.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada carga el título de la página e intenta determinar el tamaño de la página desde el recurso de cuadro de diálogo. Invalide esta función si la página de propiedades requiere cualquier acción adicional; la invalidación debe llamar a la implementación de clase base.

## <a name="colepropertypagesetcontrolstatus"></a><a name="setcontrolstatus"></a>COlePropertyPage::SetControlStatus

Cambia el estado de un control de página de propiedades.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Contiene el identificador de un control de página de propiedades.

*bDirty*<br/>
Especifica si se ha modificado un campo de la página de propiedades. Se establece en TRUE si el campo se ha modificado, FALSE si no se ha modificado.

### <a name="return-value"></a>Valor devuelto

TRUE, si se estableció el control especificado; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Si el estado de un control de página de propiedades está sucio cuando se cierra la página de propiedades o se elige el botón Aplicar, la propiedad del control se actualizará con el valor adecuado.

## <a name="colepropertypagesetdialogresource"></a><a name="setdialogresource"></a>COlePropertyPage::SetDialogResource

Establece el recurso de cuadro de diálogo de la página de propiedades.

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Parámetros

*hDialog*<br/>
Controlar el recurso de cuadro de diálogo de la página de propiedades.

## <a name="colepropertypagesethelpinfo"></a><a name="sethelpinfo"></a>COlePropertyPage::SetHelpInfo

Especifica información sobre información sobre herramientas, el nombre de archivo de ayuda y el contexto de ayuda de la página de propiedades.

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Parámetros

*lpszDocString*<br/>
Cadena que contiene información de ayuda breve para mostrar en una barra de estado u otra ubicación.

*lpszHelpFile*<br/>
Nombre del archivo de ayuda de la página de propiedades.

*dwHelpContext*<br/>
Contexto de ayuda para la página de propiedades.

## <a name="colepropertypagesetmodifiedflag"></a><a name="setmodifiedflag"></a>COlePropertyPage::SetModifiedFlag

Indica si el usuario ha modificado la página de propiedades.

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parámetros

*bModificado*<br/>
Especifica el nuevo valor para la marca modificada de la página de propiedades.

## <a name="colepropertypagesetpagename"></a><a name="setpagename"></a>COlePropertyPage::SetPageName

Establece el nombre de la página de propiedades, que el marco de propiedades normalmente se mostrará en la pestaña de la página.

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Parámetros

*lpszPageName*<br/>
Puntero a una cadena que contiene el nombre de la página de propiedades.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CIRC3](../../overview/visual-cpp-samples.md)<br/>
[PRUEBA DE MUESTRA DE MFC](../../overview/visual-cpp-samples.md)<br/>
[Clase CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDialog](../../mfc/reference/cdialog-class.md)
