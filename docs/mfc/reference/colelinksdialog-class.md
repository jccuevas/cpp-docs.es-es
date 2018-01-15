---
title: Clase COleLinksDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
dev_langs: C++
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9b998cc18ac0c357b57bc841f6db13700b078063
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="colelinksdialog-class"></a>Clase COleLinksDialog
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
|[COleLinksDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Editar vínculos de OLE.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleLinksDialog::m_el](#m_el)|Una estructura de tipo **OLEUIEDITLINKS** que controla el comportamiento del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un objeto de clase `COleLinksDialog` cuando desee llamar a este cuadro de diálogo. Después de un `COleLinksDialog` se ha construido el objeto, puede usar el [m_el](#m_el) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_el` estructura es de tipo **OLEUIEDITLINKS**. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.  
  
> [!NOTE]
>  Código de contenedor generados por el Asistente de la aplicación utiliza esta clase.  
  
 Para obtener más información, consulte el [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) estructura en el SDK de Windows.  
  
 Para obtener más información sobre los cuadros de diálogo de OLE específico, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
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
  
##  <a name="domodal"></a>COleLinksDialog::DoModal  
 Muestra el cuadro de diálogo Editar vínculos de OLE.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- **IDOK** si el cuadro de diálogo se muestra correctamente.  
  
- **IDCANCEL** si el usuario canceló el cuadro de diálogo.  
  
- **IDABORT** si se produjo un error. Si **IDABORT** es devuelto, llame a la `COleDialog::GetLastError` función de miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) función en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la [m_el](#m_el) estructura, debe hacer antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
##  <a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog  
 Construye un objeto `COleLinksDialog`.  
  
```  
COleLinksDialog (
    COleDocument* pDoc,  
    CView* pView,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDoc`  
 Señala al documento OLE que contiene los vínculos que se pueda editar.  
  
 `pView`  
 Apunta a la vista actual en `pDoc`.  
  
 `dwFlags`  
 Indicador de creación, que contiene 0 o **ELF_SHOWHELP** para especificar si el botón de ayuda se mostrará cuando se muestra el cuadro de diálogo.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) a la que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del cuadro de diálogo se establece en la ventana de la aplicación principal.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo crea una `COleLinksDialog` objeto. Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) función.  
  
##  <a name="m_el"></a>COleLinksDialog::m_el  
 Estructura de tipo **OLEUIEDITLINKS** utilizado para controlar el comportamiento del cuadro de diálogo Editar vínculos.  
  
```  
OLEUIEDITLINKS m_el;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.  
  
 Para obtener más información, consulte el [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) estructura en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)
