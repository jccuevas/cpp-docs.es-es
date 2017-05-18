---
title: Clase CFolderPickerDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
dev_langs:
- C++
helpviewer_keywords:
- CFolderPickerDialog class
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 0d020544a16056d3f4db538750ed5a16b54f9a51
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cfolderpickerdialog-class"></a>Clase CFolderPickerDialog
Clase CFolderPickerDialog implementa CFileDialog en el modo de selector de carpetas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFolderPickerDialog : public CFileDialog;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFolderPickerDialog:: ~ CFolderPickerDialog](#cfolderpickerdialog__~cfolderpickerdialog)|Destructor.|  
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|Constructor.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [CFileDialog](../../mfc/reference/cfiledialog-class.md)  
  
 `CFolderPickerDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdlgs.h  
  
##  <a name="cfolderpickerdialog"></a>CFolderPickerDialog::CFolderPickerDialog  
 Constructor.  
  
```  
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL,  
    DWORD dwSize = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFolder`  
 Carpeta inicial.  
  
 `dwFlags`  
 Una combinación de uno o más indicadores que le permiten personalizar el cuadro de diálogo.  
  
 `pParentWnd`  
 Puntero a la ventana de primario o el propietario del objeto de cuadro de diálogo.  
  
 `dwSize`  
 El tamaño de la estructura OPENFILENAME.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="_dtorcfolderpickerdialog"></a>CFolderPickerDialog:: ~ CFolderPickerDialog  
 Destructor.  
  
```  
virtual ~CFolderPickerDialog();
```  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

