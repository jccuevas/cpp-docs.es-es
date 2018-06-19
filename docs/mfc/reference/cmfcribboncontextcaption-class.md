---
title: Clase CMFCRibbonContextCaption | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2fa63de2a633b2c8a9fff975de6eaaae7cbb470c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370326"
---
# <a name="cmfcribboncontextcaption-class"></a>Clase CMFCRibbonContextCaption
Implementa una leyenda coloreada que aparece en la parte superior de una categoría de la cinta o de una categoría de contexto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonContextCaption : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonContextCaption::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCRibbonContextCaption::GetColor](#getcolor)|Devuelve el color del título.|  
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||  
|`CMFCRibbonContextCaption::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
  
## <a name="remarks"></a>Comentarios  
 No se puede crear una instancia de esta clase directamente. El [CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md) clase utiliza esta clase internamente para agregar color a las categorías de la cinta de opciones.  
  
 Para establecer el color de las categorías de la cinta de opciones, llame a [CMFCRibbonCategory:: Settabcolor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor). Para establecer el color de las categorías de contexto, llame a [CMFCRibbonBar:: Addcontextcategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonBar.h  
  
##  <a name="getcolor"></a>  CMFCRibbonContextCaption::GetColor  
 Devuelve el color de fondo del título.  
  
```  
AFX_RibbonCategoryColor GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto puede ser uno de los valores enumerados siguientes:  
  
- `AFX_CategoryColor_None`  
  
- `AFX_CategoryColor_Red`  
  
- `AFX_CategoryColor_Orange`  
  
- `AFX_CategoryColor_Yellow`  
  
- `AFX_CategoryColor_Green`  
  
- `AFX_CategoryColor_Blue`  
  
- `AFX_CategoryColor_Indigo`  
  
- `AFX_CategoryColor_Violet`  
  
### <a name="remarks"></a>Comentarios  
 El color del título se puede establecer mediante una llamada a [CMFCRibbonCategory:: Settabcolor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) o [CMFCRibbonBar:: Addcontextcategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).  
  
##  <a name="getrighttabx"></a>  CMFCRibbonContextCaption::GetRightTabX  
 Recupera la posición del borde derecho de la ficha de cinta de opciones de la categoría.  
  
```  
int GetRightTabX() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de X derecho del rectángulo envolvente de la `CMFCRibbonCategory` ficha de cinta de opciones del objeto o un valor de -1 si la ficha se trunca.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)   
 [Clase de CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
