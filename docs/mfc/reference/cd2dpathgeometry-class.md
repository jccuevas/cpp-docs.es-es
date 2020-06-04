---
title: Clase CD2DPathGeometry
ms.date: 11/04/2016
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
ms.openlocfilehash: 91460e3435130530ecc57bdcc09d1c7301333a3b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753078"
---
# <a name="cd2dpathgeometry-class"></a>Clase CD2DPathGeometry

Un contenedor para ID2D1PathGeometry.

## <a name="syntax"></a>Sintaxis

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|Construye un CD2DPathGeometry objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DPathGeometry::Attach](#attach)|Adjunta la interfaz de recursos existente al objeto|
|[CD2DPathGeometry::Crear](#create)|Crea un CD2DPathGeometry. (Reemplaza [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DPathGeometry::Destroy](#destroy)|Destruye un objeto CD2DPathGeometry. (Reemplaza [CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|
|[CD2DPathGeometry::Detach](#detach)|Separa la interfaz de recursos del objeto|
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Recupera el número de figuras en la geometría del trazado.|
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Recupera el número de segmentos de la geometría del trazado.|
|[CD2DPathGeometry::Open](#open)|Recupera el sumidero de geometría que se utiliza para rellenar la geometría de ruta con figuras y segmentos.|
|[CD2DPathGeometry::Stream](#stream)|Copia el contenido de la geometría de ruta de acceso en el ID2D1GeometrySink especificado.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|Un puntero a un ID2D1PathGeometry.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dpathgeometryattach"></a><a name="attach"></a>CD2DPathGeometry::Attach

Adjunta la interfaz de recursos existente al objeto

```cpp
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

## <a name="cd2dpathgeometrycd2dpathgeometry"></a><a name="cd2dpathgeometry"></a>CD2DPathGeometry::CD2DPathGeometry

Construye un CD2DPathGeometry objeto.

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero al destino de representación.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

## <a name="cd2dpathgeometrycreate"></a><a name="create"></a>CD2DPathGeometry::Crear

Crea un CD2DPathGeometry.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero al destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dpathgeometrydestroy"></a><a name="destroy"></a>CD2DPathGeometry::Destroy

Destruye un objeto CD2DPathGeometry.

```
virtual void Destroy();
```

## <a name="cd2dpathgeometrydetach"></a><a name="detach"></a>CD2DPathGeometry::Detach

Separa la interfaz de recursos del objeto

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de recursos separada.

## <a name="cd2dpathgeometrygetfigurecount"></a><a name="getfigurecount"></a>CD2DPathGeometry::GetFigureCount

Recupera el número de figuras en la geometría del trazado.

```
int GetFigureCount() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de figuras de la geometría de ruta.

## <a name="cd2dpathgeometrygetsegmentcount"></a><a name="getsegmentcount"></a>CD2DPathGeometry::GetSegmentCount

Recupera el número de segmentos de la geometría del trazado.

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de segmentos de la geometría de ruta de acceso.

## <a name="cd2dpathgeometrym_ppathgeometry"></a><a name="m_ppathgeometry"></a>CD2DPathGeometry::m_pPathGeometry

Un puntero a un ID2D1PathGeometry.

```
ID2D1PathGeometry* m_pPathGeometry;
```

## <a name="cd2dpathgeometryopen"></a><a name="open"></a>CD2DPathGeometry::Open

Recupera el sumidero de geometría que se utiliza para rellenar la geometría de ruta con figuras y segmentos.

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>Valor devuelto

Puntero al ID2D1GeometrySink que se utiliza para rellenar la geometría del trazado con figuras y segmentos.

## <a name="cd2dpathgeometrystream"></a><a name="stream"></a>CD2DPathGeometry::Stream

Copia el contenido de la geometría de ruta de acceso en el ID2D1GeometrySink especificado.

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>Parámetros

*geometrySink*<br/>
El receptor en el que se copia el contenido de la geometría de ruta. Modificar este receptor no cambia el contenido de esta geometría de ruta de acceso.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
