---
title: COlePropertyPage (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6b6d011b40ebc9871baec1a1e57636499a58963
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851579"
---
# <a name="colepropertypage-class"></a>COlePropertyPage (clase)
Se utiliza para mostrar las propiedades de un control personalizado en una interfaz gráfica, similar a un cuadro de diálogo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class AFX_NOVTABLE COlePropertyPage : public CDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|Construye un objeto `COlePropertyPage`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|Indica si el usuario ha modificado el valor del control.|  
|[COlePropertyPage::GetObjectArray](#getobjectarray)|Devuelve la matriz de objetos que se está editando en la página de propiedades.|  
|[COlePropertyPage::GetPageSite](#getpagesite)|Devuelve un puntero a la página de propiedades `IPropertyPageSite` interfaz.|  
|[COlePropertyPage::IgnoreApply](#ignoreapply)|Determina qué controles no habilita el botón Aplicar.|  
|[COlePropertyPage::IsModified](#ismodified)|Indica si el usuario ha modificado la página de propiedades.|  
|[COlePropertyPage::OnEditProperty](#oneditproperty)|Lo llama el marco cuando el usuario edita una propiedad.|  
|[COlePropertyPage::OnHelp](#onhelp)|Lo llama el marco cuando el usuario pide ayuda.|  
|[COlePropertyPage::OnInitDialog](#oninitdialog)|Lo llama el marco de trabajo cuando se inicializa la página de propiedades.|  
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|Lo llama el marco de trabajo cuando se elige otro control OLE con nuevas propiedades.|  
|[COlePropertyPage:: OnSetPageSite](#onsetpagesite)|Lo llama el marco de trabajo cuando la propiedad frame proporciona el sitio de la página.|  
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|Establece una marca que indica si el usuario ha modificado el valor del control.|  
|[COlePropertyPage::SetDialogResource](#setdialogresource)|Establece el recurso de cuadro de diálogo de la página de propiedades.|  
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|Establece el texto de Ayuda breve de la página de propiedades, el nombre de su archivo de ayuda y su contexto de ayuda.|  
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|Establece una marca que indica si el usuario ha modificado la página de propiedades.|  
|[COlePropertyPage::SetPageName](#setpagename)|Establece el nombre de la página de propiedades (título).|  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, una página de propiedades puede incluir un control de edición que permite al usuario ver y modificar la propiedad caption del control.  
  
 Cada propiedad de control estándar o personalizado puede tener un control de cuadro de diálogo que permite que el usuario del control ver el valor de propiedad actuales y modificar ese valor si es necesario.  
  
 Para obtener más información sobre el uso de `COlePropertyPage`, consulte el artículo [controles ActiveX: páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `COlePropertyPage`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="colepropertypage"></a>  COlePropertyPage::COlePropertyPage  
 Construye un objeto `COlePropertyPage`.  
  
```  
COlePropertyPage(
    UINT idDlg,  
    UINT idCaption);
```  
  
### <a name="parameters"></a>Parámetros  
 *idDlg*  
 Identificador de recurso de la plantilla de cuadro de diálogo.  
  
 *idCaption*  
 Identificador de recurso de la leyenda de la página de propiedades.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se implementa una subclase de `COlePropertyPage`, debe usar el constructor de la subclase el `COlePropertyPage` constructor para identificar el recurso de plantilla de cuadro de diálogo en que se basa la página de propiedades y el recurso de cadena que contiene la leyenda.  
  
##  <a name="getcontrolstatus"></a>  COlePropertyPage::GetControlStatus  
 Determina si el usuario ha modificado el valor del control de página de propiedades con el identificador de recurso especificado.  
  
```  
BOOL GetControlStatus(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *nID*  
 Identificador de recurso de un control de página de propiedades.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se ha modificado el valor del control; en caso contrario, FALSE.  
  
##  <a name="getobjectarray"></a>  COlePropertyPage::GetObjectArray  
 Devuelve la matriz de objetos que se está editando en la página de propiedades.  
  
```  
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```  
  
### <a name="parameters"></a>Parámetros  
 *pnObjects*  
 Puntero a un entero largo sin signo que se va a recibir el número de objetos que se está editando la página.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una matriz de `IDispatch` punteros, que se usan para tener acceso a las propiedades de cada control en la página de propiedades. El llamador no debe liberar estos punteros de interfaz.  
  
### <a name="remarks"></a>Comentarios  
 Cada objeto de la página de propiedad mantiene una matriz de punteros a la `IDispatch` interfaces de los objetos que se está editando la página. Esta función establece su *pnObjects* argumento para el número de elementos de la matriz y devuelve un puntero al primer elemento de la matriz.  
  
##  <a name="getpagesite"></a>  COlePropertyPage::GetPageSite  
 Obtiene un puntero a la página de propiedades `IPropertyPageSite` interfaz.  
  
```  
LPPROPERTYPAGESITE GetPageSite();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la página de propiedades `IPropertyPageSite` interfaz.  
  
### <a name="remarks"></a>Comentarios  
 Los controles y los contenedores cooperan para que los usuarios pueden examinar y editar las propiedades del control. El control proporciona páginas de propiedades, cada uno de los cuales es un objeto OLE que permite al usuario editar un conjunto de propiedades relacionadas. El contenedor proporciona un marco de propiedades que muestra las páginas de propiedades. Para cada página, la propiedad frame proporciona un sitio de la página, que es compatible con la `IPropertyPageSite` interfaz.  
  
##  <a name="ignoreapply"></a>  COlePropertyPage::IgnoreApply  
 Determina qué controles no habilita el botón Aplicar.  
  
```  
void IgnoreApply(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *nID*  
 Identificador del control se pasará por alto.  
  
### <a name="remarks"></a>Comentarios  
 Botón Aplicar de la página de propiedades está habilitada sólo cuando se han cambiado los valores de los controles de página de propiedad. Use esta función para especificar los controles que hacen que el botón Aplicar habilitarse cuando cambian sus valores.  
  
##  <a name="ismodified"></a>  COlePropertyPage::IsModified  
 Determina si el usuario ha cambiado los valores en la página de propiedades.  
  
```  
BOOL IsModified();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se ha modificado la página de propiedades.  
  
##  <a name="oneditproperty"></a>  COlePropertyPage::OnEditProperty  
 El marco de trabajo llama a esta función cuando es una propiedad específica para editarla.  
  
```  
virtual BOOL OnEditProperty(DISPID dispid);
```  
  
### <a name="parameters"></a>Parámetros  
 *DISPID*  
 Identificador de envío de la propiedad que se está edita.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve FALSE. Invalidaciones de esta función deben devolver TRUE.  
  
### <a name="remarks"></a>Comentarios  
 Se puede reemplazar para establecer el foco en el control adecuado en la página. La implementación predeterminada no hace nada y devuelve FALSE.  
  
##  <a name="onhelp"></a>  COlePropertyPage::OnHelp  
 El marco de trabajo llama a esta función cuando el usuario solicita ayuda en línea.  
  
```  
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszHelpDir*  
 Directorio que contiene el archivo de Ayuda de la página de propiedades.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Reemplácelo si su página de propiedades debe realizar alguna acción especial cuando el usuario tiene acceso a la Ayuda. La implementación predeterminada no hace nada y devuelve FALSE, lo que indica el marco de trabajo para llamar a WinHelp.  
  
##  <a name="oninitdialog"></a>  COlePropertyPage::OnInitDialog  
 El marco de trabajo llama a esta función cuando se inicializa el cuadro de diálogo de la página de propiedades.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Reemplácelo si se requiere ninguna acción especial cuando se inicializa el cuadro de diálogo. La implementación predeterminada llama `CDialog::OnInitDialog` y devuelve FALSE.  
  
##  <a name="onobjectschanged"></a>  COlePropertyPage::OnObjectsChanged  
 Lo llama el marco de trabajo cuando se elige otro control OLE con nuevas propiedades.  
  
```  
virtual void OnObjectsChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 Al ver las propiedades de un control OLE en el entorno del desarrollador, un cuadro de diálogo no modal se utiliza para mostrar sus páginas de propiedades. Si se selecciona otro control, debe mostrarse un conjunto diferente de páginas de propiedades para el nuevo conjunto de propiedades. El marco de trabajo llama a esta función para notificar a la página de propiedades del cambio.  
  
 Reemplace esta función para recibir una notificación de esta acción y realizar ninguna acción especial.  
  
##  <a name="onsetpagesite"></a>  COlePropertyPage:: OnSetPageSite  
 El marco de trabajo llama a esta función cuando la propiedad frame proporciona el sitio de la página de la página de propiedades.  
  
```  
virtual void OnSetPageSite();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada carga el título de la página y se intenta determinar el tamaño de la página desde el recurso de cuadro de diálogo. Reemplace esta función si la página de propiedad requiere ninguna acción; la invalidación debe llamar a la implementación de la clase base.  
  
##  <a name="setcontrolstatus"></a>  COlePropertyPage::SetControlStatus  
 Cambia el estado de un control de página de propiedades.  
  
```  
BOOL SetControlStatus(
    UINT nID,  
    BOOL bDirty);
```  
  
### <a name="parameters"></a>Parámetros  
 *nID*  
 Contiene el identificador de un control de página de propiedades.  
  
 *bDirty*  
 Especifica si se ha modificado un campo de la página de propiedades. Se establece en TRUE si el campo se ha modificado, FALSE si no se ha modificado.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se ha establecido el control especificado; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Si el estado de un control de página de propiedades está desfasado, cuando se cierra la página de propiedades o se elige el botón Aplicar, se actualizará la propiedad del control con el valor adecuado.  
  
##  <a name="setdialogresource"></a>  COlePropertyPage::SetDialogResource  
 Establece el recurso de cuadro de diálogo de la página de propiedades.  
  
```  
void SetDialogResource(HGLOBAL hDialog);
```  
  
### <a name="parameters"></a>Parámetros  
 *hDialog*  
 Identificador de recurso de cuadro de diálogo de la página de propiedades.  
  
##  <a name="sethelpinfo"></a>  COlePropertyPage::SetHelpInfo  
 Especifica información sobre herramientas, el nombre de archivo de ayuda y el contexto de ayuda para la página de propiedades.  
  
```  
void SetHelpInfo(
    LPCTSTR lpszDocString,  
    LPCTSTR lpszHelpFile = NULL,  
    DWORD dwHelpContext = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszDocString*  
 Una cadena que contiene información de Ayuda breve para su presentación en una barra de estado o en otra ubicación.  
  
 *lpszHelpFile*  
 Nombre del archivo de Ayuda de la página de propiedades.  
  
 *dwHelpContext*  
 Contexto de ayuda para la página de propiedades.  
  
##  <a name="setmodifiedflag"></a>  COlePropertyPage::SetModifiedFlag  
 Indica si el usuario ha modificado la página de propiedades.  
  
```  
void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bModified*  
 Especifica el nuevo valor de marca de la página de la propiedad modificada.  
  
##  <a name="setpagename"></a>  COlePropertyPage::SetPageName  
 Establece el nombre de la página de propiedades, que normalmente se mostrará el marco de propiedad en la pestaña de la página.  
  
```  
void SetPageName(LPCTSTR lpszPageName);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszPageName*  
 Puntero a una cadena que contiene el nombre de la página de propiedades.  
  
## <a name="see-also"></a>Vea también  
 [MFC ejemplo CIRC3](../../visual-cpp-samples.md)   
 [Ejemplo de MFC TESTHELP](../../visual-cpp-samples.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)
