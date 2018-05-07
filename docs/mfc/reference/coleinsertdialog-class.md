---
title: Clase de la clase COleInsertDialog | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
dev_langs:
- C++
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 041b707bec58abeb19617fbfd275428ca2cf67e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="coleinsertdialog-class"></a>Clase de la clase COleInsertDialog
Se utiliza para el cuadro de diálogo Insertar objeto OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Construye un objeto `COleInsertDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleInsertDialog::CreateItem](#createitem)|Crea el elemento seleccionado en el cuadro de diálogo.|  
|[COleInsertDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Insertar objeto OLE.|  
|[COleInsertDialog::GetClassID](#getclassid)|Obtiene el **CLSID** asociada con el elemento seleccionado.|  
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Indica si se debe dibujar el elemento como un icono.|  
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador para el metarchivo asociado con el formulario del icono de este elemento.|  
|[COleInsertDialog::GetPathName](#getpathname)|Obtiene la ruta de acceso completa al archivo elegido en el cuadro de diálogo.|  
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de objeto seleccionado.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleInsertDialog::m_io](#m_io)|Una estructura de tipo **OLEUIINSERTOBJECT** que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un objeto de clase `COleInsertDialog` cuando desee llamar a este cuadro de diálogo. Después de un `COleInsertDialog` se ha construido el objeto, puede usar el [m_io](#m_io) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_io` estructura es de tipo **OLEUIINSERTOBJECT**. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.  
  
> [!NOTE]
>  Código de contenedor generados por el Asistente de la aplicación utiliza esta clase.  
  
 Para obtener más información, consulte el [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) estructura en el SDK de Windows.  
  
 Para obtener más información sobre los cuadros de diálogo de OLE específico, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleInsertDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxodlgs.h  
  
##  <a name="coleinsertdialog"></a>  COleInsertDialog::COleInsertDialog  
 Esta función solo crea una `COleInsertDialog` objeto.  
  
