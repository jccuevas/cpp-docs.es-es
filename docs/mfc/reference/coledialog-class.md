---
title: Clase COleDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDialog
dev_langs:
- C++
helpviewer_keywords:
- OLE dialog boxes, base class
- dialog boxes, OLE
- COleDialog class
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
caps.latest.revision: 21
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
ms.openlocfilehash: 018d06ac167a8c352d9f1822b373126c4e615854
ms.lasthandoff: 02/24/2017

---
# <a name="coledialog-class"></a>Clase COleDialog
Proporciona funcionalidad común a los cuadros de diálogo para OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDialog::GetLastError](#getlasterror)|Obtiene el código de error devuelto por el cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 La biblioteca Microsoft Foundation Class proporciona varias clases derivadas de `COleDialog`:  
  
- [Clase COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)  
  
- [Clase COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)  
  
- [Clase COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)  
  
- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
- [Clase COleBusyDialog](../../mfc/reference/colebusydialog-class.md)  
  
- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)  
  
- [Clase COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)  
  
- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)  
  
- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)  
  
 Para obtener más información acerca de cuadros de diálogo OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `COleDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxodlgs.h  
  
##  <a name="a-namegetlasterrora--coledialoggetlasterror"></a><a name="getlasterror"></a>COleDialog::GetLastError  
 Llame a la `GetLastError` función miembro para obtener información de error adicional cuando `DoModal` devuelve **IDABORT**.  
  
```  
UINT GetLastError() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Los códigos de error devueltos por `GetLastError` dependen en el cuadro de diálogo específico.  
  
### <a name="remarks"></a>Comentarios  
 Consulte la `DoModal` función miembro en las clases derivadas para obtener información acerca de los mensajes de error específico.  
  
## <a name="see-also"></a>Vea también  
 [Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




