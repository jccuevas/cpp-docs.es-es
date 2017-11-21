---
title: Clase CMFCRibbonCustomizePropertyPage | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc2cade4bf896cb7e2f4085178c50d078aaf5f72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcribboncustomizepropertypage-class"></a>Clase CMFCRibbonCustomizePropertyPage
Implementa una página personalizada para la **personalizar** cuadro de diálogo de las aplicaciones basadas en cinta de opciones.  
  
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
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Llamado por el sistema cuando un usuario hace clic en **Aceptar** en el **personalizar** cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Si desea agregar comandos personalizados para el **personalizar** cuadro de diálogo, debe controlar el mensaje AFX_WM_ON_RIBBON_CUSTOMIZE. En el controlador de mensajes, crear instancias de un `CMFCRibbonCustomizePropertyPage` objeto en la pila. Crear una lista de comandos personalizados y, a continuación, llame a `AddCustomCategory` para agregar la nueva página a la **personalizar** cuadro de diálogo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCRibbonCustomizePropertyPage` objeto y agregar una categoría personalizada.  
  
 [!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]  
  
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
|[in] `lstIDS`|Contiene los identificadores de comando de la cinta de opciones que se mostrará en la categoría personalizada.|  
  
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
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
