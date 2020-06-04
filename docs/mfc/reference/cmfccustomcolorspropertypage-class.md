---
title: CMFCCustomColorsPropertyPage (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: 468d947947fc89f9ebc832cda722d854bb8b4be2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752462"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage (Clase)

Representa una página de propiedades que puede seleccionar colores personalizados en un cuadro de diálogo de color.

## <a name="syntax"></a>Sintaxis

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|`CMFCCustomColorsPropertyPage::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Establece los componentes de color de la página de propiedades.|

### <a name="remarks"></a>Observaciones

La `CMFCColorDialog` clase utiliza esta clase para mostrar la página de propiedades de color personalizada. Para obtener `CMFCColorDialog`más información sobre , vea [CMFCColorDialog (Clase)](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCCustomColorsPropertyPage` muestra cómo construir un objeto y establecer los componentes de color de la página de propiedades.

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

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a>CMFCCustomColorsPropertyPage::Setup

Establece los componentes de color de la página de propiedades.

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*R*|[en] El componente rojo del valor RGB.|
|*G*|[en] El componente verde del valor RGB.|
|*B*|[en] El componente azul del valor RGB.|

### <a name="remarks"></a>Observaciones

Este método actualiza los valores de color RGB actual y HLS asociados (hue, lightness y saturation) de la página de propiedades. El [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) método llama a este método cuando el marco de trabajo inicializa el cuadro de diálogo de color o el usuario presiona el botón izquierdo del mouse. Para obtener `CMFCColorDialog`más información sobre , vea [CMFCColorDialog (Clase)](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage (Clase)](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
