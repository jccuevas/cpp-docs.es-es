---
title: Clase CD2DResource
ms.date: 03/27/2019
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
ms.openlocfilehash: 5e747eda42e625d0f4cf65859e471933bbb043ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369091"
---
# <a name="cd2dresource-class"></a>Clase CD2DResource

Una clase abstracta que proporciona una interfaz para crear y administrar recursos D2D como pinceles, capas y textos.

## <a name="syntax"></a>Sintaxis

```
class CD2DResource : public CObject;
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DResource::CD2DResource](#cd2dresource)|Construye un objeto CD2DResource.|
|[CD2DResource::-CD2DResource](#_dtorcd2dresource)|Destructor. Se llama cuando se destruye un objeto de recurso D2D.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DResource::Crear](#create)|Crea un CD2DResource.|
|[CD2DResource::Destroy](#destroy)|Destruye un objeto CD2DResource.|
|[CD2DResource::IsValid](#isvalid)|Comprueba la validez de los recursos|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DResource::IsAutoDestroy](#isautodestroy)|Compruebe la marca de destrucción automática.|
|[CD2DResource::ReCreate](#recreate)|Vuelve a crear un CD2DResource.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|El propietario destruirá el recurso (CRenderTarget)|
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|Puntero al elemento primario CRenderTarget)|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dresourcecd2dresource"></a><a name="_dtorcd2dresource"></a>CD2DResource::-CD2DResource

Destructor. Se llama cuando se destruye un objeto de recurso D2D.

```
virtual ~CD2DResource();
```

## <a name="cd2dresourcecd2dresource"></a><a name="cd2dresource"></a>CD2DResource::CD2DResource

Construye un objeto CD2DResource.

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero al destino de representación.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

## <a name="cd2dresourcecreate"></a><a name="create"></a>CD2DResource::Crear

Crea un CD2DResource.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero al destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dresourcedestroy"></a><a name="destroy"></a>CD2DResource::Destroy

Destruye un objeto CD2DResource.

```
virtual void Destroy() = 0;
```

## <a name="cd2dresourceisautodestroy"></a><a name="isautodestroy"></a>CD2DResource::IsAutoDestroy

Compruebe la marca de destrucción automática.

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el propietario destruirá el objeto; de lo contrario FALSO.

## <a name="cd2dresourceisvalid"></a><a name="isvalid"></a>CD2DResource::IsValid

Comprueba la validez de los recursos

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el recurso es válido; de lo contrario FALSO.

## <a name="cd2dresourcem_bisautodestroy"></a><a name="m_bisautodestroy"></a>CD2DResource::m_bIsAutoDestroy

El propietario destruirá el recurso (CRenderTarget)

```
BOOL m_bIsAutoDestroy;
```

## <a name="cd2dresourcem_pparenttarget"></a><a name="m_pparenttarget"></a>CD2DResource::m_pParentTarget

Puntero al elemento primario CRenderTarget)

```
CRenderTarget* m_pParentTarget;
```

## <a name="cd2dresourcerecreate"></a><a name="recreate"></a>CD2DResource::ReCreate

Vuelve a crear un CD2DResource.

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero al destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
