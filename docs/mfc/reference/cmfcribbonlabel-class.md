---
title: Clase CMFCRibbonLabel | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonLabel
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonLabel class
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b93e0f6c46818515c8d6bcd8d71b78dcaa435ea6
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonlabel-class"></a>Clase CMFCRibbonLabel
Implementa una etiqueta de texto no seleccionable en una cinta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonLabel : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Construye e inicializa un `CMFCRibbonLabel` objeto con la cadena de texto especificado.|  
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCRibbonLabel::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonLabel::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Determina los datos de accesibilidad para el elemento de etiqueta de cinta actual. (Invalida [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
  
### <a name="remarks"></a>Comentarios  
 Después de crear una etiqueta de cinta de opciones, agregarlo a un panel mediante una llamada a [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
 No se puede agregar una etiqueta de cinta de opciones en la barra de herramientas de acceso rápido.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonLabel.h  
  
##  <a name="a-namecmfcribbonlabela--cmfcribbonlabelcmfcribbonlabel"></a><a name="cmfcribbonlabel"></a>CMFCRibbonLabel::CMFCRibbonLabel  
 Construye e inicializa un [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md) objeto que muestra la cadena de texto especificado.  
  
```  
CMFCRibbonLabel(
    LPCTSTR lpszText,  
    BOOL bIsMultiLine = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszText`  
 El texto que aparecerá en la etiqueta.  
  
 [in] `bIsMultiLine`  
 `TRUE`para especificar que la etiqueta es una etiqueta de varias líneas; de lo contrario, `FALSE`.  
  
##  <a name="a-namesetaccdataa--cmfcribbonlabelsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonLabel::SetACCData  
 Determina los datos de accesibilidad para el elemento de etiqueta de cinta actual.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParent`  
 Representa la ventana primaria de la etiqueta de cinta actual.  
  
 [out] `data`  
 Un objeto del tipo `CAccessibilityData` que se rellena con los datos de la accesibilidad de la etiqueta de cinta actual.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el `data` parámetro era correctamente rellenado con los datos de la accesibilidad de la etiqueta de cinta actual; en caso contrario, `FALSE`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

