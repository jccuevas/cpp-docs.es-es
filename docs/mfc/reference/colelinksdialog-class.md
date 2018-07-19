---
title: COleLinksDialog (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
dev_langs:
- C++
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5dd17c0541b573cba40146c55b46d14143209c87
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853883"
---
# <a name="colelinksdialog-class"></a>COleLinksDialog (clase)
Se utiliza en el cuadro de diálogo Editar vínculos de OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleLinksDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|Construye un objeto `COleLinksDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleLinksDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Editar vínculos OLE.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleLinksDialog::m_el](#m_el)|Una estructura de tipo OLEUIEDITLINKS que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un objeto de clase `COleLinksDialog` cuando desee llamar a este cuadro de diálogo. Después de un `COleLinksDialog` se ha construido el objeto, puede usar el [m_el](#m_el) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_el` estructura es de tipo OLEUIEDITLINKS. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.  
  
> [!NOTE]
>  Código de contenedor generados por el Asistente para la aplicación usa esta clase.  
  
 Para obtener más información, consulte el [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) estructura en el SDK de Windows.  
  
 Para obtener más información sobre los cuadros de diálogo OLE específicos, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleLinksDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxodlgs.h  
  
##  <a name="domodal"></a>  COleLinksDialog::DoModal  
 Muestra el cuadro de diálogo Editar vínculos OLE.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- IDOK si el cuadro de diálogo se mostró correctamente.  
  
- IDCANCEL si el usuario canceló el cuadro de diálogo.  
  
- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) función en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo mediante el establecimiento de los miembros de la [m_el](#m_el) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
##  <a name="colelinksdialog"></a>  COleLinksDialog::COleLinksDialog  
 Construye un objeto `COleLinksDialog`.  
  
```  
COleLinksDialog (
    COleDocument* pDoc,  
    CView* pView,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDoc*  
 Apunta al documento OLE que contiene los vínculos que se va a editar.  
  
 *pView*  
 Apunta a la vista actual en *pDoc*.  
  
 *dwFlags*  
 Indicador de creación, que contiene 0 o ELF_SHOWHELP para especificar si el botón de ayuda se mostrará cuando se muestra el cuadro de diálogo.  
  
 *pParentWnd*  
 Señala al objeto de ventana principal o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo construye un `COleLinksDialog` objeto. Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) función.  
  
##  <a name="m_el"></a>  COleLinksDialog::m_el  
 Estructura del tipo OLEUIEDITLINKS usado para controlar el comportamiento del cuadro de diálogo Editar vínculos.  
  
```  
OLEUIEDITLINKS m_el;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) estructura en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)
