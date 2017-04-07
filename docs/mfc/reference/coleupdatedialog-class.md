---
title: Clase COleUpdateDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- Update dialog
- links [C++], updating
- updating OLE links
- OLE dialog boxes, Edit Link
- OLE link updating
- COleUpdateDialog class
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 8066a8dc9e572c14e9423af62d340e249351ac11
ms.lasthandoff: 02/24/2017

---
# <a name="coleupdatedialog-class"></a>Clase COleUpdateDialog
Se utiliza para un caso especial del cuadro de diálogo Editar vínculos de OLE, que se debe utilizar cuando se necesita actualizar solo los objetos existentes vinculados o incrustados en un documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleUpdateDialog : public COleLinksDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Construye un objeto `COleUpdateDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleUpdateDialog::DoModal](#domodal)|Muestra el **editar vínculos** cuadro de diálogo en el modo de actualización.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre los cuadros de diálogo OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
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
  
##  <a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog  
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
 Señala el documento que contiene los vínculos que puede ser necesario actualizar.  
  
 *bUpdateLinks*  
 Marca que determina si los objetos vinculados deben actualizarse.  
  
 *bUpdateEmbeddings*  
 Marca que determina si se puede actualizar los objetos incrustados.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es **NULL**, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Esta función sólo crea un `COleUpdateDialog` objeto. Para mostrar el cuadro de diálogo, llame a [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Esta clase debe utilizarse en lugar de `COleLinksDialog` cuando desee actualizar existente solo elementos vinculados o incrustados.  
  
##  <a name="domodal"></a>COleUpdateDialog::DoModal  
 Muestra el cuadro de diálogo Editar vínculos en modo de actualización.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:  
  
- **IDOK** si el cuadro de diálogo se devolvió correctamente.  
  
- **IDCANCEL** si ninguno de los elementos vinculados o incrustados en el documento actual es necesario actualizar.  
  
- **IDABORT** si se produjo un error. Si **IDABORT** es devuelto, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, consulte el [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Todos los vínculos o incrustaciones se actualizan a menos que el usuario selecciona el botón Cancelar.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [Clase COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

