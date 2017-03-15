---
title: Clase de la clase COlePasteSpecialDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePasteSpecialDialog
dev_langs:
- C++
helpviewer_keywords:
- Paste Special dialog box
- dialog boxes, Paste Special
- OLE Paste Special dialog box
- COlePasteSpecialDialog class
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6984d714248815b062c564c7eed5c315990855af
ms.lasthandoff: 02/24/2017

---
# <a name="colepastespecialdialog-class"></a>Clase COlePasteSpecialDialog (clase)
Se utiliza en el cuadro de diálogo Pegado especial de OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COlePasteSpecialDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Construye un objeto `COlePasteSpecialDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COlePasteSpecialDialog::AddFormat](#addformat)|Formatos personalizados se agrega a la lista de formatos que puede pegar la aplicación.|  
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Agrega una nueva entrada a la lista de formatos del Portapapeles compatibles.|  
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Agrega **CF_BITMAP**, **CF_DIB**, `CF_METAFILEPICT`y, opcionalmente, `CF_LINKSOURCE` a la lista de formatos, la aplicación puede pegar.|  
|[COlePasteSpecialDialog::CreateItem](#createitem)|Crea el elemento en el documento contenedor utilizando el formato especificado.|  
|[COlePasteSpecialDialog::DoModal](#domodal)|Muestra el cuadro de diálogo OLE Pegado especial.|  
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Indica si se debe dibujar elementos como un icono o no.|  
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador para el metarchivo asociado con el formulario icónico de este elemento.|  
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Obtiene el índice de opciones de pegado disponibles que se ha elegido por el usuario.|  
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de selección elegida.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COlePasteSpecialDialog::m_ps](#m_ps)|Una estructura de tipo **OLEUIPASTESPECIAL** que controla la función del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un objeto de clase `COlePasteSpecialDialog` cuando desee llamar a este cuadro de diálogo. Después de un `COlePasteSpecialDialog` se ha construido el objeto, puede usar el [AddFormat](#addformat) y [AddStandardFormats](#addstandardformats) funciones miembro para agregar formatos de Portapapeles en el cuadro de diálogo. También puede utilizar el [m_ps](#m_ps) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_ps` estructura es de tipo **OLEUIPASTESPECIAL**.  
  
 Para obtener más información, consulte el [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre los cuadros de diálogo OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePasteSpecialDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxodlgs.h  
  
##  <a name="a-nameaddformata--colepastespecialdialogaddformat"></a><a name="addformat"></a>COlePasteSpecialDialog::AddFormat  
 Llame a esta función para agregar nuevos formatos a la lista de formatos que puede admitir la aplicación en una operación de pegado especial.  
  
```  
void AddFormat(
    const FORMATETC& formatEtc,  
    LPTSTR lpszFormat,  
    LPTSTR lpszResult,  
    DWORD flags);

 
void AddFormat(
    UINT cf,  
    DWORD tymed,  
    UINT nFormatID,  
    BOOL bEnableIcon,  
    BOOL bLink);
```  
  
### <a name="parameters"></a>Parámetros  
 *Microsoft*  
 Referencia al tipo de datos para agregar.  
  
 `lpszFormat`  
 Cadena que describe el formato para el usuario.  
  
 *lpszResult*  
 Cadena que describe el resultado si se selecciona este formato en el cuadro de diálogo.  
  
 `flags`  
 Los diferentes vincular e incrustar opciones disponibles para este formato. Este indicador es una combinación bit a bit de uno o varios de los valores diferentes en el **OLEUIPASTEFLAG** tipo enumerado.  
  
 `cf`  
 Para agregar el formato del Portapapeles.  
  
 *TYMED*  
 Los tipos de medios disponibles en este formato. Ésta es una combinación bit a bit de uno o varios de los valores de la **TYMED** tipo enumerado.  
  
 `nFormatID`  
 El identificador de la cadena que identifica este formato. El formato de esta cadena es dos cadenas independientes, separadas por un carácter '\n'. La primera cadena es el mismo que se pasará en el *lpstrFormat* parámetro y el segundo es el mismo que el *lpstrResult* parámetro.  
  
 *bEnableIcon*  
 Marca que determina si la casilla de verificación Mostrar como icono está habilitada cuando se elige este formato en el cuadro de lista.  
  
 *Intermitencia*  
 Marca que determina si está habilitado el botón Pegar vínculo cuando se elige este formato en el cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se puede llamar para agregar cualquiera de los formatos estándar, como **CF_TEXT** o **CF_TIFF** o formatos personalizados que ha registrado su aplicación con el sistema. Para obtener más información acerca de pegar los objetos de datos en su aplicación, vea el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Para obtener más información, consulte el [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) tipo de enumeración y el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información, consulte el [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) enumerado de tipo en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameaddlinkentrya--colepastespecialdialogaddlinkentry"></a><a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry  
 Agrega una nueva entrada a la lista de formatos del Portapapeles compatibles.  
  
```  
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```  
  
### <a name="parameters"></a>Parámetros  
 `cf`  
 Para agregar el formato del Portapapeles.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) estructura que contiene la información de la nueva entrada de vínculo.  
  
