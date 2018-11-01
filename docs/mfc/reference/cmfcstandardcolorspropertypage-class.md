---
title: CMFCStandardColorsPropertyPage (clase)
ms.date: 11/04/2016
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
ms.openlocfilehash: 7663f85b20ab88c999af7ba37b260237d0fd869e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520671"
---
# <a name="cmfcstandardcolorspropertypage-class"></a>CMFCStandardColorsPropertyPage (clase)

Representa una página de propiedades que usan los usuarios para seleccionar los colores estándares en un cuadro de diálogo color.

## <a name="syntax"></a>Sintaxis

```
class CMFCStandardColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Name|Descripción|
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Name|Descripción|
|`CMFCStandardColorsPropertyPage::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|
|`CMFCStandardColorsPropertyPage::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|

### <a name="remarks"></a>Comentarios

El `CMFCColorDialog` usa esta clase para mostrar la página de propiedades de color estándar. Para obtener más información acerca de `CMFCColorDialog`, consulte [CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxstandardcolorspropertypage.h

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCCustomColorsPropertyPage (clase)](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
