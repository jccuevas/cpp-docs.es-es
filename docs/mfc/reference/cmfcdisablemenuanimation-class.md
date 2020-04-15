---
title: CMFCDisableMenuAnimation (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 990f41d2dfa6491d246797322ee275c9648d52a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367571"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation (Clase)

Deshabilita la animación del menú emergente.

## <a name="syntax"></a>Sintaxis

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Construye un objeto `CMFCDisableMenuAnimation`.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCDisableMenuAnimation::Restore](#restore)|Restaura la animación anterior que el marco de trabajo utiliza para mostrar un menú emergente.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|Nombre|Descripción|
|`CMFCDisableMenuAnimation::m_animType`|Almacena el tipo de animación del menú emergente anterior.|

### <a name="remarks"></a>Observaciones

Utilice esta clase auxiliar para deshabilitar temporalmente la animación del menú emergente (por ejemplo, al procesar comandos de mouse o teclado).

Un `CMFCDisableMenuAnimation` objeto deshabilita la animación del menú emergente durante su vigencia. El constructor almacena el tipo de animación de menú emergente actual en el `m_animType` campo y establece el tipo de animación actual `CMFCPopupMenu::NO_ANIMATION`en . El destructor restaura el tipo de animación anterior.

Puede crear `CMFCDisableMenuAnimation` un objeto en la pila para deshabilitar la animación del menú emergente en una sola función. Si desea deshabilitar la animación del menú `CMFCDisableMenuAnimation` emergente entre funciones, cree un objeto en el montón y, a continuación, elimínelo cuando desee restaurar la animación del menú emergente.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar la pila para deshabilitar temporalmente la animación de menú.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpopupmenu.h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a>CMFCDisableMenuAnimation::Restore

Restaura la animación anterior que el marco de trabajo utiliza para mostrar un menú emergente.

```
void Restore ();
```

### <a name="remarks"></a>Observaciones

El destructor llama `CMFCDisableMenuAnimation` a este método para restaurar la animación anterior que el marco de trabajo utilizapara para mostrar un menú emergente.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md)
