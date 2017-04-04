---
title: Clase de la clase COleInsertDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- OLE Insert Object dialog box
- dialog boxes, OLE
- COleInsertDialog class
- Insert Object dialog box
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
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
ms.openlocfilehash: 078f421dacc79ff929249cd35c520b0c4d4a222e
ms.lasthandoff: 02/24/2017

---
# <a name="coleinsertdialog-class"></a>Clase COleInsertDialog (clase)
Se utiliza para el cuadro de diálogo Insertar objeto OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Construye un objeto `COleInsertDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleInsertDialog::CreateItem](#createitem)|Crea el elemento seleccionado en el cuadro de diálogo.|  
|[COleInsertDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Insertar objeto OLE.|  
|[COleInsertDialog::GetClassID](#getclassid)|Obtiene el **CLSID** asociado con el elemento seleccionado.|  
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Indica si se debe dibujar el elemento como un icono.|  
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador para el metarchivo asociado con el formulario icónico de este elemento.|  
|[COleInsertDialog::GetPathName](#getpathname)|Obtiene la ruta de acceso completa al archivo elegido en el cuadro de diálogo.|  
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de objeto seleccionado.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleInsertDialog::m_io](#m_io)|Una estructura de tipo **OLEUIINSERTOBJECT** que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un objeto de clase `COleInsertDialog` cuando desee llamar a este cuadro de diálogo. Después de un `COleInsertDialog` se ha construido el objeto, puede usar el [m_io](#m_io) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_io` estructura es de tipo **OLEUIINSERTOBJECT**. Para obtener más información acerca del uso de esta clase de cuadro de diálogo, vea la [DoModal](#domodal) función miembro.  
  
> [!NOTE]
>  Código de contenedor generados por el Asistente de la aplicación utiliza esta clase.  
  
 Para obtener más información, consulte el [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre los cuadros de diálogo OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
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
  
##  <a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog  
 Esta función sólo crea un `COleInsertDialog` objeto.  
  
```  
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 Indicador de creación que contiene cualquier número de los siguientes valores se combinan mediante el operador OR bit a bit:  
  
- **IOF_SHOWHELP** especifica que el botón de ayuda se mostrará cuando se llama el cuadro de diálogo.  
  
- **IOF_SELECTCREATENEW** especifica que el botón de opción Crear nuevo se seleccionará inicialmente cuando se llama el cuadro de diálogo. Este es el valor predeterminado y no puede utilizarse con **IOF_SELECTCREATEFROMFILE**.  
  
- **IOF_SELECTCREATEFROMFILE** especifica que el botón de opción Crear desde archivo se seleccionará inicialmente cuando se llama el cuadro de diálogo. No se puede usar con **IOF_SELECTCREATENEW**.  
  
- **IOF_CHECKLINK** especifica que la casilla de verificación vínculo se comprobará inicialmente cuando se llama el cuadro de diálogo.  
  
- **IOF_DISABLELINK** especifica que la casilla de verificación vínculo se deshabilitará cuando se llama el cuadro de diálogo.  
  
- **IOF_CHECKDISPLAYASICON** especifica que la casilla de verificación Mostrar como icono se comprobarán inicialmente, se mostrará el icono actual y se habilitará el botón Cambiar icono cuando se llama el cuadro de diálogo.  
  
- **IOF_VERIFYSERVERSEXIST** especifica que el cuadro de diálogo debe validar las clases que se agrega al cuadro de lista al garantizar que los servidores especificados en la base de datos de registro existen antes de mostrar el cuadro de diálogo. Establecer este indicador puede afectar significativamente al rendimiento.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) (función).  
  
##  <a name="createitem"></a>COleInsertDialog::CreateItem  
 Llame a esta función para crear un objeto de tipo [COleClientItem](../../mfc/reference/coleclientitem-class.md) sólo si [DoModal](#domodal) devuelve **IDOK**.  
  
```  
BOOL CreateItem(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Puntos de elemento que se va a crear.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se creó el elemento; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Debe asignar la `COleClientItem` objeto antes de que se puede llamar a esta función.  
  
##  <a name="domodal"></a>COleInsertDialog::DoModal  
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
  
 `COleInsertDialog::DocObjectsOnly`inserta sólo DocObjects.  
  
 `COleInsertDialog::ControlsOnly`inserta sólo los controles ActiveX.  
  
 Cero inserta DocObject ni un control ActiveX. Este valor se produce en la misma implementación que el primer prototipo mencionados anteriormente.  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
-   IDOK si el cuadro de diálogo se muestra correctamente.  
  
-   IDCANCEL si el usuario cancela el cuadro de diálogo.  
  
-   IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, consulte el [OleUIInsertObject](http://msdn.microsoft.com/library/windows/desktop/ms694325) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la [m_io](#m_io) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve IDOK, puede llamar a otro miembro de funciones para recuperar la configuración o la entrada de información en el cuadro de diálogo por el usuario.  
  
##  <a name="getclassid"></a>COleInsertDialog::GetClassID  
 Llame a esta función para obtener el **CLSID** asociado con el elemento seleccionado solo si [DoModal](#domodal) devuelve **IDOK** y es el tipo de selección **COleInsertDialog::createNewItem**.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el **CLSID** asociados con el elemento seleccionado.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect  
 Llame a esta función para determinar si el usuario decidió mostrar el elemento seleccionado como un icono.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El método necesario para representar el objeto.  
  
- `DVASPECT_CONTENT`Devuelve si no está activada la casilla de verificación Mostrar como icono.  
  
- `DVASPECT_ICON`Devuelve si se ha activado la casilla de verificación Mostrar como icono.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta si función [DoModal](#domodal) devuelve **IDOK**.  
  
 Para obtener más información sobre los aspectos de dibujo, consulte [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura de datos en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile  
 Llame a esta función para obtener un identificador de metarchivo contiene el aspecto de iconos del elemento seleccionado.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo que contiene el aspecto de iconos del elemento seleccionado, si la casilla de verificación Mostrar como icono estaba activa cuando se cerró el cuadro de diálogo seleccionando **Aceptar**; en caso contrario **NULL**.  
  
##  <a name="getpathname"></a>COleInsertDialog::GetPathName  
 Llame a esta función para obtener la ruta completa de la sólo si archivo seleccionado [DoModal](#domodal) devuelve **IDOK** y el tipo de selección no es **COleInsertDialog::createNewItem**.  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Ruta de acceso completa al archivo seleccionado en el cuadro de diálogo. Si el tipo de selección es `createNewItem`, esta función devuelve un sentido `CString` en modo de lanzamiento o produce una aserción en modo de depuración.  
  
##  <a name="getselectiontype"></a>COleInsertDialog::GetSelectionType  
 Llame a esta función para obtener el tipo de selección elegido cuando se cierra el cuadro de diálogo Insertar objeto eligiendo **Aceptar**.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de selección realizada.  
  
### <a name="remarks"></a>Comentarios  
 Especifica los valores de tipo de valor devuelto por la **selección** tipo de enumeración declarado en el `COleInsertDialog` clase.  
  
```  
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };  
```  
  
 Siguen breves descripciones de estos valores:  
  
- **COleInsertDialog::createNewItem** se ha seleccionado crear el nuevo botón de radio.  
  
- **COleInsertDialog::insertFromFile** se ha seleccionado el botón de radio de la creación de archivo y no está activada la casilla de verificación vínculo.  
  
- **COleInsertDialog::linkToFile** se ha seleccionado el botón de radio de la creación de archivo y se selecciona la casilla de verificación vínculo.  
  
##  <a name="m_io"></a>COleInsertDialog::m_io  
 Estructura de tipo **OLEUIINSERTOBJECT** utilizado para controlar el comportamiento del cuadro de diálogo Insertar objeto.  
  
```  
OLEUIINSERTOBJECT m_io;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)

