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
ms.openlocfilehash: d36c924d30bd728fcd54b6cdf6805ade25e20b5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218412"
---
# <a name="cbasekeyframe-class"></a>Clase CBaseKeyFrame

Implementa la funcionalidad básica de un fotograma clave.

## <a name="syntax"></a>Sintaxis

```
class CBaseKeyFrame : public CObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|Construye un objeto de fotograma clave.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|Agrega un fotograma clave para crear un guion gráfico.|
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Devuelve el valor del fotograma clave subyacente.|
|[CBaseKeyFrame::IsAdded](#isadded)|Indica si se ha agregado un fotograma clave en guiones gráficos.|
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|Especifica si el fotograma clave se debe agregar a guión gráfico con desplazamiento o después de la transición.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|Especifica si se ha agregado este fotograma clave a un guión gráfico.|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Especifica si se debe agregar este fotograma clave en guiones gráficos en un desplazamiento desde otro fotograma clave existente, o al final de algunos transición.|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Representa un fotograma clave de API de animación de Windows. Cuando no se ha inicializado un fotograma clave se establece al valor predefinido UI_ANIMATION_KEYFRAME_STORYBOARD_START.|

## <a name="remarks"></a>Comentarios

Encapsula la variable UI_ANIMATION_KEYFRAME. Actúa como clase base para cualquier implementación de fotograma clave. Un fotograma clave representa un momento dado dentro de un guión gráfico y puede utilizarse para especificar los tiempos de inicio y finalización de las transiciones. Hay dos tipos de fotogramas clave - fotogramas clave que se agrega al guion gráfico en el desplazamiento especificado (en tiempo), o fotogramas clave que se agregaron después de transición especificado. Dado que no se puede conocer las duraciones de algunas transiciones antes del comienzo de la animación, los valores reales de algunos fotogramas clave se determinan en tiempo de ejecución solo. Dado que los fotogramas clave pueden depender de las transiciones, que a su vez, sus dependen de los fotogramas clave, es importante evitar la recursividad infinita al crear cadenas de fotograma clave.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CBaseKeyFrame::AddToStoryboard

Agrega un fotograma clave para crear un guion gráfico.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero a un guión gráfico.

*bDeepAdd*<br/>
Si este parámetro es TRUE y el fotograma clave que se va a agregar depende de algún otro fotograma clave o transición, este método intenta agregar este fotograma clave o una transición en guiones gráficos en primer lugar.

### <a name="return-value"></a>Valor devuelto

TRUE si el fotograma clave se agregó al guión gráfico correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Se llama a este método para agregar un fotograma clave para crear un guion gráfico.

##  <a name="cbasekeyframe"></a>  CBaseKeyFrame::CBaseKeyFrame

Construye un objeto de fotograma clave.

```
CBaseKeyFrame();
```

##  <a name="getanimationkeyframe"></a>  CBaseKeyFrame::GetAnimationKeyframe

Devuelve el valor del fotograma clave subyacente.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>Valor devuelto

Un fotograma clave actual. El valor predeterminado es UI_ANIMATION_KEYFRAME_STORYBOARD_START.

### <a name="remarks"></a>Comentarios

Se trata de un descriptor de acceso para el valor del fotograma clave subyacente.

##  <a name="isadded"></a>  CBaseKeyFrame::IsAdded

Indica si se ha agregado un fotograma clave en guiones gráficos.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se agrega un fotograma clave a un guión gráfico; otehrwise FALSE.

### <a name="remarks"></a>Comentarios

En la clase base IsAdded siempre devuelve TRUE, pero que se invalide en clases derivadas.

##  <a name="iskeyframeatoffset"></a>  CBaseKeyFrame::IsKeyframeAtOffset

Especifica si el fotograma clave se debe agregar a guión gráfico con desplazamiento o después de la transición.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el fotograma clave se debe agregar al guión gráfico en algún desplazamiento especificado. FALSE si el fotograma clave se debe agregar a guión gráfico después de algunos transición.

### <a name="remarks"></a>Comentarios

Especifica si el fotograma clave se debe agregar a guión gráfico con desplazamiento. Debe especificarse el desplazamiento o la transición en una clase derivada.

##  <a name="m_badded"></a>  CBaseKeyFrame::m_bAdded

Especifica si se ha agregado este fotograma clave a un guión gráfico.

```
BOOL m_bAdded;
```

##  <a name="m_biskeyframeatoffset"></a>  CBaseKeyFrame::m_bIsKeyframeAtOffset

Especifica si se debe agregar este fotograma clave en guiones gráficos en un desplazamiento desde otro fotograma clave existente, o al final de algunos transición.

```
BOOL m_bIsKeyframeAtOffset;
```

##  <a name="m_keyframe"></a>  CBaseKeyFrame::m_keyframe

Representa un fotograma clave de API de animación de Windows. Cuando no se ha inicializado un fotograma clave se establece al valor predefinido UI_ANIMATION_KEYFRAME_STORYBOARD_START.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