##  <a name="a-nameaddstandardformatsa--colepastespecialdialogaddstandardformats"></a><a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats  
 Llame a esta función para agregar los siguientes formatos de Portapapeles a la lista de formatos que puede admitir la aplicación en una operación de pegado especial:  
  
```  
void AddStandardFormats(BOOL bEnableLink = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bEnableLink*  
 Marca que determina si se debe agregar `CF_LINKSOURCE` a la lista de formatos, la aplicación puede pegar.  
  
### <a name="remarks"></a>Comentarios  
  
- **CF_BITMAP**  
  
- **CF_DIB**  
  
- `CF_METAFILEPICT`  
  
- **"Objeto incrustado"**  
  
-   (opcional) **"Vínculo de origen"**  
  
 Estos formatos se utilizan para admitir la incrustación y vinculación.  
  
##  <a name="a-namecolepastespecialdialoga--colepastespecialdialogcolepastespecialdialog"></a><a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog  
 Construye un objeto `COlePasteSpecialDialog`.  
  
```  
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,  
    COleDataObject* pDataObject = NULL,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 Indicador de creación, contiene cualquier número de los siguientes indicadores combinados mediante el operador OR bit a bit:  
  
- `PSF_SELECTPASTE`Especifica que el botón de opción de pegar se comprobará inicialmente cuando se llama el cuadro de diálogo. No se puede usar en combinación con `PSF_SELECTPASTELINK`. Este es el valor predeterminado.  
  
- `PSF_SELECTPASTELINK`Especifica que el vínculo de pegar el botón de radio estará activada inicialmente cuando se llama el cuadro de diálogo. No se puede usar en combinación con `PSF_SELECTPASTE`.  
  
- `PSF_CHECKDISPLAYASICON`Especifica que la casilla de verificación Mostrar como icono se comprobará inicialmente cuando se llama el cuadro de diálogo.  
  
- `PSF_SHOWHELP`Especifica que el botón de ayuda se mostrará cuando se llama el cuadro de diálogo.  
  
 `pDataObject`  
 Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) de pegado. Si este valor es **NULL**, obtiene el `COleDataObject` desde el Portapapeles.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Esta función sólo se crea un `COlePasteSpecialDialog` objeto. Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) (función).  
  
 Para obtener más información, consulte el [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) enumerado de tipo en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namecreateitema--colepastespecialdialogcreateitem"></a><a name="createitem"></a>COlePasteSpecialDialog::CreateItem  
 Crea el nuevo elemento que se ha elegido en el cuadro de diálogo Pegado especial.  
  
```  
BOOL CreateItem(COleClientItem* pNewItem);
```  
  
