---
title: Clase CMFCPropertyGridColorProperty | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de336692a821ba374996fac9ee7d282d2990bd08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367999"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty (clase)
La clase `CMFCPropertyGridColorProperty` admite un elemento de control de la lista de propiedades que abre un cuadro de diálogo de selección de color.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|Construye un objeto `CMFCPropertyGridColorProperty`.|  
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Habilita la *automática* botón en el cuadro de diálogo de selección de color. (El botón automático estándar tiene la etiqueta **automática**.)|  
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Habilita la *otros* botón en el cuadro de diálogo de selección de color. (El estándar otro botón tiene la etiqueta **más colores**.)|  
|`CMFCPropertyGridColorProperty::FormatProperty`|Da formato a la representación de texto de un valor de propiedad. (Invalida [cmfcpropertygridproperty:: Formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|  
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Obtiene el color actual de la propiedad.|  
|`CMFCPropertyGridColorProperty::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|`CMFCPropertyGridColorProperty::OnClickButton`|Lo llama el marco cuando el usuario hace clic en un botón que se encuentra en una propiedad. (Invalida [cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
|`CMFCPropertyGridColorProperty::OnDrawValue`|Lo llama el marco para mostrar el valor de la propiedad. (Invalida [cmfcpropertygridproperty:: Ondrawvalue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|  
|`CMFCPropertyGridColorProperty::OnEdit`|Lo llama el marco cuando el usuario está a punto de modificar un valor de propiedad. (Invalida [cmfcpropertygridproperty:: Onedit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|  
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Lo llama el marco cuando el valor de una propiedad editable ha cambiado. (Invalida [cmfcpropertygridproperty:: Onupdatevalue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|  
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Establece un nuevo color para la propiedad.|  
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Especifica el número de columnas de la cuadrícula de propiedades de color actual.|  
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Establece el valor original de una propiedad editable.|  
  
## <a name="remarks"></a>Comentarios  
 La clase `CMFCPropertyGridColorProperty` admite una propiedad de color que puede agregarse a un control de lista de propiedades. Para obtener más información, consulte el [CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la clase `CMFCPropertyGridColorProperty` y configurarlo con varios métodos de la clase `CMFCPropertyGridColorProperty`. El código explica cómo habilitar los botones automáticos y otros botones, y cómo establecer el color y el número de columnas. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridcolorproperty"></a>  CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty  
 Construye un objeto `CMFCPropertyGridColorProperty`.  
  
```  
CMFCPropertyGridColorProperty(
    const CString& strName,  
    const COLORREF& color,  
    CPalette* pPalette = NULL,  
    LPCTSTR lpszDescr = NULL,  
    DWORD_PTR dwData = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strName`  
 Nombre de la propiedad.  
  
 [in] `color`  
 El valor de la propiedad de color.  
  
 [in] `pPalette`  
 Puntero a una paleta de colores. El valor predeterminado es `NULL`.  
  
 [in] `lpszDescr`  
 La descripción de la propiedad. El valor predeterminado es `NULL`.  
  
 [in] `dwData`  
 Datos específicos de la aplicación, como un entero o un puntero a otros datos que está asociados a la propiedad. El valor predeterminado es 0.  
  
##  <a name="enableautomaticbutton"></a>  CMFCPropertyGridColorProperty::EnableAutomaticButton  
 Habilita la *automática* botón en el cuadro de diálogo de selección de color. (El botón automático estándar tiene la etiqueta **automática**.)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 El texto de la etiqueta del botón automática.  
  
 [in] `colorAutomatic`  
 El valor de color RGB del color automático (predeterminado).  
  
 [in] `bEnable`  
 `TRUE` Para habilitar el botón automático; en caso contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enableotherbutton"></a>  CMFCPropertyGridColorProperty::EnableOtherButton  
 Habilita la *otros* botón en el cuadro de diálogo de selección de color. (El estándar otro botón tiene la etiqueta **más colores**.)  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg = TRUE,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 El texto de la etiqueta del otro botón.  
  
 [in] `bAltColorDlg`  
 `TRUE` para mostrar la `CMFCColorDialog` cuadro de diálogo; `FALSE` para mostrar el cuadro de diálogo de selección de color estándar. El valor predeterminado es `TRUE`.  
  
 [in] `bEnable`  
 `TRUE` para mostrar el botón de otro; en caso contrario, `FALSE`.  El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcolor"></a>  CMFCPropertyGridColorProperty::GetColor  
 Obtiene el color actual de la propiedad.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setcolor"></a>  CMFCPropertyGridColorProperty::SetColor  
 Establece un nuevo color para la propiedad.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setcolumnsnumber"></a>  CMFCPropertyGridColorProperty::SetColumnsNumber  
 Especifica el número de columnas de la cuadrícula de propiedades de color actual.  
  
```  
void SetColumnsNumber(int nColumnsNumber);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nColumnsNumber`  
 El número preferido de las columnas en la cuadrícula de propiedades de color.  
  
### <a name="remarks"></a>Comentarios  
 Este método establece el valor de la `m_nColumnsNumber` protegido miembro de datos.  
  
##  <a name="setoriginalvalue"></a>  CMFCPropertyGridColorProperty::SetOriginalValue  
 Establece el valor original de una propiedad editable.  
  
```  
virtual void SetOriginalValue(const COleVariant& varValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `varValue`  
 Un valor.  
  
### <a name="remarks"></a>Comentarios  
 Use la [cmfcpropertygridproperty:: Resetoriginalvalue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) método para restablecer el valor original de una propiedad editada.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty (clase)](../../mfc/reference/cmfcpropertygridproperty-class.md)
