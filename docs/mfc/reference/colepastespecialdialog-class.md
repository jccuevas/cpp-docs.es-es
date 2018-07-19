---
title: COlePasteSpecialDialog (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
dev_langs:
- C++
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42f4a45dc2b49b784f74175203e892c253ea1f5e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851438"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog (clase)
Se utiliza en el cuadro de diálogo Pegado especial de OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COlePasteSpecialDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Construye un objeto `COlePasteSpecialDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePasteSpecialDialog::AddFormat](#addformat)|Formatos personalizados se agrega a la lista de formatos que puede pegar la aplicación.|  
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Agrega una nueva entrada a la lista de formatos de Portapapeles admitidos.|  
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Agrega CF_METAFILEPICT CF_BITMAP, CF_DIB, y, opcionalmente, CF_LINKSOURCE a la lista de formatos que la aplicación puede pegar.|  
|[COlePasteSpecialDialog::CreateItem](#createitem)|Crea el elemento en el documento contenedor utilizando el formato especificado.|  
|[COlePasteSpecialDialog::DoModal](#domodal)|Muestra el cuadro de diálogo OLE Pegado especial.|  
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Indica si se debe dibujar elementos como un icono o no.|  
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador del metarchivo asociado al formulario icónico de este elemento.|  
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Obtiene el índice de las opciones de pegar disponibles que se ha elegido por el usuario.|  
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de selección elegido.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePasteSpecialDialog::m_ps](#m_ps)|Una estructura de tipo OLEUIPASTESPECIAL que controla la función del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un objeto de clase `COlePasteSpecialDialog` cuando desee llamar a este cuadro de diálogo. Después de un `COlePasteSpecialDialog` se ha construido el objeto, puede usar el [AddFormat](#addformat) y [AddStandardFormats](#addstandardformats) funciones miembro para agregar los formatos del Portapapeles en el cuadro de diálogo. También puede usar el [m_ps](#m_ps) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_ps` estructura es de tipo OLEUIPASTESPECIAL.  
  
 Para obtener más información, consulte el [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) estructura en el SDK de Windows.  
  
 Para obtener más información sobre los cuadros de diálogo OLE específicos, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
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
  
##  <a name="addformat"></a>  COlePasteSpecialDialog::AddFormat  
 Llame a esta función para agregar nuevos formatos a la lista de formatos de que la aplicación puede admitir en una operación de pegado especial.  
  
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
 *FMT*  
 Referencia al tipo de datos para agregar.  
  
 *lpszFormat*  
 Cadena que describe el formato para el usuario.  
  
 *lpszResult*  
 Cadena que describe el resultado si se elige este formato en el cuadro de diálogo.  
  
 *flags*  
 Los diferentes vincular e incrustar las opciones disponibles para este formato. Este indicador es una combinación bit a bit de uno o varios de los diferentes valores en el OLEUIPASTEFLAG tipo enumeran.  
  
 *CF*  
 Para agregar el formato del Portapapeles.  
  
 *TYMED*  
 Los tipos de medios disponibles en este formato. Se trata de una combinación bit a bit de uno o varios de los valores en el TYMED tipo enumeran.  
  
 *nFormatID*  
 El identificador de la cadena que identifica este formato. El formato de esta cadena es de dos cadenas independientes separadas por un carácter '\n'. La primera cadena es el mismo que se pasaría el *lpstrFormat* parámetro y el segundo es el mismo que el *lpstrResult* parámetro.  
  
 *bEnableIcon*  
 Marca que determina si la casilla de verificación Mostrar como icono está habilitada cuando se elige este formato en el cuadro de lista.  
  
 *Intermitencia*  
 Marca que determina si el botón de radio Pegar vínculo está habilitado cuando se elige este formato en el cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se puede llamar para agregar tanto estándares como CF_TEXT o CF_TIFF o formatos formatos personalizados que la aplicación se ha registrado con el sistema. Para obtener más información acerca de pegar objetos de datos en la aplicación, consulte el artículo [objetos de datos y orígenes de datos: manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Para obtener más información, consulte el [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) tipo de enumeración y el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura en el SDK de Windows.  
  
 Para obtener más información, consulte el [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) enumera el tipo en el SDK de Windows.  
  
##  <a name="addlinkentry"></a>  COlePasteSpecialDialog::AddLinkEntry  
 Agrega una nueva entrada a la lista de formatos de Portapapeles admitidos.  
  
```  
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```  
  
### <a name="parameters"></a>Parámetros  
 *CF*  
 Para agregar el formato del Portapapeles.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) estructura que contiene la información de la nueva entrada de vínculo.  
  
##  <a name="addstandardformats"></a>  COlePasteSpecialDialog::AddStandardFormats  
 Llame a esta función para agregar los siguientes formatos de Portapapeles a la lista de formatos de que la aplicación puede admitir en una operación de pegado especial:  
  
```  
void AddStandardFormats(BOOL bEnableLink = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bEnableLink*  
 Puede pegar la marca que determina si se debe agregar CF_LINKSOURCE a la lista de formatos de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
  
- CF_BITMAP  
  
- CF_DIB  
  
- CF_METAFILEPICT  
  
- **"Objeto incrustado"**  
  
-   (opcionalmente) **"Vincular el origen"**  
  
 Estos formatos se utilizan para admitir incrustar y vincular.  
  
##  <a name="colepastespecialdialog"></a>  COlePasteSpecialDialog::COlePasteSpecialDialog  
 Construye un objeto `COlePasteSpecialDialog`.  
  
```  
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,  
    COleDataObject* pDataObject = NULL,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwFlags*  
 Indicador de creación, contiene cualquier número de los siguientes indicadores combinados mediante el operador OR bit a bit:  
  
- PSF_SELECTPASTE especifica que el botón de radio pegar estará había activada inicialmente cuando se llama el cuadro de diálogo. No se puede usar en combinación con PSF_SELECTPASTELINK. Este es el valor predeterminado.  
  
- PSF_SELECTPASTELINK especifica que el botón de radio Pegar vínculo estará había activada inicialmente cuando se llama el cuadro de diálogo. No se puede usar en combinación con PSF_SELECTPASTE.  
  
- PSF_CHECKDISPLAYASICON especifica que la casilla de verificación Mostrar como icono estará había activada inicialmente cuando se llama el cuadro de diálogo.  
  
- PSF_SHOWHELP especifica que el botón de ayuda se mostrará cuando se llama el cuadro de diálogo.  
  
 *pDataObject*  
 Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) para pegar. Si este valor es NULL, obtiene el `COleDataObject` desde el Portapapeles.  
  
 *pParentWnd*  
 Señala al objeto de ventana principal o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo construye un `COlePasteSpecialDialog` objeto. Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) función.  
  
 Para obtener más información, consulte el [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) enumera el tipo en el SDK de Windows.  
  
