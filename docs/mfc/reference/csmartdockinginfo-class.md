---
title: CSmartDockingInfo (clase)
ms.date: 11/19/2018
f1_keywords:
- CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo::CopyTo
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_bUseThemeColorInShading
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrBaseBackground
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneDest
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneSrc
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrTransparent
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_nCentralGroupOffset
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_sizeTotal
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerBmpResID
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerLightBmpResID
helpviewer_keywords:
- CSmartDockingInfo [MFC], CopyTo
- CSmartDockingInfo [MFC], m_bUseThemeColorInShading
- CSmartDockingInfo [MFC], m_clrBaseBackground
- CSmartDockingInfo [MFC], m_clrToneDest
- CSmartDockingInfo [MFC], m_clrToneSrc
- CSmartDockingInfo [MFC], m_clrTransparent
- CSmartDockingInfo [MFC], m_nCentralGroupOffset
- CSmartDockingInfo [MFC], m_sizeTotal
- CSmartDockingInfo [MFC], m_uiMarkerBmpResID
- CSmartDockingInfo [MFC], m_uiMarkerLightBmpResID
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
ms.openlocfilehash: c0ccb9f728add37230cbfd88cc8f6c9b1696fa2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318224"
---
# <a name="csmartdockinginfo-class"></a>CSmartDockingInfo (clase)

Define el aspecto de los marcadores de acoplamiento inteligente.

## <a name="syntax"></a>Sintaxis

