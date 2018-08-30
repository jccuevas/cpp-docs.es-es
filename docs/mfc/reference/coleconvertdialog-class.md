---
title: COleConvertDialog (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
dev_langs:
- C++
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c63eda0bbe734bd7c9f0a972e6756a444369123
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212435"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog (clase)
Para obtener más información, consulte el [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) estructura en el SDK de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|Construye un objeto `COleConvertDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleConvertDialog::DoConvert](#doconvert)|Realiza la conversión especificada en el cuadro de diálogo.|  
|[COleConvertDialog::DoModal](#domodal)|Muestra el cuadro de diálogo OLE de cambios de elemento.|  
|[COleConvertDialog::GetClassID](#getclassid)|Obtiene el CLSID asociado al elemento seleccionado.|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Especifica si se debe dibujar elementos como un icono.|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador del metarchivo asociado al formulario icónico de este elemento.|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de selección elegido.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|Una estructura que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Código de contenedor generados por el Asistente para la aplicación usa esta clase.  
  
 Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxodlgs.h  
  
##  <a name="coleconvertdialog"></a>  COleConvertDialog::COleConvertDialog  
 Solo construye un `COleConvertDialog` objeto.  
  
```  
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pItem*  
 Apunta al elemento que se va a convertir o activado.  
  
 *dwFlags*  
 Marca de creación, que contiene cualquier número de los siguientes valores se combina mediante el bit a bit- u operador:  
  
- CF_SELECTCONVERTTO especifica que el botón de radio convertir a estará había seleccionado inicialmente cuando se llama el cuadro de diálogo. Este es el valor predeterminado.  
  
- CF_SELECTACTIVATEAS especifica que el botón de radio activar como estará había seleccionado inicialmente cuando se llama el cuadro de diálogo.  
  
- CF_SETCONVERTDEFAULT especifica que la clase cuyo CLSID especificado por el `clsidConvertDefault` miembro de la `m_cv` estructura se usará como la selección predeterminada en el cuadro de lista de clase cuando se selecciona el botón de radio convertir a.  
  
- CF_SETACTIVATEDEFAULT especifica que la clase cuyo CLSID especificado por el `clsidActivateDefault` miembro de la `m_cv` estructura se usará como la selección predeterminada en el cuadro de lista de clase cuando se selecciona el botón de opción Activar como.  
  
- CF_SHOWHELPBUTTON especifica que el botón de ayuda se mostrará cuando se llama el cuadro de diálogo.  
  
 *pClassID*  
 Señala el CLSID del elemento que se va a convertir o activado. Si es NULL, el CLSID asociado *pItem* se usará.  
  
 *pParentWnd*  
 Señala al objeto de ventana principal o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) función.  
  
 Para obtener más información, consulte [clave CLSID](/windows/desktop/com/clsid-key-hklm) y [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) estructura.  
  
##  <a name="doconvert"></a>  COleConvertDialog::DoConvert  
 Llame a esta función, después de devolver correctamente desde [DoModal](#domodal), ya sea para convertir o para activar un objeto de tipo [COleClientItem](../../mfc/reference/coleclientitem-class.md).  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 *pItem*  
 Apunta al elemento que se va a convertir o activado. No puede ser nulo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Se puede convertir el elemento o activa según la información seleccionada por el usuario en el cuadro de diálogo convertir.  
  
##  <a name="domodal"></a>  COleConvertDialog::DoModal  
 Llame a esta función para mostrar el cuadro de diálogo Convertir OLE.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- IDOK si el cuadro de diálogo se mostró correctamente.  
  
- IDCANCEL si el usuario canceló el cuadro de diálogo.  
  
- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIConvert](/windows/desktop/api/oledlg/nf-oledlg-oleuiconverta) función en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo mediante el establecimiento de los miembros de la [m_cv](#m_cv) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve IDOK, se puede llamar a otro miembro de funciones para recuperar la configuración o la información que se ha especificado por el usuario en el cuadro de diálogo.  
  
##  <a name="getclassid"></a>  COleConvertDialog::GetClassID  
 Llamada a esta función para obtener el CLSID asociado al elemento del usuario seleccionado en el cuadro de diálogo convertir.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El CLSID asociado al elemento seleccionado en el cuadro de diálogo convertir.  
  
### <a name="remarks"></a>Comentarios  
 Llamada a esta función solo después de [DoModal](#domodal) devuelve IDOK.  
  
 Para obtener más información, consulte [clave CLSID](/windows/desktop/com/clsid-key-hklm) en el SDK de Windows.  
  
##  <a name="getdrawaspect"></a>  COleConvertDialog::GetDrawAspect  
 Llame a esta función para determinar si el usuario optó por mostrar el elemento seleccionado como un icono.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El método necesario para representar el objeto.  
  
- DVASPECT_CONTENT devuelto si no se ha activado la casilla de verificación Mostrar como icono.  
  
- DVASPECT_ICON devuelto si se ha activado la casilla de verificación Mostrar como icono.  
  
### <a name="remarks"></a>Comentarios  
 Llamada a esta función solo después de [DoModal](#domodal) devuelve IDOK.  
  
 Para obtener más información sobre los aspectos de dibujo, consulte el [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura de datos en el SDK de Windows.  
  
##  <a name="geticonicmetafile"></a>  COleConvertDialog::GetIconicMetafile  
 Llame a esta función para obtener un identificador del metarchivo que contiene el aspecto del icono del elemento seleccionado.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo que contiene el aspecto del icono del elemento seleccionado, si la casilla de verificación Mostrar como icono comprobar cuándo se descarta el cuadro de diálogo si elige Aceptar; en caso contrario, es NULL.  
  
##  <a name="getselectiontype"></a>  COleConvertDialog::GetSelectionType  
 Llame a esta función para determinar el tipo de conversión seleccionado en el cuadro de diálogo convertir.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de selección realizada.  
  
### <a name="remarks"></a>Comentarios  
 Se especifican los valores de tipo de valor devuelto por la `Selection` tipo de enumeración declarado en el `COleConvertDialog` clase.  
  
```  
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };  
```  
  
 Siguen breves descripciones de los valores siguientes:  
  
- `COleConvertDialog::noConversion` Devuelve si se canceló el cuadro de diálogo o el usuario ha seleccionado ninguna conversión. Si `COleConvertDialog::DoModal` devuelve IDOK, es posible que el usuario seleccione un icono diferente del que previamente ha seleccionado.  
  
- `COleConvertDialog::convertItem` Devuelve si se activa el botón de radio convertir a, el usuario seleccionó un elemento diferente para convertir en, y `DoModal` devuelve IDOK.  
  
- `COleConvertDialog::activateAs` Devuelve si se activa el botón de radio activar como, el usuario seleccionó un elemento diferente en activarse y `DoModal` devuelve IDOK.  
  
##  <a name="m_cv"></a>  COleConvertDialog::m_cv  
 Estructura del tipo OLEUICONVERT usado para controlar el comportamiento del cuadro de diálogo convertir.  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) estructura en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)
