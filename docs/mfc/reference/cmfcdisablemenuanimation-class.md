---
title: CMFCDisableMenuAnimation (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 0b0df30d48b2f77d620b00f67d40743445981b66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665041"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation (clase)

Deshabilita la animación de menús emergentes.

## <a name="syntax"></a>Sintaxis

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Name|Descripción|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Construye un objeto `CMFCDisableMenuAnimation`.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Name|Descripción|
|[CMFCDisableMenuAnimation::Restore](#restore)|Restaura la animación anterior que el marco de trabajo que se usa para mostrar un menú emergente.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|nombre|Descripción|
|`CMFCDisableMenuAnimation::m_animType`|Almacena el tipo de animación anterior de un menú emergente.|

### <a name="remarks"></a>Comentarios

Utilice esta clase auxiliar para deshabilitar temporalmente la animación de menús emergentes (por ejemplo, al procesar los comandos del mouse o teclado).

Un `CMFCDisableMenuAnimation` objeto deshabilita la animación de menús emergentes durante su vigencia. El constructor almacena el tipo de animación emergente de menú actual en el `m_animType` campo y escriba la animación actual a los conjuntos de `CMFCPopupMenu::NO_ANIMATION`. El destructor restaura el tipo de animación anterior.

Puede crear un `CMFCDisableMenuAnimation` objeto de la pila para deshabilitar la animación de menús emergentes a lo largo de una sola función. Si desea deshabilitar la animación de menús emergente entre funciones, cree un `CMFCDisableMenuAnimation` en el montón de objeto y, a continuación, eliminarlo cuando desee restaurar la animación de menús emergentes.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo usar la pila para deshabilitar temporalmente la animación de menús.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpopupmenu.h

##  <a name="restore"></a>  CMFCDisableMenuAnimation::Restore

Restaura la animación anterior que el marco de trabajo que se usa para mostrar un menú emergente.

```
void Restore ();
```

### <a name="remarks"></a>Comentarios

Este método es invocado por el `CMFCDisableMenuAnimation` destructor para restaurar la animación anterior que el marco de trabajo que se usa para mostrar un menú emergente.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md)
