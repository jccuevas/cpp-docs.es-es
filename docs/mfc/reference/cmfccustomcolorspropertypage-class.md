---
title: CMFCCustomColorsPropertyPage (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: b28711991835dd14929e5387709046c3867c715e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299895"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage (clase)

Representa una página de propiedades que puede seleccionar los colores personalizados en un cuadro de diálogo color.

## <a name="syntax"></a>Sintaxis

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Name|Descripción|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Name|Descripción|
|`CMFCCustomColorsPropertyPage::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Establece los componentes de color de la página de propiedades.|

### <a name="remarks"></a>Comentarios

El `CMFCColorDialog` usa esta clase para mostrar la página de propiedades de color personalizado. Para obtener más información acerca de `CMFCColorDialog`, consulte [CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un `CMFCCustomColorsPropertyPage` de objeto y establecer los componentes de color de la página de propiedades.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcustomcolorspropertypage.h

##  <a name="setup"></a>  CMFCCustomColorsPropertyPage::Setup

Establece los componentes de color de la página de propiedades.

```
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*R*|[in] El componente rojo del valor RGB.|
|*G*|[in] El componente verde del valor RGB.|
|*B*|[in] El componente azul del valor RGB.|

### <a name="remarks"></a>Comentarios

Este método actualiza el RGB actual y los asociados HLS (matiz, saturación y luminosidad) valores de color de la página de propiedades. El [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) método llama a este método cuando el marco de trabajo inicializa el cuadro de diálogo color o el usuario presiona el botón primario del mouse. Para obtener más información acerca de `CMFCColorDialog`, consulte [CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage (clase)](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
