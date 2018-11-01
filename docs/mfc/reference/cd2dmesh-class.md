---
title: Clase CD2DMesh
ms.date: 11/04/2016
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
helpviewer_keywords:
- CD2DMesh [MFC], CD2DMesh
- CD2DMesh [MFC], Attach
- CD2DMesh [MFC], Create
- CD2DMesh [MFC], Destroy
- CD2DMesh [MFC], Detach
- CD2DMesh [MFC], Get
- CD2DMesh [MFC], IsValid
- CD2DMesh [MFC], Open
- CD2DMesh [MFC], m_pMesh
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
ms.openlocfilehash: 1cc1769f66b54f2a9a23ef9ad94298687fe4d925
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445648"
---
# <a name="cd2dmesh-class"></a>Clase CD2DMesh

Un contenedor para ID2D1Mesh.

## <a name="syntax"></a>Sintaxis

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DMesh::CD2DMesh](#cd2dmesh)|Construye un objeto CD2DMesh.|
|[CD2DMesh:: ~ CD2DMesh](#_dtorcd2dmesh)|Destructor. Se llama cuando se destruye un objeto de malla D2D.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DMesh::Attach](#attach)|Adjunta existente de la interfaz de recurso para el objeto|
|[CD2DMesh::Create](#create)|Crea un CD2DMesh. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DMesh::Destroy](#destroy)|Destruye un objeto CD2DMesh. (Invalida [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DMesh::Detach](#detach)|Separa la interfaz de recursos desde el objeto|
|[CD2DMesh::Get](#get)|Interfaz de ID2D1Mesh devuelve|
|[CD2DMesh::IsValid](#isvalid)|Comprueba la validez de los recursos (invalidaciones [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DMesh::Open](#open)|Se abre la malla de población.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DMesh::operator ID2D1Mesh *](#operator_id2d1mesh_star)|Interfaz de ID2D1Mesh devuelve|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CD2DMesh::m_pMesh](#m_pmesh)|Un puntero a un ID2D1Mesh.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="_dtorcd2dmesh"></a>  CD2DMesh:: ~ CD2DMesh

Destructor. Se llama cuando se destruye un objeto de malla D2D.

```
virtual ~CD2DMesh();
```

##  <a name="attach"></a>  CD2DMesh::Attach

Adjunta existente de la interfaz de recurso para el objeto

```
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

##  <a name="cd2dmesh"></a>  CD2DMesh::CD2DMesh

Construye un objeto CD2DMesh.

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero para el destino de representación.

*bAutoDestroy*<br/>
Indica que se va a destruir el objeto propietario (pParentTarget).

##  <a name="create"></a>  CD2DMesh::Create

Crea un CD2DMesh.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero para el destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.

##  <a name="destroy"></a>  CD2DMesh::Destroy

Destruye un objeto CD2DMesh.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DMesh::Detach

Separa la interfaz de recursos desde el objeto

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz separada del recurso.

##  <a name="get"></a>  CD2DMesh::Get

Interfaz de ID2D1Mesh devuelve

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Mesh o NULL si el objeto no se ha inicializado todavía.

##  <a name="isvalid"></a>  CD2DMesh::IsValid

Comprobaciones de validez de los recursos

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el recurso es válida; en caso contrario, FALSE.

##  <a name="m_pmesh"></a>  CD2DMesh::m_pMesh

Un puntero a un ID2D1Mesh.

```
ID2D1Mesh* m_pMesh;
```

##  <a name="open"></a>  CD2DMesh::Open

Se abre la malla de población.

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un ID2D1TessellationSink que se usa para rellenar la malla.

##  <a name="operator_id2d1mesh_star"></a>  CD2DMesh::operator ID2D1Mesh *

Interfaz de ID2D1Mesh devuelve

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Mesh o NULL si el objeto no se ha inicializado todavía.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
