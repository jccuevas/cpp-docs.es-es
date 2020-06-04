---
title: Clase CBaseKeyFrame
ms.date: 11/04/2016
f1_keywords:
- CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::GetAnimationKeyframe
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bIsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_keyframe
helpviewer_keywords:
- CBaseKeyFrame [MFC], CBaseKeyFrame
- CBaseKeyFrame [MFC], AddToStoryboard
- CBaseKeyFrame [MFC], GetAnimationKeyframe
- CBaseKeyFrame [MFC], IsAdded
- CBaseKeyFrame [MFC], IsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_bAdded
- CBaseKeyFrame [MFC], m_bIsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_keyframe
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
ms.openlocfilehash: 3fcd55f6a157f4b837090a3608fb509b870aae5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352992"
---
# <a name="cbasekeyframe-class"></a>Clase CBaseKeyFrame

Implementa la funcionalidad básica de un fotograma clave.

## <a name="syntax"></a>Sintaxis

```
class CBaseKeyFrame : public CObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|Construye un objeto de fotograma clave.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|Agrega un fotograma clave al guión gráfico.|
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Devuelve el valor de fotograma clave subyacente.|
|[CBaseKeyFrame::IsAdded](#isadded)|Indica si se ha agregado un fotograma clave al guión gráfico.|
|[CBaseKeyFrame::IskeyframeAtOffset](#iskeyframeatoffset)|Especifica si el fotograma clave se debe agregar al guión gráfico en el desplazamiento o después de la transición.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|Especifica si este fotograma clave se ha agregado a un guión gráfico.|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Especifica si este fotograma clave se debe agregar al guión gráfico en un desplazamiento de otro fotograma clave existente o al final de alguna transición.|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Representa un fotograma clave de la API de animación de Windows. Cuando no se inicializa un fotograma clave, se establece en el valor predefinido UI_ANIMATION_KEYFRAME_STORYBOARD_START.|

## <a name="remarks"></a>Observaciones

Encapsula UI_ANIMATION_KEYFRAME variable. Sirve como clase base para cualquier implementación de fotograma clave. Un fotograma clave representa un momento en el tiempo dentro de un guión gráfico y se puede utilizar para especificar las horas de inicio y finalización de las transiciones. Hay dos tipos de fotogramas clave: fotogramas clave agregados al guión gráfico en el desplazamiento especificado (en el tiempo) o fotogramas clave agregados después de la transición especificada. Dado que las duraciones de algunas transiciones no se pueden conocer antes de que se inicie la animación, los valores reales de algunos fotogramas clave se determinan solo en tiempo de ejecución. Dado que los fotogramas clave pueden depender de transiciones, que a su vez dependen de fotogramas clave, es importante evitar recursividads infinitas al crear cadenas de fotogramas clave.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="cbasekeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseKeyFrame::AddToStoryboard

Agrega un fotograma clave al guión gráfico.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero a un guión gráfico.

*bDeepAdd*<br/>
Si este parámetro es TRUE y el fotograma clave que se agrega depende de algún otro fotograma clave o transición, este método intenta agregar primero este fotograma clave o la transición al guión gráfico.

### <a name="return-value"></a>Valor devuelto

TRUESi el fotograma clave se ha agregado correctamente al guión gráfico; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Se llama a este método para agregar un fotograma clave al guión gráfico.

## <a name="cbasekeyframecbasekeyframe"></a><a name="cbasekeyframe"></a>CBaseKeyFrame::CBaseKeyFrame

Construye un objeto de fotograma clave.

```
CBaseKeyFrame();
```

## <a name="cbasekeyframegetanimationkeyframe"></a><a name="getanimationkeyframe"></a>CBaseKeyFrame::GetAnimationKeyframe

Devuelve el valor de fotograma clave subyacente.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>Valor devuelto

Un fotograma clave actual. El valor predeterminado es UI_ANIMATION_KEYFRAME_STORYBOARD_START.

### <a name="remarks"></a>Observaciones

Se trata de un descriptor de acceso al valor de fotograma clave subyacente.

## <a name="cbasekeyframeisadded"></a><a name="isadded"></a>CBaseKeyFrame::IsAdded

Indica si se ha agregado un fotograma clave al guión gráfico.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se agrega un fotograma clave a un guión gráfico; FALSO otehrwise.

### <a name="remarks"></a>Observaciones

En la clase base IsAdded siempre devuelve TRUE, pero se invalida en clases derivadas.

## <a name="cbasekeyframeiskeyframeatoffset"></a><a name="iskeyframeatoffset"></a>CBaseKeyFrame::IskeyframeAtOffset

Especifica si el fotograma clave se debe agregar al guión gráfico en el desplazamiento o después de la transición.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el fotograma clave se debe agregar al guión gráfico en algún desplazamiento especificado. FALSE si el fotograma clave se debe agregar al guión gráfico después de alguna transición.

### <a name="remarks"></a>Observaciones

Especifica si el fotograma clave se debe agregar al guión gráfico en el desplazamiento. El desplazamiento o la transición deben especificarse en una clase derivada.

## <a name="cbasekeyframem_badded"></a><a name="m_badded"></a>CBaseKeyFrame::m_bAdded

Especifica si este fotograma clave se ha agregado a un guión gráfico.

```
BOOL m_bAdded;
```

## <a name="cbasekeyframem_biskeyframeatoffset"></a><a name="m_biskeyframeatoffset"></a>CBaseKeyFrame::m_bIsKeyframeAtOffset

Especifica si este fotograma clave se debe agregar al guión gráfico en un desplazamiento de otro fotograma clave existente o al final de alguna transición.

```
BOOL m_bIsKeyframeAtOffset;
```

## <a name="cbasekeyframem_keyframe"></a><a name="m_keyframe"></a>CBaseKeyFrame::m_keyframe

Representa un fotograma clave de la API de animación de Windows. Cuando no se inicializa un fotograma clave, se establece en el valor predefinido UI_ANIMATION_KEYFRAME_STORYBOARD_START.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
