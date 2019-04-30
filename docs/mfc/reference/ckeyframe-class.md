---
title: Clase CKeyFrame
ms.date: 11/04/2016
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
ms.openlocfilehash: c2c6add30757e1d83b70001679b37a7a22b9d7d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392614"
---
# <a name="ckeyframe-class"></a>Clase CKeyFrame

Representa un fotograma clave de la animación.

## <a name="syntax"></a>Sintaxis

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|Sobrecargado. Construye un fotograma clave que depende de otro fotogramas clave.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Agrega un fotograma clave a un guión gráfico. (Invalida [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Agrega un fotograma clave para crear un guion gráfico después de la transición.|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Agrega un fotograma clave para crear un guion gráfico con desplazamiento.|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Devuelve un puntero a un fotograma clave que depende de este fotograma clave.|
|[CKeyFrame::GetOffset](#getoffset)|Devuelve un desplazamiento respecto a otro fotogramas clave.|
|[CKeyFrame::GetTransition](#gettransition)|Devuelve un puntero a una transición que depende de este fotograma clave.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|Especifica el desplazamiento de este fotograma clave desde un fotograma clave almacenado en m_pExistingKeyFrame.|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Almacena un puntero a un keframe existente. Este fotograma clave se agrega al guion gráfico con m_offset el fotograma clave existente.|
|[CKeyFrame::m_pTransition](#m_ptransition)|Almacena un puntero a la transición que comienza en este fotograma clave.|

## <a name="remarks"></a>Comentarios

Esta clase implementa un fotograma clave de animación. Un fotograma clave representa un momento dado dentro de un guión gráfico y puede utilizarse para especificar los tiempos de inicio y finalización de las transiciones. Un fotograma clave deben basarse en otro fotogramas clave y tener un desplazamiento (en segundos), o puede basarse en una transición y representa un momento en el tiempo cuando finaliza esta transición.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CKeyFrame::AddToStoryboard

Agrega un fotograma clave a un guión gráfico.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero a un guión gráfico.

*bDeepAdd*<br/>
Especifica si se debe agregar fotogramas clave o realizar la transición de forma recursiva.

### <a name="return-value"></a>Valor devuelto

TRUE si el fotograma clave se agregó correctamente.

### <a name="remarks"></a>Comentarios

Este método agrega un fotograma clave para crear un guion gráfico. Si depende de otros fotogramas clave o una transición y bDeepAdd es TRUE, este método intenta agregarlos de forma recursiva.

##  <a name="addtostoryboardaftertransition"></a>  CKeyFrame::AddToStoryboardAfterTransition

Agrega un fotograma clave para crear un guion gráfico después de la transición.

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero a un guión gráfico.

*bDeepAdd*<br/>
Especifica si se debe agregar una transición de forma recursiva.

### <a name="return-value"></a>Valor devuelto

TRUE si el fotograma clave se agregó correctamente.

### <a name="remarks"></a>Comentarios

Esta función se llama el marco de trabajo para agregar un fotograma clave para crear un guion gráfico después de la transición.

##  <a name="addtostoryboardatoffset"></a>  CKeyFrame::AddToStoryboardAtOffset

Agrega un fotograma clave para crear un guion gráfico con desplazamiento.

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero a un guión gráfico.

*bDeepAdd*<br/>
Especifica si este fotograma clave dependen de forma recursiva para agregar un fotograma clave.

### <a name="return-value"></a>Valor devuelto

TRUE si el fotograma clave se agregó correctamente.

### <a name="remarks"></a>Comentarios

Esta función se llama el marco de trabajo para agregar un fotograma clave para crear un guion gráfico con desplazamiento.

##  <a name="ckeyframe"></a>  CKeyFrame::CKeyFrame

Construye un fotograma clave que depende de una transición.

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parámetros

*pTransition*<br/>
Un puntero a una transición.

*pKeyframe*<br/>
Un puntero al fotograma clave.

*offset*<br/>
Desplazamiento, en segundos, desde el fotograma clave especificado por pKeyframe.

### <a name="remarks"></a>Comentarios

El fotograma clave construido representará un momento dado dentro de un guión gráfico cuando finaliza la transición especificada.

##  <a name="getexistingkeyframe"></a>  CKeyFrame::GetExistingKeyframe

Devuelve un puntero a un fotograma clave que depende de este fotograma clave.

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>Valor devuelto

Un puntero válido al fotograma clave, o NULL si este fotograma clave no depende de otro fotogramas clave.

### <a name="remarks"></a>Comentarios

Se trata de un descriptor de acceso a un fotograma clave que depende de este fotograma clave.

##  <a name="getoffset"></a>  CKeyFrame::GetOffset

Devuelve un desplazamiento respecto a otro fotogramas clave.

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>Valor devuelto

Posición de desplazamiento en segundos desde otro fotograma clave.

### <a name="remarks"></a>Comentarios

Este método debe llamarse para determinar la posición de desplazamiento en segundos desde otro fotograma clave.

##  <a name="gettransition"></a>  CKeyFrame::GetTransition

Devuelve un puntero a una transición que depende de este fotograma clave.

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>Valor devuelto

Un puntero válido para la transición, o NULL si este fotograma clave no depende de la transición.

### <a name="remarks"></a>Comentarios

Se trata de un descriptor de acceso a una transición que depende de este fotograma clave.

##  <a name="m_offset"></a>  CKeyFrame::m_offset

Especifica el desplazamiento de este fotograma clave desde un fotograma clave almacenado en m_pExistingKeyFrame.

```
UI_ANIMATION_SECONDS m_offset;
```

##  <a name="m_pexistingkeyframe"></a>  CKeyFrame::m_pExistingKeyFrame

Almacena un puntero a un keframe existente. Este fotograma clave se agrega al guion gráfico con m_offset el fotograma clave existente.

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

##  <a name="m_ptransition"></a>  CKeyFrame::m_pTransition

Almacena un puntero a la transición que comienza en este fotograma clave.

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
