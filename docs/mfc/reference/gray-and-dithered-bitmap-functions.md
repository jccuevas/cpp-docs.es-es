---
title: funciones de mapa de bits grises o interpoladas
ms.date: 11/19/2018
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
ms.openlocfilehash: a220596b880ee74d5f9ebf683d087156224ee7c5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751481"
---
# <a name="gray-and-dithered-bitmap-functions"></a>funciones de mapa de bits grises o interpoladas

**Funciones de mapa de bits grises**

MFC proporciona dos funciones para dar a un mapa de bits la apariencia de un control deshabilitado.

![Comparación de versiones de icono grises y originales](../../mfc/reference/media/vcgraybitmap.gif "Comparación de versiones de icono grises y originales")

|||
|-|-|
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|Dibuja una versión gris de un mapa de bits.|
|[AfxGetGrayBitmap](#afxgetgraybitmap)|Copia una versión gris de un mapa de bits.|

**Funciones de mapa de bits interpoladas**

MFC también proporciona dos funciones para reemplazar el fondo de un mapa de bits por un patrón interpolado.

![Comparación de versiones de icono interpoladas y originales](../../mfc/reference/media/vcditheredbitmap.gif "Comparación de versiones de icono interpoladas y originales")

|||
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|Dibuja un mapa de bits con un fondo interpolado.|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|Copia un mapa de bits con un fondo interpolado.|

## <a name="afxdrawgraybitmap"></a><a name="afxdrawgraybitmap"></a>AfxDrawGrayBitmap

Dibuja una versión gris de un mapa de bits.

```cpp
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al controlador de dominio de destino.

*x*<br/>
Coordenada X de destino.

*y y*<br/>
Coordenada Y de destino.

*rSrc*<br/>
Mapa de bits de origen.

*crBackground*<br/>
Nuevo color de fondo (normalmente gris, como COLOR_MENU).

### <a name="remarks"></a>Observaciones

Un mapa de bits dibujado con `AfxDrawGrayBitmap` tendrá el aspecto de un control desactivado.

![Comparación de versiones de icono grises y originales](../../mfc/reference/media/vcgraybitmap.gif "Comparación de versiones de icono grises y originales")

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a>AfxGetGrayBitmap

Copia una versión gris de un mapa de bits.

```cpp
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Mapa de bits de origen.

*pDest*<br/>
Mapa de bits de destino.

*crBackground*<br/>
Nuevo color de fondo (normalmente gris, como COLOR_MENU).

### <a name="remarks"></a>Observaciones

Un mapa de bits copiado con `AfxGetGrayBitmap` tendrá el aspecto de un control desactivado.

![Comparación de versiones de icono grises y originales](../../mfc/reference/media/vcgraybitmap.gif "Comparación de versiones de icono grises y originales")

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a>AfxDrawDitheredBitmap

Dibuja un mapa de bits, reemplazando su fondo con un patrón tramado (checker).

```cpp
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al controlador de dominio de destino.

*x*<br/>
Coordenada X de destino.

*y y*<br/>
Coordenada Y de destino.

*rSrc*<br/>
Mapa de bits de origen.

*cr1*<br/>
Uno de los dos colores de tramado, típicamente blanco.

*cr2*<br/>
El otro color de tramado, típicamente gris claro (COLOR_MENU).

### <a name="remarks"></a>Observaciones

El mapa de bits de origen se dibuja en el controlador de dominio de destino con un patrón a cuadros de dos colores (*cr1* y *cr2*) que reemplaza el fondo del mapa de bits. El fondo del mapa de bits de origen se define como sus píxeles blancos y todos los píxeles que coinciden con el color del píxel en la esquina superior izquierda del mapa de bits.

![Comparación de versiones de icono interpoladas y originales](../../mfc/reference/media/vcditheredbitmap.gif "Comparación de versiones de icono interpoladas y originales")

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a>AfxGetDitheredBitmap

Copia un mapa de bits, reemplazando su fondo con un patrón tramado (checker).

```cpp
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parámetros

*rSrc*<br/>
Mapa de bits de origen.

*pDest*<br/>
Mapa de bits de destino.

*cr1*<br/>
Uno de los dos colores de tramado, típicamente blanco.

*cr2*<br/>
El otro color de tramado, típicamente gris claro (COLOR_MENU).

### <a name="remarks"></a>Observaciones

El mapa de bits de origen se copia en el mapa de bits de destino con un patrón a cuadros de dos colores (*cr1* y *cr2*) que reemplaza el fondo del mapa de bits de origen. El fondo del mapa de bits de origen se define como sus píxeles blancos y todos los píxeles que coinciden con el color del píxel en la esquina superior izquierda del mapa de bits.

![Comparación de versiones de icono interpoladas y originales](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="see-also"></a>Vea también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
