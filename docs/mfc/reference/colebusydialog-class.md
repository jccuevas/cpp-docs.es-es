---
title: Clase de la clase COleBusyDialog | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
dev_langs:
- C++
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4af90e9354e7d443cb50acbafaa1468c99c12c85
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040917"
---
# <a name="colebusydialog-class"></a>Clase de la clase COleBusyDialog
Se utiliza en los cuadros de diálogo que indican que el servidor OLE no responde o el servidor está ocupado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleBusyDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Construye un objeto `COleBusyDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleBusyDialog::DoModal](#domodal)|Muestra el cuadro de diálogo OLE servidor ocupado.|  
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Determina la elección realizada en el cuadro de diálogo.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleBusyDialog::m_bz](#m_bz)|Estructura de tipo **OLEUIBUSY** que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un objeto de clase `COleBusyDialog` cuando desee llamar a estos cuadros de diálogo. Después de un `COleBusyDialog` se ha construido el objeto, puede usar el [m_bz](#m_bz) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_bz` estructura es de tipo **OLEUIBUSY**. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.  
  
> [!NOTE]
>  Código de contenedor generados por el Asistente de la aplicación utiliza esta clase.  
  
 Para obtener más información, consulte el [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) estructura en el SDK de Windows.  
  
 Para obtener más información sobre los cuadros de diálogo de OLE específico, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleBusyDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxodlgs.h  
  
##  <a name="colebusydialog"></a>  COleBusyDialog::COleBusyDialog  
 Esta función solo se crea un `COleBusyDialog` objeto.  
  
```  
explicit COleBusyDialog(
    HTASK htaskBusy,  
    BOOL bNotResponding = FALSE,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *htaskBusy*  
 Identificador de la tarea de servidor está ocupada.  
  
 *bNotResponding*  
 Si **TRUE**, llamar el cuadro de diálogo no responde en lugar del cuadro de diálogo servidor ocupado. El texto en el cuadro de diálogo no responde es ligeramente diferente que el texto en el cuadro de diálogo servidor ocupado y el botón Cancelar está deshabilitado.  
  
 *dwFlags*  
 Indicador de creación. Puede contener cero o más de los siguientes valores que se combina con el operador OR bit a bit:  
  
- **BZ_DISABLECANCELBUTTON** deshabilitar el botón de cancelación cuando el cuadro de diálogo de llamada.  
  
- **BZ_DISABLESWITCHTOBUTTON** deshabilitar el botón Cambiar a cuando se llama el cuadro de diálogo.  
  
- **BZ_DISABLERETRYBUTTON** deshabilitar el botón de reintento cuando se llama el cuadro de diálogo.  
  
 *pParentWnd*  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) a la que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana de la aplicación principal.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar el cuadro de diálogo, llame a [DoModal](#domodal).  
  
 Para obtener más información, consulte el [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) estructura en el SDK de Windows.  
  
##  <a name="domodal"></a>  COleBusyDialog::DoModal  
 Llame a esta función para mostrar el cuadro de diálogo de OLE servidor ocupado o servidor no responde.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- **IDOK** si el cuadro de diálogo se muestra correctamente.  
  
- **IDCANCEL** si el usuario canceló el cuadro de diálogo.  
  
- **IDABORT** si se produjo un error. Si **IDABORT** es devuelto, llame a la `COleDialog::GetLastError` función de miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIBusy](http://msdn.microsoft.com/library/windows/desktop/ms680125) función en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la [m_bz](#m_bz) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve **IDOK**, puede llamar a otro miembro funciones para recuperar los valores de configuración o la información que se ha especificado por el usuario en el cuadro de diálogo.  
  
##  <a name="getselectiontype"></a>  COleBusyDialog::GetSelectionType  
 Llame a esta función para obtener el tipo de selección elegido por el usuario en el cuadro de diálogo servidor ocupado.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de selección realizada.  
  
### <a name="remarks"></a>Comentarios  
 Se especifican los valores de tipo de valor devuelto por la **selección** tipo de enumeración declarado en el `COleBusyDialog` clase.  
  
```  
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```  
  
 Siguen breves descripciones de los valores siguientes:  
  
- **COleBusyDialog::switchTo** se presionó el botón Cambiar a.  
  
- **COleBusyDialog::retry** se presionó el botón de reintento.  
  
- **COleBusyDialog::callUnblocked** llamada para activar el servidor ahora está desbloqueado.  
  
##  <a name="m_bz"></a>  COleBusyDialog::m_bz  
 Estructura de tipo **OLEUIBUSY** utilizado para controlar el comportamiento del cuadro de diálogo servidor ocupado.  
  
```  
OLEUIBUSY m_bz;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) estructura en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)
