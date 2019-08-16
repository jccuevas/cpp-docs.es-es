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
ms.openlocfilehash: d5f918b591e1db9ff67288a8761f7554698fa761
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324017"
---
# <a name="csmartdockinginfo-class"></a>CSmartDockingInfo (clase)

Define el aspecto de los marcadores de acoplamiento inteligente.

## <a name="syntax"></a>Sintaxis

```
class CSmartDockingInfo : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CSmartDockingInfo::CSmartDockingInfo`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSmartDockingInfo::CopyTo](#copyto)|Copia los parámetros de información de acoplamiento inteligente actuales en proporcionado [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) objeto.|

### <a name="data-members"></a>Miembros de datos

|Name|Descripción|
|----------|-----------------|
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|Especifica si se utiliza el color del tema actual cuando el marco de trabajo muestra marcadores de acoplamiento inteligente.|
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|Especifica el color de fondo de base de los marcadores de acoplamiento inteligente.|
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|Especifica el color que reemplaza `m_clrToneSrc` en mapas de bits de marcador de acoplamiento inteligente.|
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|Especifica el color de mapas de bits de marcador de acoplamiento inteligente.|
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|Especifica el color de mapas de bits de marcador de acoplamiento inteligente cuando están transparentes.|
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|Especifica el desplazamiento del grupo central de marcadores de acoplamiento inteligente de los límites del rectángulo del grupo central.|
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|Especifica el tamaño total de todos los marcadores de acoplamiento inteligente de un grupo.|
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Define los identificadores de recursos de los mapas de bits que usa el marco de trabajo para los marcadores de acoplamiento inteligentes que no están resaltados.|
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Define los identificadores de recursos de los mapas de bits que usa el marco de trabajo para los marcadores de acoplamiento inteligentes que se resaltan.|

## <a name="remarks"></a>Comentarios

Los identificadores de marco inteligente internamente los marcadores de acoplamiento. La siguiente ilustración muestra los marcadores de acoplamiento inteligentes estándares:

![Marcadores estándares de acoplamiento inteligente](../../mfc/reference/media/nextsdmarkers.png "marcadores estándares de acoplamiento inteligente")

En esta ilustración, la imagen de la izquierda muestra un marcador de acoplamiento inteligente de grupo central que no tienen acoplamiento a una pestaña habilitada. La imagen en la parte central muestra un marcador de acoplamiento inteligente del borde derecho. La imagen de la derecha muestra un marcador de acoplamiento inteligente de grupo central que tienen acoplamiento a una pestaña habilitada. El marcador de acoplamiento inteligente de grupo central tiene un mapa de bits principal y cinco inteligente acoplamiento mapas de bits de marcador.

Puede personalizar los siguientes parámetros de marcadores de acoplamiento inteligente:

- Color. Por ejemplo, puede reemplazar el color azul de los marcadores en la ilustración con cualquier color definido por el usuario.

- Color de transparencia.

- Desplazamiento de un marcador de acoplamiento inteligente en el grupo central desde el borde del rectángulo delimitador.

- El mapa de bits principal que representa el grupo central.

- Los mapas de bits que representa los marcadores de acoplamiento inteligentes normales y resaltados.

En la siguiente ilustración se muestra un ejemplo de marcadores de acoplamiento inteligente que se han personalizado:

![Marcadores personalizados de acoplamiento inteligente](../../mfc/reference/media/nextsdmarkerscustom.png "marcadores personalizados de acoplamiento inteligente")

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDockingManager.h

##  <a name="copyto"></a>  CSmartDockingInfo::CopyTo

Copia los parámetros de acoplamiento inteligentes actuales en proporcionado [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) objeto.

```
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Parámetros

*params*<br/>
[out] Un objeto de tipo `CSmartDockingInfo` que se rellena con los parámetros actuales de acoplamiento inteligentes.

##  <a name="m_busethemecolorinshading"></a>  CSmartDockingInfo::m_bUseThemeColorInShading

Especifica si se utiliza el color del tema actual cuando el marco de trabajo muestra marcadores de acoplamiento inteligente.

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>Comentarios

Si es TRUE, los marcadores se dibujan usando el color del tema actual; en caso contrario, los marcadores se dibujan con un color azul claro.

El valor predeterminado es FALSE.

##  <a name="m_clrbasebackground"></a>  CSmartDockingInfo::m_clrBaseBackground

Especifica el color de fondo de base de los marcadores de acoplamiento inteligente.

```
COLORREF m_clrBaseBackground;
```

##  <a name="m_clrtonedest"></a>  CSmartDockingInfo::m_clrToneDest

Especifica el color que va a reemplazar `m_clrToneSrc` en mapas de bits de marcador de acoplamiento inteligente.

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>Comentarios

Establezca este valor para cambiar el color de mapas de bits de marcador mediante programación. Por ejemplo, si desea cambiar el color de los marcadores estándares proporcionada con el marco de trabajo, establezca este valor para el color que desee. De forma predeterminada, [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) está establecido en RGB (61, 123, 241) (color azulado).

Para cambiar el color de marcadores personalizados, debe especificar `m_clrToneDest` y `m_clrToneSrc`.

##  <a name="m_clrtonesrc"></a>  CSmartDockingInfo::m_clrToneSrc

Especifica el color de mapas de bits de marcador de acoplamiento inteligente.

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>Comentarios

Establezca este valor sólo cuando desea reemplazar el color de un mapa de bits personalizado con otro color. No es necesario establecer este valor si va a cambiar el color de un estándar (marco de trabajo proporcionado) marcador.

Use `(COLORREF)-1` a un miembro del grupo de acoplamiento inteligente deje en blanco.

##  <a name="m_clrtransparent"></a>  CSmartDockingInfo::m_clrTransparent

Especifica el color de mapas de bits de marcador de acoplamiento inteligente cuando están transparentes.

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>Comentarios

Debe establecer este valor cuando se muestra marcadores personalizados y mapas de bits personalizados en el grupo de acoplamiento.

##  <a name="m_ncentralgroupoffset"></a>  CSmartDockingInfo::m_nCentralGroupOffset

Especifica el desplazamiento entre el grupo de marcadores de acoplamiento inteligente central y los límites del rectángulo del grupo central.

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>Comentarios

Especifique este valor si desea cambiar el desplazamiento predeterminado entre marcadores personalizados y los límites del grupo central de marcadores de acoplamiento inteligente. El desplazamiento predeterminado es 5 píxeles.

##  <a name="m_sizetotal"></a>  CSmartDockingInfo::m_sizeTotal

Especifica el tamaño total de un rectángulo delimitador que rodea todos los marcadores de acoplamiento inteligente en el grupo central.

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>Comentarios

Establecer `m_sizeTotal` al tamaño del rectángulo delimitador del marcador de grupo central. Debe especificar este valor si usa mapas de bits personalizados para los marcadores.

##  <a name="m_uimarkerbmpresid"></a>  CSmartDockingInfo::m_uiMarkerBmpResID

Define los identificadores de los mapas de bits que se usan para no resaltado inteligentes acoplamiento marcadores personalizados de recursos.

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Comentarios

Rellene esta matriz con los identificadores de los mapas de bits que representa los marcadores de acoplamiento inteligentes de recursos. AFX_SD_MARKERS_NUM está actualmente definido como 5. Rellene la matriz como sigue:

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

##  <a name="m_uimarkerlightbmpresid"></a>  CSmartDockingInfo::m_uiMarkerLightBmpResID

Define los identificadores de los mapas de bits que se usan para resaltado marcadores personalizados de acoplamiento inteligentes de recursos.

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Comentarios

Rellene esta matriz con los identificadores de recursos de los mapas de bits que representa los marcadores de acoplamiento inteligentes resaltados. AFX_SD_MARKERS_NUM está actualmente definido como 5. Rellene la matriz como sigue:

```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)
