---
title: Clase CMFCRibbonCustomizePropertyPage | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
dev_langs:
- C++
helpviewer_keywords:
- ~CMFCRibbonCustomizePropertyPage destructor
- CMFCRibbonCustomizePropertyPage class, destructor
- GetThisClass method
- CreateObject method
- CMFCRibbonCustomizePropertyPage class
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 83323142441de13140383152a32122bf1644003f
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncustomizepropertypage-class"></a>Clase CMFCRibbonCustomizePropertyPage
Implementa una página personalizada para la **personalizar** cuadro de diálogo en aplicaciones basadas en cinta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Construye un objeto `CMFCRibbonCustomizePropertyPage`.|  
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Agrega una categoría personalizada a la **comandos** cuadro combinado.|  
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Llamado por el sistema cuando un usuario hace clic en **Aceptar** en el **personalizar** cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Si desea agregar comandos personalizados a la **personalizar** cuadro de diálogo, debe controlar el mensaje AFX_WM_ON_RIBBON_CUSTOMIZE. En el controlador de mensajes, crear una instancia de un `CMFCRibbonCustomizePropertyPage` objeto en la pila. Crear una lista de comandos personalizados y, a continuación, llame a `AddCustomCategory` para agregar la nueva página para la **personalizar** cuadro de diálogo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCRibbonCustomizePropertyPage` objeto y para agregar una categoría personalizada.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#22;](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
 [CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribboncustomizedialog.h  
  
##  <a name="addcustomcategory"></a>CMFCRibbonCustomizePropertyPage::AddCustomCategory  
 Agrega una categoría personalizada a la **comandos** cuadro combinado.  
  
```  
void AddCustomCategory(
    LPCTSTR lpszName,  
    const CList<UINT, UINT>& lstIDS);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `lpszName`|Especifica el nombre de la categoría personalizada.|  
|[in] `lstIDS`|Contiene los identificadores de comando de cinta de opciones que se mostrará en la categoría personalizada.|  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega una categoría denominada `lpszName` a la **comandos** cuadro combinado. Cuando el usuario selecciona la categoría, los comandos especifican en `lstIDS` aparecen en la lista de comandos.  
  
##  <a name="cmfcribboncustomizepropertypage"></a>CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage  
 Construye un objeto `CMFCRibbonCustomizePropertyPage`.  
  
```  
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRibbonBar`  
 Un puntero a un control de la cinta de opciones para que las opciones para personalizar.  
  
##  <a name="onok"></a>CMFCRibbonCustomizePropertyPage::OnOK  
 Calleld por el sistema cuando un usuario hace clic en **Aceptar** en el **personalizar** cuadro de diálogo.  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada aplica a las opciones seleccionadas en el **personalizar** cuadro de diálogo para la barra de herramientas de acceso rápido.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

