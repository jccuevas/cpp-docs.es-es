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
ms.openlocfilehash: f535503338a82c7cc70455ae6a08cdab0f13c624
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372291"
---
# <a name="ckeyframe-class"></a>Clase CKeyFrame

Representa un fotograma clave de la animación.

## <a name="syntax"></a>Sintaxis

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|Sobrecargado. Construye un fotograma clave que depende de otro fotograma clave.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Agrega un fotograma clave a un guión gráfico. (Reemplaza [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Agrega un fotograma clave al guión gráfico después de la transición.|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Agrega un fotograma clave al guión gráfico en el desplazamiento.|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Devuelve un puntero a un fotograma clave del que depende este fotograma clave.|
|[CKeyFrame::GetOffset](#getoffset)|Devuelve un desplazamiento de otro fotograma clave.|
|[CKeyFrame::GetTransition](#gettransition)|Devuelve un puntero a una transición de la que depende este fotograma clave.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|Especifica el desplazamiento de este fotograma clave de un fotograma clave almacenado en m_pExistingKeyFrame.|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Almacena un puntero a un keframe existente. Este fotograma clave se agrega al guión gráfico con m_offset al fotograma clave existente.|
|[CKeyFrame::m_pTransition](#m_ptransition)|Almacena un puntero a la transción que comienza en este fotograma clave.|

## <a name="remarks"></a>Observaciones

Esta clase implementa un fotograma clave de animación. Un fotograma clave representa un momento en el tiempo dentro de un guión gráfico y se puede utilizar para especificar las horas de inicio y finalización de las transiciones. Un fotograma clave puede basarse en otro fotograma clave y tener un desplazamiento (en segundos) de él, o puede basarse en una transición y representar un momento en el tiempo en el que finaliza esta transición.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CKeyFrame::AddToStoryboard

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
Especifica si se debe agregar fotograma clave o transición de forma recursiva.

### <a name="return-value"></a>Valor devuelto

TRUE, si el fotograma clave se ha agregado correctamente.

### <a name="remarks"></a>Observaciones

Este método agrega un fotograma clave al guión gráfico. Si depende de otro fotograma clave o transición y bDeepAdd es TRUE, este método intenta agregarlos recursivamente.

## <a name="ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a>CKeyFrame::AddToStoryboardAfterTransition

Agrega un fotograma clave al guión gráfico después de la transición.

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

TRUE, si el fotograma clave se ha agregado correctamente.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función para agregar un fotograma clave al guión gráfico después de la transición.

## <a name="ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a>CKeyFrame::AddToStoryboardAtOffset

Agrega un fotograma clave al guión gráfico en el desplazamiento.

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero a un guión gráfico.

*bDeepAdd*<br/>
Especifica si se debe agregar un fotograma clave este fotograma clave de forma recursiva.

### <a name="return-value"></a>Valor devuelto

TRUE, si el fotograma clave se ha agregado correctamente.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función para agregar un fotograma clave al guión gráfico en offset.

## <a name="ckeyframeckeyframe"></a><a name="ckeyframe"></a>CKeyFrame::CKeyFrame

Construye un fotograma clave que depende de una transición.

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parámetros

*pTransición*<br/>
Un puntero a una transición.

*pKeyframe*<br/>
Un puntero al fotograma clave.

*offset*<br/>
Desplazamiento, en segundos, del fotograma clave especificado por pKeyframe.

### <a name="remarks"></a>Observaciones

El fotograma clave construido representará un momento en el tiempo dentro de un guión gráfico cuando finalice la transición especificada.

## <a name="ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a>CKeyFrame::GetExistingKeyframe

Devuelve un puntero a un fotograma clave del que depende este fotograma clave.

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>Valor devuelto

Un puntero válido al fotograma clave, o NULL si este fotograma clave no depende de otro fotograma clave.

### <a name="remarks"></a>Observaciones

Este es un descriptor de acceso a un fotograma clave del que depende este fotograma clave.

## <a name="ckeyframegetoffset"></a><a name="getoffset"></a>CKeyFrame::GetOffset

Devuelve un desplazamiento de otro fotograma clave.

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>Valor devuelto

Un desplazamiento en segundos desde otro fotograma clave.

### <a name="remarks"></a>Observaciones

Se debe llamar a este método para determinar un desplazamiento en segundos desde otro fotograma clave.

## <a name="ckeyframegettransition"></a><a name="gettransition"></a>CKeyFrame::GetTransition

Devuelve un puntero a una transición de la que depende este fotograma clave.

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>Valor devuelto

Un puntero válido a la transición, o NULL si este fotograma clave no depende de la transición.

### <a name="remarks"></a>Observaciones

Este es un descriptor de acceso a una transición de la que depende este fotograma clave.

## <a name="ckeyframem_offset"></a><a name="m_offset"></a>CKeyFrame::m_offset

Especifica el desplazamiento de este fotograma clave de un fotograma clave almacenado en m_pExistingKeyFrame.

```
UI_ANIMATION_SECONDS m_offset;
```

## <a name="ckeyframem_pexistingkeyframe"></a><a name="m_pexistingkeyframe"></a>CKeyFrame::m_pExistingKeyFrame

Almacena un puntero a un keframe existente. Este fotograma clave se agrega al guión gráfico con m_offset al fotograma clave existente.

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

## <a name="ckeyframem_ptransition"></a><a name="m_ptransition"></a>CKeyFrame::m_pTransition

Almacena un puntero a la transción que comienza en este fotograma clave.

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
