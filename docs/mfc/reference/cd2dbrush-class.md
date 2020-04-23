---
title: Clase CD2DBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
ms.openlocfilehash: 536d84fe2c2f68d62490e1ce2b65085426762e87
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754195"
---
# <a name="cd2dbrush-class"></a>Clase CD2DBrush

Un contenedor para ID2D1Brush.

## <a name="syntax"></a>Sintaxis

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBrush::CD2DBrush](#cd2dbrush)|Construye un CD2DBrush objeto.|
|[CD2DBrush::-CD2DBrush](#_dtorcd2dbrush)|Destructor. Se llama cuando se destruye un objeto de pincel D2D.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBrush::Attach](#attach)|Adjunta la interfaz de recursos existente al objeto|
|[CD2DBrush::Destroy](#destroy)|Destruye un OBJETO CD2DBrush. (Reemplaza [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBrush::Detach](#detach)|Separa la interfaz de recursos del objeto|
|[CD2DBrush::Get](#get)|Devuelve la interfaz ID2D1Brush|
|[CD2DBrush::GetOpacity](#getopacity)|Obtiene el grado de opacidad de este pincel|
|[CD2DBrush::GetTransform](#gettransform)|Obtiene la transformación actual del destino de representación|
|[CD2DBrush::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DBrush::SetOpacity](#setopacity)|Establece el grado de opacidad de este pincel|
|[CD2DBrush::SetTransform](#settransform)|Aplica la transformación especificada al destino de representación, reemplazando la transformación existente. Todas las operaciones de dibujo posteriores se producen en el espacio transformado|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBrush::operator ID2D1Brush*](#operator_id2d1brush_star)|Devuelve la interfaz ID2D1Brush|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBrush::m_pBrush](#m_pbrush)|Almacena un puntero a un ID2D1Brush objeto.|
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|Propiedades del pincel.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dbrushcd2dbrush"></a><a name="_dtorcd2dbrush"></a>CD2DBrush::-CD2DBrush

Destructor. Se llama cuando se destruye un objeto de pincel D2D.

```
virtual ~CD2DBrush();
```

## <a name="cd2dbrushattach"></a><a name="attach"></a>CD2DBrush::Attach

Asocia la interfaz de recursos existente al objeto.

```cpp
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL.

## <a name="cd2dbrushcd2dbrush"></a><a name="cd2dbrush"></a>CD2DBrush::CD2DBrush

Construye un CD2DBrush objeto.

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero al destino de representación.

*pBrushProperties*<br/>
Un puntero a la opacidad y transformación de un pincel.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

## <a name="cd2dbrushdestroy"></a><a name="destroy"></a>CD2DBrush::Destroy

Destruye un OBJETO CD2DBrush.

```
virtual void Destroy();
```

## <a name="cd2dbrushdetach"></a><a name="detach"></a>CD2DBrush::Detach

Separa la interfaz de recursos del objeto.

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de recursos separada.

## <a name="cd2dbrushget"></a><a name="get"></a>CD2DBrush::Get

Devuelve la interfaz ID2D1Brush

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Brush o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dbrushgetopacity"></a><a name="getopacity"></a>CD2DBrush::GetOpacity

Obtiene el grado de opacidad de este pincel

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor entre cero y 1 que indica la opacidad del pincel. Este valor es un multiplicador constante que escala linealmente el valor alfa de todos los píxeles rellenados por el pincel. Los valores de opacidad se sujetan en el rango 0 a 1 antes de que se multipliquen juntos.

## <a name="cd2dbrushgettransform"></a><a name="gettransform"></a>CD2DBrush::GetTransform

Obtiene la transformación actual del destino de representación

```cpp
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>Parámetros

*Transformar*<br/>
Cuando se devuelve, contiene la transformación actual del destino de representación. Este parámetro se pasa sin inicializar.

## <a name="cd2dbrushisvalid"></a><a name="isvalid"></a>CD2DBrush::IsValid

Comprueba la validez de los recursos

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el recurso es válido; de lo contrario FALSO.

## <a name="cd2dbrushm_pbrush"></a><a name="m_pbrush"></a>CD2DBrush::m_pBrush

Almacena un puntero a un ID2D1Brush objeto.

```
ID2D1Brush* m_pBrush;
```

## <a name="cd2dbrushm_pbrushproperties"></a><a name="m_pbrushproperties"></a>CD2DBrush::m_pBrushProperties

Propiedades del pincel.

```
CD2DBrushProperties* m_pBrushProperties;
```

## <a name="cd2dbrushoperator-id2d1brush"></a><a name="operator_id2d1brush_star"></a>CD2DBrush::operator ID2D1Brush*

Devuelve la interfaz ID2D1Brush

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Brush o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dbrushsetopacity"></a><a name="setopacity"></a>CD2DBrush::SetOpacity

Establece el grado de opacidad de este pincel

```cpp
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>Parámetros

*Opacidad*<br/>
Un valor entre cero y 1 que indica la opacidad del pincel. Este valor es un multiplicador constante que escala linealmente el valor alfa de todos los píxeles rellenados por el pincel. Los valores de opacidad se sujetan en el rango 0 a 1 antes de que se multipliquen juntos.

## <a name="cd2dbrushsettransform"></a><a name="settransform"></a>CD2DBrush::SetTransform

Aplica la transformación especificada al destino de representación, reemplazando la transformación existente. Todas las operaciones de dibujo posteriores se producen en el espacio transformado.

```cpp
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>Parámetros

*Transformar*<br/>
La transformación que se aplicará al destino de representación

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