```  
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 Marca de creación que contiene cualquier número de los siguientes valores para que se pueden combinar mediante el operador OR bit a bit:  
  
- **IOF_SHOWHELP** especifica que el botón de ayuda se mostrará cuando se llama el cuadro de diálogo.  
  
- **IOF_SELECTCREATENEW** especifica que el botón de opción Crear nuevo se seleccionará inicialmente cuando se llama el cuadro de diálogo. Este es el valor predeterminado y no puede utilizarse con **IOF_SELECTCREATEFROMFILE**.  
  
- **IOF_SELECTCREATEFROMFILE** especifica que el botón de opción de creación de archivo se seleccionará inicialmente cuando se llama el cuadro de diálogo. No se puede usar con **IOF_SELECTCREATENEW**.  
  
- **IOF_CHECKLINK** especifica que la casilla de verificación de vínculo se comprobará inicialmente cuando se llama el cuadro de diálogo.  
  
- **IOF_DISABLELINK** especifica que la casilla de verificación de vínculo se deshabilitará cuando se llama el cuadro de diálogo.  
  
- **IOF_CHECKDISPLAYASICON** especifica que se va a comprobar inicialmente la casilla de verificación Mostrar como icono, se mostrará el icono actual y el botón Cambiar icono se habilitará cuando se llama el cuadro de diálogo.  
  
- **IOF_VERIFYSERVERSEXIST** especifica que el cuadro de diálogo debe validar las clases que se agrega al cuadro de lista asegurándose de que los servidores especificados en la base de datos de registro existen antes de que se muestre el cuadro de diálogo. Al establecer este indicador puede afectar significativamente al rendimiento.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) a la que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana de la aplicación principal.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) función.  
  
##  <a name="createitem"></a>  COleInsertDialog::CreateItem  
 Llame a esta función para crear un objeto de tipo [COleClientItem](../../mfc/reference/coleclientitem-class.md) solo si [DoModal](#domodal) devuelve **IDOK**.  
  
```  
BOOL CreateItem(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Apunta al elemento que se va a crear.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se creó el elemento; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Debe asignar la `COleClientItem` objeto antes de que se puede llamar a esta función.  
  
##  <a name="domodal"></a>  COleInsertDialog::DoModal  
 Llame a esta función para mostrar el cuadro de diálogo Insertar objeto OLE.  
  
```  
virtual INT_PTR   
    DoModal();

 
INT_PTR   
    DoModal(DWORD  dwFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 Uno de los siguientes valores:  
  
 `COleInsertDialog::DocObjectsOnly` Inserta solo DocObjects.  
  
 `COleInsertDialog::ControlsOnly` inserta sólo los controles ActiveX.  
  
 Cero inserta DocObject ni un control ActiveX. Este valor se genera en la misma implementación como el primer prototipo mencionados anteriormente.  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
-   IDOK si el cuadro de diálogo se muestra correctamente.  
  
-   IDCANCEL si el usuario canceló el cuadro de diálogo.  
  
-   IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función de miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIInsertObject](http://msdn.microsoft.com/library/windows/desktop/ms694325) función en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la [m_io](#m_io) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve IDOK, puede llamar a otro miembro funciones para recuperar los valores de configuración o la entrada de información en el cuadro de diálogo por el usuario.  
  
##  <a name="getclassid"></a>  COleInsertDialog::GetClassID  
 Llame a esta función para obtener el **CLSID** asociados con el elemento seleccionado solo si [DoModal](#domodal) devuelve **IDOK** y el tipo de selección es **clase COleInsertDialog:: createNewItem**.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el **CLSID** asociados con el elemento seleccionado.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) del SDK de Windows.  
  
##  <a name="getdrawaspect"></a>  COleInsertDialog::GetDrawAspect  
 Llame a esta función para determinar si el usuario decidió mostrar el elemento seleccionado como un icono.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El método necesario para representar el objeto.  
  
- `DVASPECT_CONTENT` Devuelve si no se activa la casilla de verificación Mostrar como icono.  
  
- `DVASPECT_ICON` Devuelve si se activa la casilla de verificación Mostrar como icono.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este solo si función [DoModal](#domodal) devuelve **IDOK**.  
  
 Para obtener más información sobre los aspectos de dibujo, consulte [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura de datos en el SDK de Windows.  
  
##  <a name="geticonicmetafile"></a>  COleInsertDialog::GetIconicMetafile  
 Llame a esta función para obtener un identificador de metarchivo que contiene el icono aspecto del elemento seleccionado.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo que contiene el icono aspecto del elemento seleccionado, si la casilla de verificación Mostrar como icono estaba activa cuando se cierra el cuadro de diálogo seleccionando **Aceptar**; en caso contrario **NULL**.  
  
##  <a name="getpathname"></a>  COleInsertDialog::GetPathName  
 Llame a esta función para obtener la ruta completa del archivo seleccionado solo si [DoModal](#domodal) devuelve **IDOK** y el tipo de selección no es **COleInsertDialog::createNewItem**.  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La ruta de acceso completa al archivo seleccionado en el cuadro de diálogo. Si el tipo de selección es `createNewItem`, esta función devuelve un sentido `CString` en modo de lanzamiento o produce una aserción en modo de depuración.  
  
##  <a name="getselectiontype"></a>  COleInsertDialog::GetSelectionType  
 Llame a esta función para obtener el tipo de selección que elige al descartar el cuadro de diálogo Insertar objeto eligiendo **Aceptar**.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de selección realizada.  
  
### <a name="remarks"></a>Comentarios  
 Se especifican los valores de tipo de valor devuelto por la **selección** tipo de enumeración declarado en el `COleInsertDialog` clase.  
  
```  
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };  
```  
  
 Siguen breves descripciones de los valores siguientes:  
  
- **COleInsertDialog::createNewItem** se seleccionó crear el nuevo botón de radio.  
  
- **COleInsertDialog::insertFromFile** se ha seleccionado el botón de radio de la creación de archivo y no se activó la casilla de verificación de vínculo.  
  
- **COleInsertDialog::linkToFile** se ha seleccionado el botón de radio de la creación de archivo y se activa la casilla de verificación de vínculo.  
  
##  <a name="m_io"></a>  COleInsertDialog::m_io  
 Estructura de tipo **OLEUIINSERTOBJECT** utilizado para controlar el comportamiento del cuadro de diálogo Insertar objeto.  
  
```  
OLEUIINSERTOBJECT m_io;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) estructura en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)
