---
title: Clase CMFCDesktopAlertWndInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndInfo class
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
caps.latest.revision: 26
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
ms.openlocfilehash: 7013a7c9b29c6dc9e6324ca0490a667ed79c88f7
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdesktopalertwndinfo-class"></a>Clase CMFCDesktopAlertWndInfo
El `CMFCDesktopAlertWndInfo` clase se utiliza con la [CMFCDesktopAlertWnd clase](../../mfc/reference/cmfcdesktopalertwnd-class.md). Especifica los controles que se muestran si emerge la ventana de alerta de escritorio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCDesktopAlertWndInfo  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Identificador del icono que se muestra.|  
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|El identificador de comando asociado con un vínculo en la ventana de alerta de escritorio.|  
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|El texto que se muestra en la ventana de alerta de escritorio.|  
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|El vínculo que se muestra en la ventana de alerta de escritorio.|  
  
## <a name="remarks"></a>Comentarios  
 El `CMFCDesktopAlertWndInfo` clase se pasa a la [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) método para especificar los elementos que se muestran en el cuadro de diálogo predeterminado de la ventana de alerta de escritorio. El cuadro de diálogo predeterminado puede contener tres elementos:  
  
-   Un icono que se establece mediante una llamada a [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon).  
  
-   Una etiqueta o un mensaje de texto, que se establece mediante una llamada a [CMFCDesktopAlertWndInfo::m_strText](#m_strtext).  
  
-   Un vínculo, que se establece mediante una llamada a [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl). Para establecer el comando que se ejecuta cuando se hace clic en el vínculo, llame a [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid).  
  
 Si el cuadro de diálogo predeterminado no es suficiente, puede crear un cuadro de diálogo personalizado y lo pasa a la [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) método en lugar de utilizar esta clase. Para obtener más información, consulte [CMFCDesktopAlertDialog clase](../../mfc/reference/cmfcdesktopalertdialog-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar los diversos miembros de la `CMFCDesktopAlertWndInfo` clase. En el ejemplo se muestra cómo establecer el identificador del icono que se muestra, el texto que se muestra en la ventana de alerta de escritorio, el vínculo que se muestra en la ventana de alerta de escritorio y el identificador de comando que está asociado con un vínculo en la ventana de alerta de escritorio. Este ejemplo forma parte de la [ejemplo de demostración de alerta de escritorio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo&3;](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxDesktopAlertDialog.h  
  
##  <a name="operator_eq"></a>CMFCDesktopAlertWndInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_hicon"></a>CMFCDesktopAlertWndInfo::m_hIcon  
 Identificador del icono que se muestra.  
  
```  
HICON m_hIcon;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_nurlcmdid"></a>CMFCDesktopAlertWndInfo::m_nURLCmdID  
 El identificador de comando asociado con un vínculo en la ventana de alerta de escritorio.  
  
```  
UINT m_nURLCmdID;  
```  
  
### <a name="remarks"></a>Comentarios  
 El identificador de comando se envía al propietario de la ventana emergente cuando el usuario hace clic en el vínculo especificado por [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl).  
  
##  <a name="m_strtext"></a>CMFCDesktopAlertWndInfo::m_strText  
 El texto que se muestra en la ventana de alerta de escritorio.  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_strurl"></a>CMFCDesktopAlertWndInfo::m_strURL  
 El vínculo que se muestra en la ventana de alerta de escritorio.  
  
```  
CString m_strURL;  
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario hace clic en el vínculo, el comando que tiene el [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid) identificador de comando que se enviarán al propietario de la ventana emergente.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)   
 [Clase CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)

