---
title: Clase COleUpdateDialog | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54088de4c07f1c58656aad468160ef58f0e41398
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373056"
---
# <a name="coleupdatedialog-class"></a>Clase COleUpdateDialog
Se utiliza para un caso especial del cuadro de diálogo Editar vínculos de OLE, que se debe utilizar cuando se necesita actualizar solo los objetos existentes vinculados o incrustados en un documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleUpdateDialog : public COleLinksDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Construye un objeto `COleUpdateDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleUpdateDialog::DoModal](#domodal)|Muestra el **editar vínculos** cuadro de diálogo en un modo de actualización.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre los cuadros de diálogo de OLE específico, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
 `COleUpdateDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxodlgs.h  
  
##  <a name="coleupdatedialog"></a>  COleUpdateDialog::COleUpdateDialog  
 Construye un objeto `COleUpdateDialog`.  
  
```  
explicit COleUpdateDialog(
    COleDocument* pDoc,  
    BOOL bUpdateLinks = TRUE,  
    BOOL bUpdateEmbeddings = FALSE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDoc`  
 Señala el documento que contiene los vínculos que necesiten actualizarse.  
  
 *bUpdateLinks*  
 Marca que determina si los objetos vinculados deben actualizarse.  
  
 *bUpdateEmbeddings*  
 Marca que determina si los objetos incrustados se actualizará.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) a la que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del cuadro de diálogo se establecerá en la ventana de la aplicación principal.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo crea una `COleUpdateDialog` objeto. Para mostrar el cuadro de diálogo, llame a [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Esta clase debe utilizarse en lugar de `COleLinksDialog` si desea actualizar las existentes solo elementos vinculados o incrustados.  
  
##  <a name="domodal"></a>  COleUpdateDialog::DoModal  
 Muestra el cuadro de diálogo Editar vínculos en modo de actualización.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- **IDOK** si el cuadro de diálogo se devolvió correctamente.  
  
- **IDCANCEL** si ninguno de los elementos vinculados o incrustados en el documento actual es necesario actualizar.  
  
- **IDABORT** si se produjo un error. Si **IDABORT** es devuelto, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función de miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) función en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Todos los vínculos o incrustaciones se actualizan a menos que el usuario selecciona el botón Cancelar.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [Clase COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleLinksDialog (clase)](../../mfc/reference/colelinksdialog-class.md)
