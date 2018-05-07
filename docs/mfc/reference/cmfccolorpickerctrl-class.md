---
title: Clase CMFCColorPickerCtrl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad7e67cc32621fc30108767493c3a7bffd481b68
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfccolorpickerctrl-class"></a>Clase CMFCColorPickerCtrl
La `CMFCColorPickerCtrl` clase proporciona funcionalidad para un control que se utiliza para seleccionar colores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCColorPickerCtrl : public CButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Construye un objeto `CMFCColorPickerCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::GetColor](#getcolor)|Recupera el color que el usuario seleccione.|  
|[CMFCColorPickerCtrl::GetHLS](#gethls)|Recupera los valores de matiz, luminancia y la saturación del color que el usuario seleccione.|  
|[CMFCColorPickerCtrl::GetHue](#gethue)|Recupera el componente de matiz del color que el usuario seleccione.|  
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|Recupera el componente de luminancia del color que el usuario seleccione.|  
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|Recupera el componente de saturación del color que el usuario seleccione.|  
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Establece el color actual en el color definido por los componentes de color RGB especificados o los hexágonos celda especificada.|  
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Establece el color actual en el valor de color RGB especificado.|  
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Establece el color actual en el valor de color HLS especificado.|  
|[CMFCColorPickerCtrl::SetHue](#sethue)|Cambia el componente de matiz del color actualmente seleccionado.|  
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Cambia el componente de luminancia del color actualmente seleccionado.|  
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Establece el ancho de la barra de luminancia en el control de selector de color.|  
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Establece el color seleccionado inicial.|  
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Establece la paleta de colores actual.|  
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Cambia el componente de saturación del color actualmente seleccionado.|  
|[CMFCColorPickerCtrl::SetType](#settype)|Establece el tipo de control de selector de color para mostrar.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Llamado por el marco de trabajo antes de que se muestra un cursor que apunta al color seleccionado.|  
  
## <a name="remarks"></a>Comentarios  
 Colores estándar están seleccionados de una paleta de colores hexagonal y colores personalizados estén seleccionados en una barra de luminancia donde colores se especifican utilizando la notación rojo/verde/azul o notación de matiz/satuaration/luminancia.  
  
 La siguiente ilustración muestra varios `CMFCColorPickerCtrl` objetos.  
  
 ![Cuadro de diálogo CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "colorpicker")  
  
 El `CMFCColorPickerCtrl` admite dos pares de estilos. Los estilos HEXADECIMAL y HEX_GREYSCALE son adecuados para la selección de color estándar. Los estilos de SELECTOR y LUMINANCIA son adecuados para la selección de color personalizado.  
  
 Realice los pasos siguientes para incorporar el `CMFCColorPickerCtrl` control en el cuadro de diálogo:  
  
1.  Si usas el **ClassWizard**, inserte un nuevo control de botón en la plantilla de cuadro de diálogo (porque el `CMFCColorPickerCtrl` clase se hereda de la `CButton` clase).  
  
2.  Insertar una variable de miembro que está asociada con el nuevo control de botón a la clase de cuadro de diálogo. A continuación, cambie el tipo de variable de `CButton` a `CMFCColorPickerCtrl`.  
  
3.  Insertar el `WM_INITDIALOG` el controlador de mensajes para la clase de cuadro de diálogo. En el controlador, establezca el tipo, la paleta y el color seleccionado inicial de la `CMFCColorPickerCtrl` control.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar un `CMFCColorPickerCtrl` objeto con varios métodos en la `CMFCColorPickerCtrl` clase. En el ejemplo se muestra cómo establecer el tipo de control de selector de y cómo establecer su color, el matiz, la luminancia y la saturación. El ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcolorpickerctrl.h  
  
##  <a name="cmfccolorpickerctrl"></a>  CMFCColorPickerCtrl::CMFCColorPickerCtrl  
 Construye un objeto `CMFCColorPickerCtrl`.  
  
```  
CMFCColorPickerCtrl();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="drawcursor"></a>  CMFCColorPickerCtrl::DrawCursor  
 Llamado por el marco de trabajo antes de que se muestra un cursor que apunta al color seleccionado.  
  