```
class CSmartDockingInfo : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CSmartDockingInfo::CSmartDockingInfo`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSmartDockingInfo::CopyTo](#copyto)|Copia los parámetros de información de acoplamiento inteligente actuales en el objeto [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) proporcionado.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|Especifica si se debe utilizar el color del tema actual cuando el marco de trabajo muestra marcadores de acoplamiento inteligentes.|
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|Especifica el color de fondo base de los marcadores de acoplamiento inteligentes.|
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|Especifica el color que `m_clrToneSrc` se reemplaza en los mapas de bits de marcador de acoplamiento inteligente.|
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|Especifica el color de los mapas de bits de marcador de acoplamiento inteligente.|
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|Especifica el color de los mapas de bits de marcador de acoplamiento inteligente cuando son transparentes.|
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|Especifica el desfase del grupo central de marcadores de acoplamiento inteligentes desde los límites del rectángulo del grupo central.|
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|Especifica el tamaño total de todos los marcadores de acoplamiento inteligentes de un grupo.|
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Define los identificadores de recursos de los mapas de bits que el marco de trabajo utiliza para los marcadores de acoplamiento inteligente que no se resaltan.|
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Define los identificadores de recursos de los mapas de bits que el marco de trabajo utiliza para los marcadores de acoplamiento inteligente que se resaltan.|

## <a name="remarks"></a>Observaciones

El marco de trabajo controla los marcadores de acoplamiento inteligentes internamente. La siguiente ilustración muestra los marcadores de acoplamiento inteligentes estándar:

![Marcadores estándar de acoplamiento inteligente](../../mfc/reference/media/nextsdmarkers.png "Marcadores estándar de acoplamiento inteligente")

En esta figura, la imagen de la izquierda muestra un marcador de acoplamiento inteligente de grupo central que no tiene habilitado el acoplamiento a una pestaña. La imagen en el medio muestra un marcador de acoplamiento inteligente de borde derecho. La imagen de la derecha muestra un marcador de acoplamiento inteligente de grupo central que tiene habilitado el acoplamiento a una pestaña. El marcador de acoplamiento inteligente del grupo central tiene un mapa de bits principal y cinco mapas de bits de marcador de acoplamiento inteligente.

Puede personalizar los siguientes parámetros de marcadores de acoplamiento inteligentes:

- Color. Por ejemplo, puede reemplazar el color azul de los marcadores de la figura por cualquier color definido por el usuario.

- Color de transparencia.

- Desplazamiento de un marcador de acoplamiento inteligente en el grupo central desde el borde del rectángulo delimitador.

- El mapa de bits principal que representa el grupo central.

- Los mapas de bits que representan los marcadores de acoplamiento inteligente regulares y resaltados.

En la ilustración siguiente se muestra un ejemplo de marcadores de acoplamiento inteligentes que se han personalizado:

![Marcadores personalizados de acoplamiento inteligente](../../mfc/reference/media/nextsdmarkerscustom.png "Marcadores personalizados de acoplamiento inteligente")

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDockingManager.h

## <a name="csmartdockinginfocopyto"></a><a name="copyto"></a>CSmartDockingInfo::CopyTo

Copia los parámetros de acoplamiento inteligente actuales en el objeto [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) proporcionado.

```
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Parámetros

*params*<br/>
[fuera] Objeto de `CSmartDockingInfo` tipo que se rellena con los parámetros de acoplamiento inteligente actuales.

## <a name="csmartdockinginfom_busethemecolorinshading"></a><a name="m_busethemecolorinshading"></a>CSmartDockingInfo::m_bUseThemeColorInShading

Especifica si se debe utilizar el color del tema actual cuando el marco de trabajo muestra marcadores de acoplamiento inteligentes.

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, los marcadores se dibujan utilizando el color del tema actual; de lo contrario, los marcadores se dibujan con un color azul claro.

El valor predeterminado es FALSE.

## <a name="csmartdockinginfom_clrbasebackground"></a><a name="m_clrbasebackground"></a>CSmartDockingInfo::m_clrBaseBackground

Especifica el color de fondo base de los marcadores de acoplamiento inteligentes.

```
COLORREF m_clrBaseBackground;
```

## <a name="csmartdockinginfom_clrtonedest"></a><a name="m_clrtonedest"></a>CSmartDockingInfo::m_clrToneDest

Especifica el color que `m_clrToneSrc` se reemplazará en los mapas de bits de marcador de acoplamiento inteligente.

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>Observaciones

Establezca este valor para cambiar el color de los mapas de bits de marcador mediante programación. Por ejemplo, si desea cambiar el color de los marcadores estándar proporcionados con el marco de trabajo, establezca este valor en el color deseado. De forma predeterminada, [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) se establece en RGB (61, 123, 241) (un color azulado).

Para cambiar el color de los `m_clrToneDest` marcadores personalizados, debe especificar ambos y `m_clrToneSrc`.

## <a name="csmartdockinginfom_clrtonesrc"></a><a name="m_clrtonesrc"></a>CSmartDockingInfo::m_clrToneSrc

Especifica el color de los mapas de bits de marcador de acoplamiento inteligente.

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>Observaciones

Establezca este valor solo cuando desee reemplazar el color de un mapa de bits personalizado por otro color. No es necesario establecer este valor si va a cambiar el color de un marcador estándar (marco proporcionado).

Se `(COLORREF)-1` usa para dejar vacío a un miembro del grupo de acoplamiento inteligente.

## <a name="csmartdockinginfom_clrtransparent"></a><a name="m_clrtransparent"></a>CSmartDockingInfo::m_clrTransparent

Especifica el color de los mapas de bits de marcador de acoplamiento inteligente cuando son transparentes.

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>Observaciones

Debe establecer este valor al mostrar marcadores personalizados y mapas de bits personalizados en el grupo de acoplamiento.

## <a name="csmartdockinginfom_ncentralgroupoffset"></a><a name="m_ncentralgroupoffset"></a>CSmartDockingInfo::m_nCentralGroupOffset

Especifica el desfase entre el grupo central de marcadores de acoplamiento inteligentes y los límites del rectángulo del grupo central.

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>Observaciones

Especifique este valor si desea cambiar el desplazamiento predeterminado entre los marcadores personalizados y los límites del grupo central de marcadores de acoplamiento inteligente. El desplazamiento predeterminado es de 5 píxeles.

## <a name="csmartdockinginfom_sizetotal"></a><a name="m_sizetotal"></a>CSmartDockingInfo::m_sizeTotal

Especifica el tamaño total de un rectángulo delimitador que encierra todos los marcadores de acoplamiento inteligentes del grupo central.

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>Observaciones

Establézalo `m_sizeTotal` en el tamaño del rectángulo delimitador del marcador de grupo central. Debe especificar este valor si utiliza mapas de bits personalizados para los marcadores.

## <a name="csmartdockinginfom_uimarkerbmpresid"></a><a name="m_uimarkerbmpresid"></a>CSmartDockingInfo::m_uiMarkerBmpResID

Define los identificadores de recursos de los mapas de bits que se utilizan para los marcadores de acoplamiento inteligente personalizados no resaltados.

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Observaciones

Rellene esta matriz con los identificadores de recursos de los mapas de bits que representan los marcadores de acoplamiento inteligente. AFX_SD_MARKERS_NUM se define actualmente como 5. La matriz se rellena de la siguiente manera:

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

## <a name="csmartdockinginfom_uimarkerlightbmpresid"></a><a name="m_uimarkerlightbmpresid"></a>CSmartDockingInfo::m_uiMarkerLightBmpResID

Define los identificadores de recursos de los mapas de bits que se utilizan para los marcadores de acoplamiento inteligente personalizados resaltados.

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Observaciones

Rellene esta matriz con los identificadores de recursos de los mapas de bits que representan los marcadores de acoplamiento inteligente resaltados. AFX_SD_MARKERS_NUM se define actualmente como 5. La matriz se rellena de la siguiente manera:

```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)
