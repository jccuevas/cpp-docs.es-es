---
title: Clase de la clase COleChangeIconDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
dev_langs:
- C++
helpviewer_keywords:
- OLE dialog boxes, Change Icon
- OLE Change Icon dialog box
- dialog boxes, OLE
- COleChangeIconDialog class
- Change Icon dialog box
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 07dfd7995bbbdb0f52f55dceedc318d8d702111b
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="colechangeicondialog-class"></a>Clase COleChangeIconDialog (clase)
Se utiliza en el cuadro de diálogo Cambiar icono de OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleChangeIconDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Construye un objeto `COleChangeIconDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Realiza el cambio especificado en el cuadro de diálogo.|  
|[COleChangeIconDialog::DoModal](#domodal)|Muestra el cuadro de diálogo de OLE 2 Cambiar icono.|  
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador para el metarchivo asociado con el formulario icónico de este elemento.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleChangeIconDialog::m_ci](#m_ci)|Estructura que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un objeto de clase `COleChangeIconDialog` cuando desee llamar a este cuadro de diálogo. Después de un `COleChangeIconDialog` se ha construido el objeto, puede usar el [m_ci](#m_ci) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_ci` estructura es de tipo **OLEUICHANGEICON**. Para obtener más información acerca del uso de esta clase de cuadro de diálogo, vea la [DoModal](#domodal) función miembro.  
  
 Para obtener más información, consulte el [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información acerca de cuadros de diálogo OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeIconDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxodlgs.h  
  
##  <a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog  
 Esta función sólo crea un `COleChangeIconDialog` objeto.  
  
```  
explicit COleChangeIconDialog(
    COleClientItem* pItem,  
    DWORD dwFlags = CIF_SELECTCURRENT,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Puntos de elemento que se va a convertir.  
  
 `dwFlags`  
 Indicador de creación, que contiene cualquier número de los siguientes valores combinados mediante el bit a bit- u operador:  
  
- **CIF_SELECTCURRENT** especifica que el botón de opción actual se seleccionará inicialmente cuando se llama el cuadro de diálogo. Este es el valor predeterminado.  
  
- **CIF_SELECTDEFAULT** especifica que el botón de radio predeterminado se seleccionará inicialmente cuando se llama el cuadro de diálogo.  
  
- **CIF_SELECTFROMFILE** especifica que el botón de opción de archivo se seleccionará inicialmente cuando se llama el cuadro de diálogo.  
  
- **CIF_SHOWHELP** especifica que el botón de ayuda se mostrará cuando se llama el cuadro de diálogo.  
  
- **CIF_USEICONEXE** especifica que se debe extraer el icono desde el archivo ejecutable especificado en el **szIconExe** del [m_ci](#m_ci) en lugar de recuperar del tipo. Esto es útil para incrustar o vincular a archivos no OLE.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) (función).  
  
 Para obtener más información, consulte el [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="dochangeicon"></a>COleChangeIconDialog::DoChangeIcon  
 Llame a esta función para cambiar el icono que representa el elemento seleccionado en el cuadro de diálogo después de [DoModal](#domodal) devuelve **IDOK**.  
  
```  
BOOL DoChangeIcon(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Señala el elemento cuyo icono está cambiando.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el cambio es correcto; en caso contrario, 0.  
  
##  <a name="domodal"></a>COleChangeIconDialog::DoModal  
 Llame a esta función para mostrar el cuadro de diálogo de OLE Cambiar icono.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- **IDOK** si el cuadro de diálogo se muestra correctamente.  
  
- **IDCANCEL** si el usuario cancela el cuadro de diálogo.  
  
- **IDABORT** si se produjo un error. Si **IDABORT** es devuelto, llame a la `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, consulte el [OleUIChangeIcon](http://msdn.microsoft.com/library/windows/desktop/ms688307) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la [m_ci](#m_ci) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve **IDOK**, puede llamar a otro miembro de funciones para recuperar la configuración o la información que se introduce el usuario en el cuadro de diálogo.  
  
##  <a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile  
 Llame a esta función para obtener un identificador de metarchivo contiene el aspecto de iconos del elemento seleccionado.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo que contiene el aspecto del nuevo icono icónico Si descarta el cuadro de diálogo seleccionando **Aceptar**; en caso contrario, el icono tal y como estaba antes de que se muestre el cuadro de diálogo.  
  
##  <a name="m_ci"></a>COleChangeIconDialog::m_ci  
 Estructura de tipo **OLEUICHANGEICON** utilizado para controlar el comportamiento del cuadro de diálogo Cambiar icono.  
  
```  
OLEUICHANGEICON m_ci;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)