```  
virtual void DrawCursor(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Especifica un área rectangular que rodea del color seleccionado.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método cuando necesite cambiar la forma del cursor que apunta al color seleccionado.  
  
##  <a name="getcolor"></a>  CMFCColorPickerCtrl::GetColor  
 Recupera el color que el usuario seleccione.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor RGB del color seleccionado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gethls"></a>  CMFCColorPickerCtrl::GetHLS  
 Recupera los valores de matiz, luminancia y la saturación del color que el usuario seleccione.  
  
```  
void GetHLS(
    double* hue,  
    double* luminance,  
    double* saturation);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `hue`  
 Puntero a una variable de tipo double que recibe información de matiz.  
  
 [out] `luminance`  
 Puntero a una variable de tipo double que recibe información de luminancia.  
  
 [out] `saturation`  
 Puntero a una variable de tipo double que recibe información de saturación.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue  
 Recupera el componente de matiz del color que el usuario seleccione.  
  
```  
double GetHue() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El componente de matiz del color seleccionado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance  
 Recupera el componente de luminancia del color que el usuario seleccione.  
  
```  
double GetLuminance() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El componente de luminancia del color seleccionado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation  
 Recupera el valor de saturación del color que el usuario seleccione.  
  
```  
double GetSaturation() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El componente de saturación del color seleccionado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon  
 Establece el color actual en el color definido por los componentes de color RGB especificados o los hexágonos celda especificada.  
  
```  
void SelectCellHexagon(
    BYTE R,  
    BYTE G,  
    BYTE B);

 
BOOL SelectCellHexagon(
    int x,  
    int y);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `R`  
 El componente de color rojo.  
  
 [in] `G`  
 El componente de color verde.  
  
 [in] `B`  
 El componente de color azul.  
  
 [in] `x`  
 La coordenada x del cursor, que señala a un hexágonos de celda.  
  
 [in] `y`  
 Coordenada y del cursor, que señala a un hexágonos de celda.  
  
### <a name="return-value"></a>Valor devuelto  
 La segunda sobrecarga de este método siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 La primera sobrecarga de este método establece la actual de color en el color que se corresponde con el control de selección de color especificado del componentes de color rojo, verde y azul.  
  
 La segunda sobrecarga de este método establece el color actual en el color de los hexágonos de celda que apunta a la ubicación del cursor especificado.  
  
##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor  
 Establece el color actual en el valor de color RGB especificado.  
  
```  
void SetColor(COLORREF Color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `Color`  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS  
 Establece el color actual en el valor de color HLS especificado.  
  
```  
void SetHLS(
    double hue,  
    double luminance,  
    double saturation,  
    BOOL bInvalidate=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hue`  
 Un valor de matiz.  
  
 [in] `luminance`  
 Un valor de luminancia.  
  
 [in] `saturation`  
 Un valor de saturación.  
  
 [in] `bInvalidate`  
 `TRUE` Para forzar la ventana para actualizar inmediatamente el nuevo color; en caso contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue  
 Cambia el matiz del color actualmente seleccionado.  
  
```  
void SetHue(double Hue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `Hue`  
 Un valor de matiz.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance  
 Cambia la luminancia del color actualmente seleccionado.  
  
```  
void SetLuminance(double Luminance);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `Luminance`  
 Un valor de luminancia.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth  
 Establece el ancho de la barra de luminancia en el control de selector de color.  
  
```  
void SetLuminanceBarWidth(int w);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `w`  
 El ancho de la barra de luminancia expresado en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para cambiar el tamaño de la barra de luminancia, que se encuentra en la **personalizado** ficha del control de selector de color. El `w` parámetro especifica el nuevo ancho de la barra de luminancia. Si se supera tres cuartas partes del ancho del área de cliente, se omite el valor de ancho.  
  
##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor  
 Establece el color seleccionado inicial.  
  
```  
void SetOriginalColor(COLORREF ref);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ref`  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método cuando se inicializa el control de selector de color.  
  
##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette  
 Establece la paleta de colores actual.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPalette`  
 Puntero a una paleta de colores.  
  
### <a name="remarks"></a>Comentarios  
 La paleta de colores define la matriz de colores que se muestra en el control de selector de color.  
  
##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation  
 Cambia la saturación del color actualmente seleccionado.  
  
```  
void SetSaturation(double Saturation);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `Saturation`  
 Un valor de saturación.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType  
 Establece el tipo de control de selector de color para mostrar.  
  
```  
void SetType(COLORTYPE colorType);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `colorType`  
 Un tipo de control de selector de color.  
  
 Los tipos se definen mediante el `CMFCColorPickerCtrl::COLORTYPE` enumeración. Los tipos posibles son `LUMINANCE`, `PICKER`, `HEX` y `HEX_GREYSCALE`. El tipo predeterminado es `PICKER`.  
  
### <a name="remarks"></a>Comentarios  
 Para especificar un tipo de control de selector de color, llame a este método antes de crea el control de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md)
