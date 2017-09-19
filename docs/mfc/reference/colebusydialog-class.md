---
title: Clase de la clase COleBusyDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- Server Not Responding dialog box
- Server Busy dialog box
- COleBusyDialog class
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
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
ms.openlocfilehash: 0c3ed264cdb83bc97337f13279a20f26b21d454b
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="colebusydialog-class"></a>Clase COleBusyDialog (clase)
Se utiliza en los cuadros de diálogo que indican que el servidor OLE no responde o el servidor está ocupado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleBusyDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Construye un objeto `COleBusyDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleBusyDialog::DoModal](#domodal)|Muestra el cuadro de diálogo OLE servidor ocupado.|  
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Determina la elección realizada en el cuadro de diálogo.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleBusyDialog::m_bz](#m_bz)|Estructura de tipo **OLEUIBUSY** que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un objeto de clase `COleBusyDialog` cuando desee llamar a estos cuadros de diálogo. Después de un `COleBusyDialog` se ha construido el objeto, puede usar el [m_bz](#m_bz) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_bz` estructura es de tipo **OLEUIBUSY**. Para obtener más información acerca del uso de esta clase de cuadro de diálogo, vea la [DoModal](#domodal) función miembro.  
  
> [!NOTE]
>  Código de contenedor generados por el Asistente de la aplicación utiliza esta clase.  
  
 Para obtener más información, consulte el [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre los cuadros de diálogo OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
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
  
##  <a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog  
 Esta función sólo se crea un `COleBusyDialog` objeto.  
  
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
 Si **TRUE**, llame el cuadro de diálogo no responde en lugar del cuadro de diálogo servidor ocupado. El texto en el cuadro de diálogo no responde es ligeramente diferente que el texto en el cuadro de diálogo servidor ocupado y el botón Cancelar está deshabilitado.  
  
 `dwFlags`  
 Indicador de creación. Puede contener cero o más de los siguientes valores que se combina con el operador OR bit a bit:  
  
- **BZ_DISABLECANCELBUTTON** deshabilita el botón de cancelación al llamar el cuadro de diálogo.  
  
- **BZ_DISABLESWITCHTOBUTTON** deshabilitar el botón Cambiar a cuando se llama el cuadro de diálogo.  
  
- **BZ_DISABLERETRYBUTTON** deshabilitar el botón Reintentar al llamar el cuadro de diálogo.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar el cuadro de diálogo, llame a [DoModal](#domodal).  
  
 Para obtener más información, consulte el [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="domodal"></a>COleBusyDialog::DoModal  
 Llame a esta función para mostrar el cuadro de diálogo OLE servidor ocupado o servidor no responde.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- **IDOK** si el cuadro de diálogo se muestra correctamente.  
  
- **IDCANCEL** si el usuario cancela el cuadro de diálogo.  
  
- **IDABORT** si se produjo un error. Si **IDABORT** es devuelto, llame a la `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, consulte el [OleUIBusy](http://msdn.microsoft.com/library/windows/desktop/ms680125) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la [m_bz](#m_bz) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Si `DoModal` devuelve **IDOK**, puede llamar a otro miembro de funciones para recuperar la configuración o la información que se introduce el usuario en el cuadro de diálogo.  
  
##  <a name="getselectiontype"></a>COleBusyDialog::GetSelectionType  
 Llame a esta función para obtener el tipo de selección elegido por el usuario en el cuadro de diálogo servidor ocupado.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de selección realizada.  
  
### <a name="remarks"></a>Comentarios  
 Especifica los valores de tipo de valor devuelto por la **selección** tipo de enumeración declarado en el `COleBusyDialog` clase.  
  
```  
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```  
  
 Siguen breves descripciones de estos valores:  
  
- **COleBusyDialog::switchTo** se presionó el botón Cambiar a.  
  
- **COleBusyDialog::retry** se presionó el botón Reintentar.  
  
- **COleBusyDialog::callUnblocked** llamada para activar el servidor ya está desbloqueado.  
  
##  <a name="m_bz"></a>COleBusyDialog::m_bz  
 Estructura de tipo **OLEUIBUSY** utilizado para controlar el comportamiento del cuadro de diálogo servidor ocupado.  
  
```  
OLEUIBUSY m_bz;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)

