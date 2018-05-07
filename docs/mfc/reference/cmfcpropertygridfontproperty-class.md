---
title: Clase CMFCPropertyGridFontProperty | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e7acda3bf3734a325c7d603489c1305cb63bc3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcpropertygridfontproperty-class"></a>Clase CMFCPropertyGridFontProperty
La `CMFCPropertyGridFileProperty` clase es compatible con un elemento de control de lista de propiedades que se abre un cuadro de diálogo de selección de fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Construye un objeto `CMFCPropertyGridFontProperty`.|  
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCPropertyGridFontProperty::FormatProperty`|Da formato a la representación de texto de un valor de propiedad. (Invalida [cmfcpropertygridproperty:: Formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|  
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Recupera el color de fuente que el usuario selecciona en el cuadro de diálogo fuente.|  
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Recupera la fuente que el usuario selecciona en el cuadro de diálogo fuente.|  
|`CMFCPropertyGridFontProperty::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|`CMFCPropertyGridFontProperty::OnClickButton`|Lo llama el marco cuando el usuario hace clic en un botón que se encuentra en una propiedad. (Invalida [cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty  
 Construye un objeto `CMFCPropertyGridFontProperty`.  
  
```  
CMFCPropertyGridFontProperty(
    const CString& strName,  
    LOGFONT& lf,  
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,  
    LPCTSTR lpszDescr = NULL,  
    DWORD_PTR dwData = 0,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strName`  
 Nombre de la propiedad.  
  
 [in] `lf`  
 Una estructura de fuente lógica que especifica los atributos de la fuente.  
  
 [in] `dwFontDialogFlags`  
 Estilos que se aplican al cuadro de diálogo fuente que se muestra al hacer clic en el botón de lista desplegable del valor de propiedad. El valor predeterminado es la combinación bit a bit (OR) de CF_EFFECTS y CF_SCREENFONTS. Para obtener más información, consulte el `Flags` parámetro de la [CHOOSEFONT estructura](http://msdn.microsoft.com/library/windows/desktop/ms646832).  
  
 [in] `lpszDescr`  
 Descripción de la propiedad font. El valor predeterminado es `NULL`.  
  
 [in] `dwData`  
 Datos específicos de la aplicación, como un entero o un puntero a otros datos que está asociados a la propiedad. El valor predeterminado es 0.  
  
 [in] `color`  
 El color de la fuente. El valor predeterminado es el color predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Un `CMFCPropertyGridFontProperty` objeto representa una propiedad de fuente en un control de fuente de cuadrícula de propiedades.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCPropertyGridFontProperty` clase. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]  
  
##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor  
 Recupera el color de fuente que el usuario selecciona en el cuadro de diálogo fuente.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de color RGB que representa el color de fuente seleccionada.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont  
 Recupera la fuente que el usuario selecciona en el cuadro de diálogo fuente.  
  
```  
LPLOGFONT GetLogFont();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura que describe la fuente seleccionada.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty (clase)](../../mfc/reference/cmfcpropertygridproperty-class.md)
