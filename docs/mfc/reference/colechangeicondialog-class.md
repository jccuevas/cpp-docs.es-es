---
title: COleChangeIconDialog (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 089fe435c86b524acc41ba528452d93032d1b1a4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214498"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog (clase)
Se utiliza en el cuadro de diálogo Cambiar icono de OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleChangeIconDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Construye un objeto `COleChangeIconDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Realiza el cambio especificado en el cuadro de diálogo.|  
|[COleChangeIconDialog::DoModal](#domodal)|Muestra el cuadro de diálogo de OLE 2 Cambiar icono.|  
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador del metarchivo asociado al formulario icónico de este elemento.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleChangeIconDialog::m_ci](#m_ci)|Una estructura que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un objeto de clase `COleChangeIconDialog` cuando desee llamar a este cuadro de diálogo. Después de un `COleChangeIconDialog` se ha construido el objeto, puede usar el [m_ci](#m_ci) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_ci` estructura es de tipo OLEUICHANGEICON. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.  
  
 Para obtener más información, consulte el [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) estructura en el SDK de Windows.  
  
 Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
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
  
##  <a name="colechangeicondialog"></a>  COleChangeIconDialog::COleChangeIconDialog  
 Esta función solo construye un `COleChangeIconDialog` objeto.  
  
```  
explicit COleChangeIconDialog(
    COleClientItem* pItem,  
    DWORD dwFlags = CIF_SELECTCURRENT,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pItem*  
 Señala el elemento que se va a convertir.  
  
 *dwFlags*  
 Marca de creación, que contiene cualquier número de los siguientes valores se combina mediante el bit a bit- u operador:  
  
- CIF_SELECTCURRENT especifica que el botón de radio actual está había seleccionado inicialmente cuando se llama el cuadro de diálogo. Este es el valor predeterminado.  
  
- CIF_SELECTDEFAULT especifica que el botón de radio predeterminado será había seleccionado inicialmente cuando se llama el cuadro de diálogo.  
  
- CIF_SELECTFROMFILE especifica que el botón de radio desde el archivo estará había seleccionado inicialmente cuando se llama el cuadro de diálogo.  
  
- CIF_SHOWHELP especifica que el botón de ayuda se mostrará cuando se llama el cuadro de diálogo.  
  
- CIF_USEICONEXE especifica que se debe extraer el icono desde el archivo ejecutable especificado en el `szIconExe` campo de [m_ci](#m_ci) en lugar de recuperarse el tipo. Esto es útil para incrustar o vincular a archivos que no son compatibles con OLE.  
  
 *pParentWnd*  
 Señala al objeto de ventana principal o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) función.  
  
 Para obtener más información, consulte el [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) estructura en el SDK de Windows.  
  
##  <a name="dochangeicon"></a>  COleChangeIconDialog::DoChangeIcon  
 Llame a esta función para cambiar el icono que representa el elemento a la seleccionada en el cuadro de diálogo después [DoModal](#domodal) devuelve IDOK.  
  
```  
BOOL DoChangeIcon(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 *pItem*  
 Apunta al elemento cuyo icono está cambiando.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el cambio tiene éxito; en caso contrario, es 0.  
  
##  <a name="domodal"></a>  COleChangeIconDialog::DoModal  
 Llame a esta función para mostrar el cuadro de diálogo OLE Cambiar icono.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- IDOK si el cuadro de diálogo se mostró correctamente.  
  
- IDCANCEL si el usuario canceló el cuadro de diálogo.  
  
- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIChangeIcon](/windows/desktop/api/oledlg/nf-oledlg-oleuichangeicona) función en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo mediante el establecimiento de los miembros de la [m_ci](#m_ci) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve IDOK, se puede llamar a otro miembro de funciones para recuperar la configuración o la información que se ha especificado por el usuario en el cuadro de diálogo.  
  
##  <a name="geticonicmetafile"></a>  COleChangeIconDialog::GetIconicMetafile  
 Llame a esta función para obtener un identificador del metarchivo que contiene el aspecto del icono del elemento seleccionado.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo que contiene el aspecto del nuevo icono icónico si se descartó el cuadro de diálogo eligiendo **Aceptar**; en caso contrario, el icono tal y como estaba antes de que se muestre el cuadro de diálogo.  
  
##  <a name="m_ci"></a>  COleChangeIconDialog::m_ci  
 Estructura del tipo OLEUICHANGEICON usado para controlar el comportamiento del cuadro de diálogo Cambiar icono.  
  
```  
OLEUICHANGEICON m_ci;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) estructura en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)
