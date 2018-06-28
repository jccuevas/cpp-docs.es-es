---
title: Clase CMFCRibbonLabel | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36b2d78bb3f1ffaefa67a062c6498c195d46336f
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042500"
---
# <a name="cmfcribbonlabel-class"></a>Clase CMFCRibbonLabel
Implementa una etiqueta de texto no seleccionable en una cinta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonLabel : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Construye e inicializa un `CMFCRibbonLabel` objeto con la cadena de texto especificada.|  
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonLabel::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonLabel::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Determina los datos de accesibilidad para el elemento de etiqueta de cinta actual. (Invalida [cmfcribbonbutton:: Setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
  
### <a name="remarks"></a>Comentarios  
 Después de crear una etiqueta de cinta de opciones, agréguelo a un panel mediante una llamada a [cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
 No se puede agregar una etiqueta de cinta de opciones en la barra de herramientas de acceso rápido.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonLabel.h  
  
##  <a name="cmfcribbonlabel"></a>  CMFCRibbonLabel::CMFCRibbonLabel  
 Construye e inicializa un [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md) objeto que muestra la cadena de texto especificado.  
  
```  
CMFCRibbonLabel(
    LPCTSTR lpszText,  
    BOOL bIsMultiLine = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpszText*  
 El texto que aparecerá en la etiqueta.  
  
 [in] *bIsMultiLine*  
 `TRUE` para especificar que la etiqueta es una etiqueta de varias líneas; en caso contrario, `FALSE`.  
  
##  <a name="setaccdata"></a>  CMFCRibbonLabel::SetACCData  
 Determina los datos de accesibilidad para el elemento de etiqueta de cinta actual.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pParent*  
 Representa la ventana primaria de la etiqueta de cinta actual.  
  
 [out] *datos*  
 Un objeto del tipo `CAccessibilityData` que se rellena con los datos de accesibilidad de la etiqueta de cinta actual.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si el *datos* parámetro se rellena con los datos de accesibilidad de la etiqueta de cinta actual correctamente; en caso contrario, `FALSE`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)