### <a name="parameters"></a>Parámetros  
 *pNewItem*  
 Apunta a un `COleClientItem` instancia. No puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el elemento se creó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo debe llamarse después de [DoModal](#domodal) devuelve **IDOK**.  
  
##  <a name="a-namedomodala--colepastespecialdialogdomodal"></a><a name="domodal"></a>COlePasteSpecialDialog::DoModal  
 Muestra el cuadro de diálogo OLE Pegado especial.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- **IDOK** si el cuadro de diálogo se muestra correctamente.  
  
- **IDCANCEL** si el usuario cancela el cuadro de diálogo.  
  
- **IDABORT** si se produjo un error. Si **IDABORT** es devuelto, llame a la `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, consulte el [OleUIPasteSpecial](http://msdn.microsoft.com/library/windows/desktop/ms694512) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la [m_ps](#m_ps) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve **IDOK**, puede llamar a otro miembro de funciones para recuperar la configuración o la entrada de información por el usuario en el cuadro de diálogo.  
  
##  <a name="a-namegetdrawaspecta--colepastespecialdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect  
 Determina si el usuario decidió mostrar el elemento seleccionado como un icono.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El método necesario para representar el objeto.  
  
- `DVASPECT_CONTENT`Devuelve si la casilla de verificación Mostrar como icono no se comprueba al descarta el cuadro de diálogo.  
  
- `DVASPECT_ICON`Devuelve si se ha activado la casilla de verificación Mostrar como icono al descarta el cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Solo llame a esta función después de [DoModal](#domodal) devuelve **IDOK**.  
  
 Para obtener más información sobre los aspectos de dibujo, consulte el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegeticonicmetafilea--colepastespecialdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile  
 Obtiene el metarchivo asociado al elemento seleccionado por el usuario.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo que contiene el aspecto de iconos del elemento seleccionado, si se ha seleccionado la casilla de verificación Mostrar como icono al descarta el cuadro de diálogo seleccionando **Aceptar**; en caso contrario **NULL**.  
  
##  <a name="a-namegetpasteindexa--colepastespecialdialoggetpasteindex"></a><a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex  
 Obtiene el valor de índice asociado a la entrada seleccionada por el usuario.  
  
```  
int GetPasteIndex() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice en la matriz de **OLEUIPASTEENTRY** estructuras que se ha seleccionado por el usuario. El formato que se corresponde con el índice seleccionado debe usarse al realizar la operación de pegado.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el [OLEUIPASTEENTRY](http://msdn.microsoft.com/library/windows/desktop/ms690165) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetselectiontypea--colepastespecialdialoggetselectiontype"></a><a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType  
 Determina el tipo de selección que realiza el usuario.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tipo de selección realizada.  
  
### <a name="remarks"></a>Comentarios  
 Especifica los valores de tipo de valor devuelto por la **selección** tipo de enumeración declarado en el `COlePasteSpecialDialog` clase.  
  
 `enum Selection`  
  
 `{`  
  
 `pasteLink,`  
  
 `pasteNormal,`  
  
 `pasteOther,`  
  
 `pasteStatic`  
  
 `};`  
  
 Siga desccriptions breves de estos valores:  
  
- **COlePasteSpecialDialog::pasteLink** botón Pegar el vínculo estaba activado y el formato elegido fue un formato estándar de OLE.  
  
- **COlePasteSpecialDialog::pasteNormal** botón Pegar el estaba activado y el formato elegido fue un formato estándar de OLE.  
  
- **COlePasteSpecialDialog::pasteOther** el formato seleccionado no es un formato estándar de OLE.  
  
- **COlePasteSpecialDialog::pasteStatic** el formato elegido no era un metarchivo.  
  
##  <a name="a-namempsa--colepastespecialdialogmps"></a><a name="m_ps"></a>COlePasteSpecialDialog::m_ps  
 Estructura de tipo **OLEUIPASTESPECIAL** utilizado para controlar el comportamiento del cuadro de diálogo Pegado especial.  
  
```  
OLEUIPASTESPECIAL m_ps;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)

