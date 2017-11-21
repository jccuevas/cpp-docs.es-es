---
title: Clase de la clase COleConvertDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 72de3b05dad581b2b0f4f3eec19e15d211bba601
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="coleconvertdialog-class"></a>Clase de la clase COleConvertDialog
Para obtener más información, consulte el [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) estructura en el SDK de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|Construye un objeto `COleConvertDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleConvertDialog::DoConvert](#doconvert)|Realiza la conversión especificada en el cuadro de diálogo.|  
|[COleConvertDialog::DoModal](#domodal)|Muestra el cuadro de diálogo elemento OLE cambio.|  
|[COleConvertDialog::GetClassID](#getclassid)|Obtiene el **CLSID** asociada con el elemento seleccionado.|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Especifica si se debe dibujar elementos como un icono.|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador para el metarchivo asociado con el formulario del icono de este elemento.|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de selección elegido.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|Una estructura que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Código de contenedor generados por el Asistente de la aplicación utiliza esta clase.  
  
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
  
##  <a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog  
 Construye sólo un `COleConvertDialog` objeto.  
  
```  
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Apunta al elemento que desea convertir o activar.  
  
 `dwFlags`  
 Indicador de creación, que contiene cualquier número de los valores siguientes combinada con el bit a bit- u operador:  
  
- **CF_SELECTCONVERTTO** especifica que el botón de radio convertir a se seleccionará inicialmente cuando se llama el cuadro de diálogo. Este es el valor predeterminado.  
  
- **CF_SELECTACTIVATEAS** especifica que el botón de opción Activar como se seleccionará inicialmente cuando se llama el cuadro de diálogo.  
  
- **CF_SETCONVERTDEFAULT** especifica que la clase cuyos **CLSID** especificado por el **clsidConvertDefault** miembro de la `m_cv` estructura se usará como valor predeterminado selección en el cuadro de lista de la clase cuando se selecciona el botón de radio convertir a.  
  
- **CF_SETACTIVATEDEFAULT** especifica que la clase cuyos **CLSID** especificado por el **clsidActivateDefault** miembro de la `m_cv` estructura se usará como valor predeterminado selección en el cuadro de lista de la clase cuando se selecciona el botón de opción Activar como.  
  
- **CF_SHOWHELPBUTTON** especifica que el botón de ayuda se mostrará cuando se llama el cuadro de diálogo.  
  
 `pClassID`  
 Señala el CLSID del elemento que se pueden convertir o activar. Si **NULL**, **CLSID** asociada `pItem` se usará.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) a la que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del cuadro de diálogo se establece en la ventana de la aplicación principal.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) función.  
  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) y [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) estructura.  
  
##  <a name="doconvert"></a>COleConvertDialog::DoConvert  
 Llame a esta función, después de volver correctamente desde [DoModal](#domodal), ya sea para convertir o para activar un objeto de tipo [COleClientItem](../../mfc/reference/coleclientitem-class.md).  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Apunta al elemento que desea convertir o activar. No puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El elemento se convierte o se activa según la información seleccionada por el usuario en el cuadro de diálogo convertir.  
  
##  <a name="domodal"></a>COleConvertDialog::DoModal  
 Llame a esta función para mostrar el cuadro de diálogo Convertir OLE.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- **IDOK** si el cuadro de diálogo se muestra correctamente.  
  
- **IDCANCEL** si el usuario canceló el cuadro de diálogo.  
  
- **IDABORT** si se produjo un error. Si **IDABORT** es devuelto, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función de miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIConvert](http://msdn.microsoft.com/library/windows/desktop/ms680694) función en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la [m_cv](#m_cv) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve **IDOK**, puede llamar a otro miembro funciones para recuperar los valores de configuración o la información que se ha especificado por el usuario en el cuadro de diálogo.  
  
##  <a name="getclassid"></a>COleConvertDialog::GetClassID  
 Llame a esta función para obtener el **CLSID** asociado al elemento del usuario seleccionado en el cuadro de diálogo convertir.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El **CLSID** asociada con el elemento seleccionado en el cuadro de diálogo convertir.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo después de llamada [DoModal](#domodal) devuelve **IDOK**.  
  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) del SDK de Windows.  
  
##  <a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect  
 Llame a esta función para determinar si el usuario decidió mostrar el elemento seleccionado como un icono.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El método necesario para representar el objeto.  
  
- `DVASPECT_CONTENT`Devuelve si no se activa la casilla de verificación Mostrar como icono.  
  
- `DVASPECT_ICON`Devuelve si se activa la casilla de verificación Mostrar como icono.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo después de llamada [DoModal](#domodal) devuelve **IDOK**.  
  
 Para obtener más información sobre los aspectos de dibujo, consulte el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura de datos en el SDK de Windows.  
  
##  <a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile  
 Llame a esta función para obtener un identificador de metarchivo que contiene el icono aspecto del elemento seleccionado.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo que contiene el icono aspecto del elemento seleccionado, si la casilla de verificación Mostrar como icono estaba activa cuando se cierra el cuadro de diálogo seleccionando **Aceptar**; en caso contrario **NULL**.  
  
##  <a name="getselectiontype"></a>COleConvertDialog::GetSelectionType  
 Llame a esta función para determinar el tipo de conversión seleccionado en el cuadro de diálogo de Convert.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de selección realizada.  
  
### <a name="remarks"></a>Comentarios  
 Se especifican los valores de tipo de valor devuelto por la **selección** tipo de enumeración declarado en el `COleConvertDialog` clase.  
  
```  
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };  
```  
  
 Siguen breves descripciones de los valores siguientes:  
  
- **COleConvertDialog::noConversion** devuelto si se canceló el cuadro de diálogo o el usuario seleccionado no existe una conversión. Si `COleConvertDialog::DoModal` devuelve **IDOK**, es posible que el usuario selecciona un icono diferente que aquel seleccionado anteriormente.  
  
- **COleConvertDialog::convertItem** devuelto si se activa el botón de radio convertir a, el usuario selecciona otro elemento para convertir, y `DoModal` devuelve **IDOK**.  
  
- **COleConvertDialog::activateAs** devuelto si se activa el botón de opción Activar como, el usuario selecciona un elemento diferente para activar, y `DoModal` devuelve **IDOK**.  
  
##  <a name="m_cv"></a>COleConvertDialog::m_cv  
 Estructura de tipo **OLEUICONVERT** utilizado para controlar el comportamiento del cuadro de diálogo convertir.  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) estructura en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)
