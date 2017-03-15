---
title: Clase de la clase COleConvertDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleConvertDialog
dev_langs:
- C++
helpviewer_keywords:
- COleConvertDialog class
- OLE Convert dialog box
- dialog boxes, OLE
- OLE dialog boxes, Convert
- Convert dialog box
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
caps.latest.revision: 22
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
ms.openlocfilehash: 6db5caf443e7f71c58e2c65b46794c2c9d246d38
ms.lasthandoff: 02/24/2017

---
# <a name="coleconvertdialog-class"></a>Clase COleConvertDialog (clase)
Para obtener más información, consulte el [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
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
|[COleConvertDialog::GetClassID](#getclassid)|Obtiene el **CLSID** asociado con el elemento seleccionado.|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Especifica si se debe dibujar elementos como un icono.|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador para el metarchivo asociado con el formulario icónico de este elemento.|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de selección elegida.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|Estructura que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Código de contenedor generados por el Asistente de la aplicación utiliza esta clase.  
  
 Para obtener más información acerca de cuadros de diálogo OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
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
  
##  <a name="a-namecoleconvertdialoga--coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog  
 Sólo se crea un `COleConvertDialog` objeto.  
  
```  
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Señala el elemento que se va a convertir o activado.  
  
 `dwFlags`  
 Indicador de creación, que contiene cualquier número de los siguientes valores combinados mediante el bit a bit- u operador:  
  
- **CF_SELECTCONVERTTO** especifica que el botón de radio convertir a se seleccionará inicialmente cuando se llama el cuadro de diálogo. Este es el valor predeterminado.  
  
- **CF_SELECTACTIVATEAS** especifica que el botón de opción Activar como se seleccionará inicialmente cuando se llama el cuadro de diálogo.  
  
- **CF_SETCONVERTDEFAULT** especifica que la clase cuyos **CLSID** especificado por la **clsidConvertDefault** miembro de la `m_cv` estructura se usará como la selección predeterminada en el cuadro de lista de la clase cuando se selecciona el botón de radio convertir a.  
  
- **CF_SETACTIVATEDEFAULT** especifica que la clase cuyos **CLSID** especificado por la **clsidActivateDefault** miembro de la `m_cv` estructura se usará como la selección predeterminada en el cuadro de lista de la clase cuando se selecciona el botón de opción Activar como.  
  
- **CF_SHOWHELPBUTTON** especifica que el botón de ayuda se mostrará cuando se llama el cuadro de diálogo.  
  
 `pClassID`  
 Señala el CLSID del elemento que se va a convertir o activado. Si **NULL**, **CLSID** asociado `pItem` se usará.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) (función).  
  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) y [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) estructura.  
  
##  <a name="a-namedoconverta--coleconvertdialogdoconvert"></a><a name="doconvert"></a>COleConvertDialog::DoConvert  
 Llame a esta función, después de volver correctamente de [DoModal](#domodal), ya sea para convertir o activar un objeto de tipo [COleClientItem](../../mfc/reference/coleclientitem-class.md).  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Señala el elemento que se va a convertir o activado. No puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El elemento se convierte o se activa según la información seleccionada por el usuario en el cuadro de diálogo convertir.  
  
##  <a name="a-namedomodala--coleconvertdialogdomodal"></a><a name="domodal"></a>COleConvertDialog::DoModal  
 Llame a esta función para mostrar el cuadro de diálogo Convertir OLE.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- **IDOK** si el cuadro de diálogo se muestra correctamente.  
  
- **IDCANCEL** si el usuario cancela el cuadro de diálogo.  
  
- **IDABORT** si se produjo un error. Si **IDABORT** es devuelto, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, consulte el [OleUIConvert](http://msdn.microsoft.com/library/windows/desktop/ms680694) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la [m_cv](#m_cv) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve **IDOK**, puede llamar a otro miembro de funciones para recuperar la configuración o la información que se introduce el usuario en el cuadro de diálogo.  
  
##  <a name="a-namegetclassida--coleconvertdialoggetclassid"></a><a name="getclassid"></a>COleConvertDialog::GetClassID  
 Llame a esta función para obtener el **CLSID** asociado con el elemento, el usuario seleccionado en el cuadro de diálogo convertir.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El **CLSID** asociado con el elemento seleccionado en el cuadro de diálogo convertir.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo después de llamada [DoModal](#domodal) devuelve **IDOK**.  
  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetdrawaspecta--coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect  
 Llame a esta función para determinar si el usuario decidió mostrar el elemento seleccionado como un icono.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El método necesario para representar el objeto.  
  
- `DVASPECT_CONTENT`Devuelve si no está activada la casilla de verificación Mostrar como icono.  
  
- `DVASPECT_ICON`Devuelve si se ha activado la casilla de verificación Mostrar como icono.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo después de llamada [DoModal](#domodal) devuelve **IDOK**.  
  
 Para obtener más información sobre los aspectos de dibujo, consulte el [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura de datos en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegeticonicmetafilea--coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile  
 Llame a esta función para obtener un identificador de metarchivo contiene el aspecto de iconos del elemento seleccionado.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo que contiene el aspecto de iconos del elemento seleccionado, si la casilla de verificación Mostrar como icono estaba activa cuando se cerró el cuadro de diálogo seleccionando **Aceptar**; en caso contrario **NULL**.  
  
##  <a name="a-namegetselectiontypea--coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleConvertDialog::GetSelectionType  
 Llame a esta función para determinar el tipo de conversión seleccionado en el cuadro de diálogo convertir.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de selección realizada.  
  
### <a name="remarks"></a>Comentarios  
 Especifica los valores de tipo de valor devuelto por la **selección** tipo de enumeración declarado en el `COleConvertDialog` clase.  
  
 `enum Selection`  
  
 `{`  
  
 `noConversion,`  
  
 `convertItem,`  
  
 `activateAs`  
  
 `};`  
  
 Siguen breves descripciones de estos valores:  
  
- **COleConvertDialog::noConversion** devuelto si el cuadro de diálogo se canceló o el usuario no seleccionó ninguna conversión. Si `COleConvertDialog::DoModal` devuelve **IDOK**, es posible que el usuario seleccionó un icono diferente a la que seleccionó anteriormente.  
  
- **COleConvertDialog::convertItem** devuelto si se activa el botón de radio convertir a, el usuario seleccionó un elemento diferente para convertir, y `DoModal` devuelve **IDOK**.  
  
- **COleConvertDialog::activateAs** devuelto si se activa el botón de opción Activar como, el usuario selecciona otro elemento para activar, y `DoModal` devuelve **IDOK**.  
  
##  <a name="a-namemcva--coleconvertdialogmcv"></a><a name="m_cv"></a>COleConvertDialog::m_cv  
 Estructura de tipo **OLEUICONVERT** utilizado para controlar el comportamiento del cuadro de diálogo convertir.  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)

