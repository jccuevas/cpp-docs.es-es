---
title: CMFCToolTipInfo (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
ms.openlocfilehash: 000a2fd33928e59685efa6f145406542a4935819
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377339"
---
# <a name="cmfctooltipinfo-class"></a>CMFCToolTipInfo (Clase)

Almacena información sobre el aspecto visual de la información sobre herramientas.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolTipInfo
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolTipInfo::operator=](#operator_eq)||

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|Variable booleana que indica si la información sobre herramientas tiene apariencia de globo.|
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Variable booleana que indica si las etiquetas de información sobre herramientas se muestran en negrita.|
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Variable booleana que indica si la información sobre herramientas contiene una descripción.|
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Variable booleana que indica si la información sobre herramientas contiene un icono.|
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Variable booleana que indica si se muestra un separador entre la etiqueta de información sobre herramientas y la descripción de la información sobre herramientas.|
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Variable booleana que indica si la información sobre herramientas tiene esquinas redondeadas.|
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Variable booleana que indica si un administrador visual debe controlar la apariencia de la información sobre herramientas (consulte [CMFCVisualManager (Clase).](../../mfc/reference/cmfcvisualmanager-class.md)|
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Color del borde de la información sobre herramientas.|
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Color del fondo de la información sobre herramientas.|
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Color del relleno de degradado en la información sobre herramientas.|
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Color del texto en la información sobre herramientas.|
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Ángulo del relleno de degradado en la información sobre herramientas.|
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Ancho máximo posible, en píxeles, de la descripción en la información sobre herramientas.|

## <a name="remarks"></a>Observaciones

Use [CMFCToolTipCtrl (Clase)](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`y [CTooltipManager (clase)](../../mfc/reference/ctooltipmanager-class.md) juntos para implementar información sobre herramientas personalizada en la aplicación. Para obtener un ejemplo de cómo utilizar estas clases de información sobre herramientas, vea el [CMFCToolTipCtrl tema.](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo establecer los valores de las distintas variables de miembro en la clase `CMFCToolTipInfo`.

[!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtooltipctrl.h

## <a name="cmfctooltipinfom_bballoontooltip"></a><a name="m_bballoontooltip"></a>CMFCToolTipInfo::m_bBalloonTooltip

Especifica el estilo de visualización de todas las descripciones emergentes.

```
BOOL m_bBalloonTooltip;
```

### <a name="remarks"></a>Observaciones

TRUE indica que la información sobre herramientas utiliza el estilo de globo, FALSE indica que la información sobre herramientas utiliza el estilo rectangular.

## <a name="cmfctooltipinfom_bboldlabel"></a><a name="m_bboldlabel"></a>CMFCToolTipInfo::m_bBoldLabel

Especifica si la fuente del texto de información sobre herramientas está en negrita.

```
BOOL m_bBoldLabel;
```

### <a name="remarks"></a>Observaciones

Establezca este miembro en TRUE para mostrar texto de información sobre herramientas con fuente en negrita, o FALSE para mostrar etiquetas de información sobre herramientas con fuente no negrita.

## <a name="cmfctooltipinfom_bdrawdescription"></a><a name="m_bdrawdescription"></a>CMFCToolTipInfo::m_bDrawDescription

Especifica si cada información sobre herramientas muestra texto de descripción.

```
BOOL m_bDrawDescription;
```

### <a name="remarks"></a>Observaciones

Establezca este miembro en TRUE para mostrar la descripción o FALSE para ocultar la descripción. Puede especificar la descripción en una información sobre herramientas llamando a [CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)

## <a name="cmfctooltipinfom_bdrawicon"></a><a name="m_bdrawicon"></a>CMFCToolTipInfo::m_bDrawIcon

Especifica si todas las descripciones emergentes muestran iconos.

```
BOOL m_bDrawIcon;
```

### <a name="remarks"></a>Observaciones

Establezca este miembro en TRUE para mostrar un icono en cada información sobre herramientas o FALSE para mostrar información sobre herramientas sin iconos.

## <a name="cmfctooltipinfom_bdrawseparator"></a><a name="m_bdrawseparator"></a>CMFCToolTipInfo::m_bDrawSeparator

Especifica si cada información sobre herramientas tiene un separador entre su etiqueta y su descripción.

```
BOOL m_bDrawSeparator;
```

### <a name="remarks"></a>Observaciones

Establezca este miembro en TRUE para mostrar el separador entre la etiqueta y la descripción de la información sobre herramientas, o FALSE para mostrar información sobre herramientas sin separador.

## <a name="cmfctooltipinfom_broundedcorners"></a><a name="m_broundedcorners"></a>CMFCToolTipInfo::m_bRoundedCorners

Especifica si todas las descripciones emergentes tienen esquinas redondeadas.

```
BOOL m_bRoundedCorners;
```

### <a name="remarks"></a>Observaciones

Establezca este miembro en TRUE para mostrar las esquinas redondeadas en la información sobre herramientas o FALSE para mostrar las esquinas rectangulares en la información sobre herramientas.

## <a name="cmfctooltipinfom_clrborder"></a><a name="m_clrborder"></a>CMFCToolTipInfo::m_clrBorder

Especifica el color de los bordes en todas las descripciones emergentes.

```
COLORREF m_clrBorder;
```

## <a name="cmfctooltipinfom_clrfill"></a><a name="m_clrfill"></a>CMFCToolTipInfo::m_clrFill

Especifica el color de los fondos de información sobre herramientas.

```
COLORREF m_clrFill;
```

### <a name="remarks"></a>Observaciones

Si [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) es -1, el `m_clrFill`color de fondo de la información sobre herramientas es . De `m_clrFill` lo contrario, especifica el color `m_clrFillGradient` del principio del degradado y especifica el color del final del degradado. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) determina la dirección del degradado.

## <a name="cmfctooltipinfom_clrfillgradient"></a><a name="m_clrfillgradient"></a>CMFCToolTipInfo::m_clrFillGradient

Especifica el color final de un fondo degradado para la información sobre herramientas.

```
COLORREF m_clrFillGradient;
```

### <a name="remarks"></a>Observaciones

Si `m_clrFillGradient` es -1, no hay degradado. De lo contrario, [CMFCToolTipInfo::m_clrFill](#m_clrfill) especifica el color inicial del degradado `m_clrFillGradient`y el color de acabado de degradado se especifica mediante . [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) determina la dirección del degradado.

## <a name="cmfctooltipinfom_clrtext"></a><a name="m_clrtext"></a>CMFCToolTipInfo::m_clrText

Especifica el color del texto de todas las descripciones emergentes.

```
COLORREF m_clrText;
```

## <a name="cmfctooltipinfom_ngradientangle"></a><a name="m_ngradientangle"></a>CMFCToolTipInfo::m_nGradientAngle

Especifica el ángulo en el que se dibuja un degradado en el fondo de la información sobre herramientas.

```
int m_nGradientAngle;
```

### <a name="remarks"></a>Observaciones

`m_nGradientAngle`especifica el ángulo, en grados, que el degradado en el fondo de la información sobre herramientas se desfasa de horizontal. Si `m_nGradientAngle` es 0, el degradado se dibuja de izquierda a derecha. Si `m_nGradientAngle` está entre 1 y 360, el degradado gira en el sentido de las agujas del reloj por ese número de grados. Si `m_nGradientAngle` es -1, que es el valor predeterminado, el degradado se dibuja de arriba a abajo. Esto es lo `m_nGradientAngle` mismo que establecer en 90.

[CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill` especifica el color del principio del degradado y [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` especifica el color del final del degradado. Si `m_clrFillGradient` es -1, no hay degradado.

## <a name="cmfctooltipinfom_nmaxdescrwidth"></a><a name="m_nmaxdescrwidth"></a>CMFCToolTipInfo::m_nMaxDescrWidth

Especifica el ancho máximo de la descripción que se muestra en cada información sobre herramientas. Si el ancho de la descripción supera el valor especificado, el texto se ajusta.

```
int m_nMaxDescrWidth;
```

## <a name="cmfctooltipinfom_bvislmanagertheme"></a><a name="m_bvislmanagertheme"></a>CMFCToolTipInfo::m_bVislManagerTheme

Especifica si el administrador visual de la aplicación controla el aspecto de todas las descripciones emergentes.

```
BOOL m_bVislManagerTheme;
```

### <a name="remarks"></a>Observaciones

Si `m_bVislManagerTheme` es TRUE, cada información sobre herramientas solicita un nuevo [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) desde el administrador visual de la aplicación antes de que aparezcan en la pantalla y usa los valores de ese objeto para determinar su apariencia. Los demás miembros de [su CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) se omiten.

## <a name="cmfctooltipinfooperator"></a><a name="operator_eq"></a>CMFCToolTipInfo::operator ?

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```

### <a name="parameters"></a>Parámetros

[en] *src*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipCtrl Clase](../../mfc/reference/cmfctooltipctrl-class.md)