##  <a name="createitem"></a>  COlePasteSpecialDialog::CreateItem  
 Crea el nuevo elemento que se ha elegido en el cuadro de diálogo Pegado especial.  
  
```  
BOOL CreateItem(COleClientItem* pNewItem);
```  
  
### <a name="parameters"></a>Parámetros  
 *pNewItem*  
 Apunta a un `COleClientItem` instancia. No puede ser nulo.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el elemento se creó correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo debe llamarse después [DoModal](#domodal) devuelve IDOK.  
  
##  <a name="domodal"></a>  COlePasteSpecialDialog::DoModal  
 Muestra el cuadro de diálogo OLE Pegado especial.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- IDOK si el cuadro de diálogo se mostró correctamente.  
  
- IDCANCEL si el usuario canceló el cuadro de diálogo.  
  
- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIPasteSpecial](http://msdn.microsoft.com/library/windows/desktop/ms694512) función en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo mediante el establecimiento de los miembros de la [m_ps](#m_ps) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve IDOK, se puede llamar a otra funciones miembro para recuperar la configuración o la entrada de información por el usuario en el cuadro de diálogo.  
  
##  <a name="getdrawaspect"></a>  COlePasteSpecialDialog::GetDrawAspect  
 Determina si el usuario optó por mostrar el elemento seleccionado como un icono.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El método necesario para representar el objeto.  
  
- DVASPECT_CONTENT devuelto si la casilla de verificación Mostrar como icono no se comprueban cuando se descartó el cuadro de diálogo.  
  
- DVASPECT_ICON devuelto si se ha activado la casilla de verificación Mostrar como icono al descarta el cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Solo llame a esta función después de [DoModal](#domodal) devuelve IDOK.  
  
 Para obtener más información sobre los aspectos de dibujo, consulte el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura en el SDK de Windows.  
  
##  <a name="geticonicmetafile"></a>  COlePasteSpecialDialog::GetIconicMetafile  
 Obtiene el metarchivo asociado al elemento seleccionado por el usuario.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo que contiene el aspecto del icono del elemento seleccionado, si se ha seleccionado la casilla de verificación Mostrar como icono al descarta el cuadro de diálogo eligiendo **Aceptar**; de lo contrario, NULL.  
  
##  <a name="getpasteindex"></a>  COlePasteSpecialDialog::GetPasteIndex  
 Obtiene el valor de índice asociado a la entrada del usuario seleccionado.  
  
```  
int GetPasteIndex() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de la matriz de `OLEUIPASTEENTRY` estructuras que se ha seleccionado por el usuario. El formato que se corresponde con el índice seleccionado debe usarse al realizar la operación de pegado.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el [OLEUIPASTEENTRY](http://msdn.microsoft.com/library/windows/desktop/ms690165) estructura en el SDK de Windows.  
  
##  <a name="getselectiontype"></a>  COlePasteSpecialDialog::GetSelectionType  
 Determina el tipo de selección realizado al usuario.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tipo de selección realizada.  
  
### <a name="remarks"></a>Comentarios  
 Se especifican los valores de tipo de valor devuelto por la `Selection` tipo de enumeración declarado en el `COlePasteSpecialDialog` clase.  
  
```  
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };  
```  
  
 Siga desccriptions breves de estos valores:  
  
- `COlePasteSpecialDialog::pasteLink` Se activa el botón de radio de pegar vínculos y al formato elegido fue un formato OLE estándar.  
  
- `COlePasteSpecialDialog::pasteNormal` Se activa el botón de radio de pegar y al formato elegido fue un formato OLE estándar.  
  
- `COlePasteSpecialDialog::pasteOther` El formato seleccionado no es un formato OLE estándar.  
  
- `COlePasteSpecialDialog::pasteStatic` El formato elegido no es un metarchivo.  
  
##  <a name="m_ps"></a>  COlePasteSpecialDialog::m_ps  
 Estructura del tipo OLEUIPASTESPECIAL usado para controlar el comportamiento del cuadro de diálogo Pegado especial.  
  
```  
OLEUIPASTESPECIAL m_ps;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) estructura en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)
