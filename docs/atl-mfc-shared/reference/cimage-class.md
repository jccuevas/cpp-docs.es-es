---
title: Clase CImage
ms.date: 08/19/2019
f1_keywords:
- CImage
- ATLIMAGE/ATL::CImage
- ATLIMAGE/ATL::CImage::CImage
- ATLIMAGE/ATL::CImage::AlphaBlend
- ATLIMAGE/ATL::CImage::Attach
- ATLIMAGE/ATL::CImage::BitBlt
- ATLIMAGE/ATL::CImage::Create
- ATLIMAGE/ATL::CImage::CreateEx
- ATLIMAGE/ATL::CImage::Destroy
- ATLIMAGE/ATL::CImage::Detach
- ATLIMAGE/ATL::CImage::Draw
- ATLIMAGE/ATL::CImage::GetBits
- ATLIMAGE/ATL::CImage::GetBPP
- ATLIMAGE/ATL::CImage::GetColorTable
- ATLIMAGE/ATL::CImage::GetDC
- ATLIMAGE/ATL::CImage::GetExporterFilterString
- ATLIMAGE/ATL::CImage::GetHeight
- ATLIMAGE/ATL::CImage::GetImporterFilterString
- ATLIMAGE/ATL::CImage::GetMaxColorTableEntries
- ATLIMAGE/ATL::CImage::GetPitch
- ATLIMAGE/ATL::CImage::GetPixel
- ATLIMAGE/ATL::CImage::GetPixelAddress
- ATLIMAGE/ATL::CImage::GetTransparentColor
- ATLIMAGE/ATL::CImage::GetWidth
- ATLIMAGE/ATL::CImage::IsDIBSection
- ATLIMAGE/ATL::CImage::IsIndexed
- ATLIMAGE/ATL::CImage::IsNull
- ATLIMAGE/ATL::CImage::IsTransparencySupported
- ATLIMAGE/ATL::CImage::Load
- ATLIMAGE/ATL::CImage::LoadFromResource
- ATLIMAGE/ATL::CImage::MaskBlt
- ATLIMAGE/ATL::CImage::PlgBlt
- ATLIMAGE/ATL::CImage::ReleaseDC
- ATLIMAGE/ATL::CImage::ReleaseGDIPlus
- ATLIMAGE/ATL::CImage::Save
- ATLIMAGE/ATL::CImage::SetColorTable
- ATLIMAGE/ATL::CImage::SetPixel
- ATLIMAGE/ATL::CImage::SetPixelIndexed
- ATLIMAGE/ATL::CImage::SetPixelRGB
- ATLIMAGE/ATL::CImage::SetTransparentColor
- ATLIMAGE/ATL::CImage::StretchBlt
- ATLIMAGE/ATL::CImage::TransparentBlt
helpviewer_keywords:
- jpeg files
- bitmaps [C++], ATL and MFC support for
- images [C++], ATL and MFC support for
- gif files, ATL and MFC support
- .gif files, ATL and MFC support
- PNG files, ATL and MFC support
- CImage class
- transparent color
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
ms.openlocfilehash: 5b5ef833a3755b07e42a60b24464b1f260062d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317812"
---
# <a name="cimage-class"></a>Clase CImage

`CImage`Proporciona compatibilidad mejorada con mapas de bits, incluida la capacidad de cargar y guardar imágenes en formatos JPEG, GIF, BMP y gráficos de red portátiles (PNG).

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CImage
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImage::CImage](#cimage)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImage::AlphaBlend](#alphablend)|Muestra mapas de bits que tienen píxeles transparentes o semitransparentes.|
|[CImage::Attach](#attach)|Asocia un HBITMAP `CImage` a un objeto. Se puede utilizar con mapas de bits de sección que no sean DIB o mapas de bits de sección DIB.|
|[CImage::BitBlt](#bitblt)|Copia un mapa de bits del contexto del dispositivo de origen a este contexto de dispositivo actual.|
|[CImage::Create](#create)|Crea un mapa de bits de sección DIB y lo adjunta al objeto construido `CImage` anteriormente.|
|[CImage::CreateEx](#createex)|Crea un mapa de bits de sección DIB (con `CImage` parámetros adicionales) y lo asocia al objeto construido anteriormente.|
|[CImage::Destroy](#destroy)|Separa el mapa `CImage` de bits del objeto y destruye el mapa de bits.|
|[CImage::Detach](#detach)|Separa el mapa `CImage` de bits de un objeto.|
|[CImage::Draw](#draw)|Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino. `Draw`estira o comprime el mapa de bits para que se ajuste a las dimensiones del rectángulo de destino, si es necesario, y controla la fusión alfa y los colores transparentes.|
|[CImage::GetBits](#getbits)|Recupera un puntero a los valores de píxel reales del mapa de bits.|
|[CImage::GetBPP](#getbpp)|Recupera los bits por píxel.|
|[CImage::GetColorTable](#getcolortable)|Recupera valores de color rojo, verde, azul (RGB) de un rango de entradas de la tabla de colores.|
|[CImage::GetDC](#getdc)|Recupera el contexto del dispositivo en el que se selecciona el mapa de bits actual.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Busca los formatos de imagen disponibles y sus descripciones.|
|[CImage::GetHeight](#getheight)|Recupera la altura de la imagen actual en píxeles.|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Busca los formatos de imagen disponibles y sus descripciones.|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Recupera el número máximo de entradas en la tabla de colores.|
|[CImage::GetPitch](#getpitch)|Recupera el tono de la imagen actual, en bytes.|
|[CImage::GetPixel](#getpixel)|Recupera el color del píxel especificado por *x* e *y*.|
|[CImage::GetPixelAddress](#getpixeladdress)|Recupera la dirección de un píxel determinado.|
|[CImage::GetTransparentColor](#gettransparentcolor)|Recupera la posición del color transparente en la tabla de colores.|
|[CImage::GetWidth](#getwidth)|Recupera el ancho de la imagen actual en píxeles.|
|[CImage::IsDIBSection](#isdibsection)|Determina si el mapa de bits adjunto es una sección DIB.|
|[CImage::IsIndexed](#isindexed)|Indica que los colores de un mapa de bits se asignan a una paleta indizada.|
|[CImage::IsNull](#isnull)|Indica si se ha cargado actualmente un mapa de bits de origen.|
|[CImage::IsTransparencySupported](#istransparencysupported)|Indica si la aplicación admite mapas de bits transparentes.|
|[CImage::Load](#load)|Carga una imagen desde el archivo especificado.|
|[CImage::LoadFromResource](#loadfromresource)|Carga una imagen desde el recurso especificado.|
|[CImage::MaskBlt](#maskblt)|Combina los datos de color de los mapas de bits de origen y destino utilizando la máscara especificada y la operación ráster.|
|[CImage::PlgBlt](#plgblt)|Realiza una transferencia de bloque de bits desde un rectángulo en un contexto de dispositivo de origen a un paralelogramo en un contexto de dispositivo de destino.|
|[CImage::ReleaseDC](#releasedc)|Libera el contexto del dispositivo que se recuperó con [CImage::GetDC](#getdc).|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Libera los recursos utilizados por GDI+. Debe llamarse para liberar recursos `CImage` creados por un objeto global.|
|[CImage::Guardar](#save)|Guarda una imagen como el tipo especificado. `Save`no puede especificar opciones de imagen.|
|[CImage::SetColorTable](#setcolortable)|Establece valores de color rojo, verde y azul RGB) en un rango de entradas en la tabla de colores de la sección DIB.|
|[CImage::SetPixel](#setpixel)|Establece el píxel en las coordenadas especificadas en el color especificado.|
|[CImage::SetPixelIndexed](#setpixelindexed)|Establece el píxel en las coordenadas especificadas en el color en el índice especificado de la paleta.|
|[CImage::SetPixelRGB](#setpixelrgb)|Establece el píxel en las coordenadas especificadas en el valor rojo, verde, azul (RGB) especificado.|
|[CImage::SetTransparentColor](#settransparentcolor)|Establece el índice del color que se tratará como transparente. Solo un color de una paleta puede ser transparente.|
|[CImage::StretchBlt](#stretchblt)|Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino, estirando o comprimiendo el mapa de bits para ajustarse a las dimensiones del rectángulo de destino, si es necesario.|
|[CImage::TransparentBlt](#transparentblt)|Copia un mapa de bits con color transparente desde el contexto del dispositivo de origen a este contexto de dispositivo actual.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImage::operator HBITMAP](#operator_hbitmap)|Devuelve el identificador de `CImage` Windows asociado al objeto.|

## <a name="remarks"></a>Observaciones

`CImage`toma mapas de bits que son secciones de mapa de bits independientes del dispositivo (DIB) o no; sin embargo, puede usar [Create](#create) o [CImage::Load](#load) con solo secciones DIB. Puede adjuntar un mapa de bits `CImage` de sección que no sea DIB a un objeto mediante [Attach](#attach), pero no puede utilizar los métodos siguientes, `CImage` que solo admiten mapas de bits de sección DIB:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Para determinar si un mapa de bits adjunto es una sección DIB, llame a [IsDibSection](#isdibsection).

> [!NOTE]
> En Visual Studio .NET 2003, esta clase `CImage` mantiene un recuento del número de objetos creados. Cada vez que el recuento `GdiplusShutdown` va a 0, la función se llama automáticamente para liberar los recursos utilizados por GDI+GDI+. Esto garantiza `CImage` que los objetos creados directa o indirectamente `GdiplusShutdown` por los `DllMain`archivos DLL siempre se destruyen correctamente y que no se llama desde .

> [!NOTE]
> No `CImage` se recomienda el uso de objetos globales en un archivo DLL. Si necesita utilizar un `CImage` objeto global en un archivo DLL, llame a [CImage::ReleaseGDIPlus](#releasegdiplus) para liberar explícitamente los recursos utilizados por GDI+GDI+.

`CImage`no se puede seleccionar en un nuevo [CDC](../../mfc/reference/cdc-class.md). `CImage`crea su propio HDC para la imagen. Dado que un HBITMAP solo se puede seleccionar en un HDC a la vez, el HBITMAP asociado a la `CImage` no se puede seleccionar en otro HDC. Si necesita un CDC, recupere `CImage` el HDC del archivo y dárselo a [CDC::FromHandle](../../mfc/reference/cdc-class.md#fromhandle).

## <a name="example"></a>Ejemplo

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Cuando se `CImage` usa en un proyecto MFC, tenga en cuenta qué funciones miembro del proyecto esperan un puntero a un [CBitmap](../../mfc/reference/cbitmap-class.md) objeto. Si desea utilizar `CImage` con una función de este tipo, como [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu) `CImage` , utilice [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), pásele el HBITMAP y utilice el valor devuelto `CBitmap*`.

## <a name="example"></a>Ejemplo

```cpp
void CMyDlg::OnRButtonDown(UINT nFlags, CPoint point)
{
    UNREFERENCED_PARAMETER(nFlags);

    CBitmap* pBitmap = CBitmap::FromHandle(m_myImage);
    m_pmenuPop->AppendMenu(0, ID_BMPCOMMAND, pBitmap);
    ClientToScreen(&point);
    m_pmenuPop->TrackPopupMenu(TPM_RIGHTBUTTON | TPM_LEFTALIGN, point.x,
    point.y, this);
}
```

A `CImage`través de , usted tiene acceso a los bits reales de una sección DIB. Puede utilizar `CImage` un objeto en cualquier lugar en el que haya utilizado anteriormente una sección Win32 HBITMAP o DIB.

Puede usar `CImage` desde MFC o ATL.

> [!NOTE]
> Al crear un `CImage`proyecto mediante `CString` , debe definir antes de incluir *atlimage.h*. Si el proyecto usa ATL sin MFC, incluya *atlstr.h* antes de incluir *atlimage.h*. Si el proyecto utiliza MFC (o si es un proyecto ATL con compatibilidad con MFC), incluya *afxstr.h* antes de incluir *atlimage.h*.<br/>
> <br/>
> Del mismo modo, debe incluir *atlimage.h* antes de incluir *atlimpl.cpp*. Para lograr esto fácilmente, incluya *atlimage.h* en su *pch.h* *(stdafx.h* en Visual Studio 2017 y versiones anteriores).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlimage.h

## <a name="cimagealphablend"></a><a name="alphablend"></a>CImage::AlphaBlend

Muestra mapas de bits que tienen píxeles transparentes o semitransparentes.

```
BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    const POINT& pointDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);

BOOL AlphaBlend(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);
```

### <a name="parameters"></a>Parámetros

*hDestDC*<br/>
Controle el contexto del dispositivo de destino.

*xDest*<br/>
Coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
Coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*bSrcAlpha*<br/>
Un valor de transparencia alfa que se utilizará en todo el mapa de bits de origen. El valor predeterminado 0xff (255) supone que la imagen es opaca y que solo desea usar valores alfa por píxel.

*bBlendOp*<br/>
La función de fusión alfa para mapas de bits de origen y destino, un valor alfa global que se aplicará a todo el mapa de bits de origen y la información de formato para el mapa de bits de origen. Las funciones de mezcla de origen y destino están actualmente limitadas a AC_SRC_OVER.

*pointDest*<br/>
Una referencia a una estructura [POINT](/previous-versions/dd162805\(v=vs.85\)) que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
La altura, en unidades lógicas, del rectángulo de destino.

*xSrc*<br/>
Coordenada x lógica de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
Coordenada y lógica de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
La altura, en unidades lógicas, del rectángulo de origen.

*rectDest*<br/>
Una referencia a una estructura [RECT,](/previous-versions/dd162897\(v=vs.85\)) identificando el destino.

*rectSrc*<br/>
Una referencia `RECT` a una estructura, identificando el origen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Los mapas de bits de mezcla alfa admiten la combinación de colores por píxel.

Cuando *bBlendOp* se establece en el valor predeterminado de AC_SRC_OVER, el mapa de bits de origen se coloca sobre el mapa de bits de destino en función de los valores alfa de los píxeles de origen.

## <a name="cimageattach"></a><a name="attach"></a>CImage::Attach

Adjunta *hBitmap* a `CImage` un objeto.

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
Identificador de un HBITMAP.

*eOrientation*<br/>
Especifica la orientación del mapa de bits. Puede ser uno de los siguientes:

- DIBOR_DEFAULT El sistema operativo determina la orientación del mapa de bits.

- DIBOR_BOTTOMUP Las líneas del mapa de bits están en orden inverso. Esto hace que [CImage::GetBits](#getbits) devuelva un puntero cerca del final del búfer de mapa de bits y [CImage::GetPitch](#getpitch) para devolver un número negativo.

- DIBOR_TOPDOWN Las líneas del mapa de bits están en orden de arriba a abajo. Esto hace que [CImage::GetBits](#getbits) devuelva un puntero al primer byte del búfer de mapa de bits y [CImage::GetPitch](#getpitch) para devolver un número positivo.

### <a name="remarks"></a>Observaciones

El mapa de bits puede ser un mapa de bits de sección no DIB o un mapa de bits de sección DIB. Consulte [IsDIBSection](#isdibsection) para obtener una lista de métodos que solo puede utilizar con mapas de bits de sección DIB.

## <a name="cimagebitblt"></a><a name="bitblt"></a>CImage::BitBlt

Copia un mapa de bits del contexto del dispositivo de origen a este contexto de dispositivo actual.

```
BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const POINT& pointDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parámetros

*hDestDC*<br/>
El HDC de destino.

*xDest*<br/>
Coordenada x lógica de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
Coordenada y lógica de la esquina superior izquierda del rectángulo de destino.

*dwROP*<br/>
La operación ráster que se va a realizar. Los códigos de operación ráster definen exactamente cómo combinar los bits del origen, el destino y el patrón (según lo definido por el pincel seleccionado actualmente) para formar el destino. Consulte [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) en el Windows SDK para obtener una lista de otros códigos de operación ráster y sus descripciones.

*pointDest*<br/>
Estructura [POINT](/previous-versions/dd162805\(v=vs.85\)) que indica la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
La altura, en unidades lógicas, del rectángulo de destino.

*xSrc*<br/>
Coordenada x lógica de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
Coordenada y lógica de la esquina superior izquierda del rectángulo de origen.

*rectDest*<br/>
Estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que indica el rectángulo de destino.

*pointSrc*<br/>
Estructura `POINT` que indica la esquina superior izquierda del rectángulo de origen.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) en el Windows SDK.

## <a name="cimagecimage"></a><a name="cimage"></a>CImage::CImage

Construye un objeto `CImage`.

```
CImage() throw();
```

### <a name="remarks"></a>Observaciones

Una vez que haya construido el objeto, llame a [Create](#create), [Load](#load), [LoadFromResource](#loadfromresource)o [Attach](#attach) para adjuntar un mapa de bits al objeto.

**Nota** En Visual Studio, esta clase mantiene `CImage` un recuento del número de objetos creados. Cada vez que el recuento `GdiplusShutdown` va a 0, la función se llama automáticamente para liberar los recursos utilizados por GDI+GDI+. Esto garantiza `CImage` que los objetos creados directa o indirectamente `GdiplusShutdown` por archivos DLL siempre se destruyen correctamente y que no se llama desde DllMain.

No `CImage` se recomienda el uso de objetos globales en un archivo DLL. Si necesita utilizar un `CImage` objeto global en un archivo DLL, llame a [CImage::ReleaseGDIPlus](#releasegdiplus) para liberar explícitamente los recursos utilizados por GDI+GDI+.

## <a name="cimagecreate"></a><a name="create"></a>CImage::Create

Crea `CImage` un mapa de bits y `CImage` lo adjunta al objeto construido anteriormente.

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parámetros

*nAncho*<br/>
El ancho `CImage` del mapa de bits, en píxeles.

*nAltura*<br/>
La altura `CImage` del mapa de bits, en píxeles. Si *nHeight* es positivo, el mapa de bits es un DIB de abajo hacia arriba y su origen es la esquina inferior izquierda. Si *nHeight* es negativo, el mapa de bits es un DIB de arriba hacia abajo y su origen es la esquina superior izquierda.

*nBPP*<br/>
El número de bits por píxel en el mapa de bits. Por lo general, 4, 8, 16, 24 o 32. Puede ser 1 para mapas de bits o máscaras monocromos.

*dwFlags*<br/>
Especifica si el objeto de mapa de bits tiene un canal alfa. Puede ser una combinación de cero o más de los siguientes valores:

- *createAlphaChannel* Solo se puede utilizar si *nBPP* es 32 y *eCompression* está BI_RGB. Si se especifica, la imagen creada tiene un valor alfa (transparencia) para cada píxel, almacenado en el 4o byte de cada píxel (sin usar en una imagen de 32 bits no alfa). Este canal alfa se utiliza automáticamente al llamar a [CImage::AlphaBlend](#alphablend).

> [!NOTE]
> En las llamadas a [CImage::Draw](#draw), las imágenes con un canal alfa se mezclan automáticamente alfa con el destino.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="cimagecreateex"></a><a name="createex"></a>CImage::CreateEx

Crea `CImage` un mapa de bits y `CImage` lo adjunta al objeto construido anteriormente.

```
BOOL CreateEx(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD eCompression,
    const DWORD* pdwBitmasks = NULL,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parámetros

*nAncho*<br/>
El ancho `CImage` del mapa de bits, en píxeles.

*nAltura*<br/>
La altura `CImage` del mapa de bits, en píxeles. Si *nHeight* es positivo, el mapa de bits es un DIB de abajo hacia arriba y su origen es la esquina inferior izquierda. Si *nHeight* es negativo, el mapa de bits es un DIB de arriba hacia abajo y su origen es la esquina superior izquierda.

*nBPP*<br/>
El número de bits por píxel en el mapa de bits. Por lo general, 4, 8, 16, 24 o 32. Puede ser 1 para mapas de bits o máscaras monocromos.

*eCompression*<br/>
Especifica el tipo de compresión de un mapa de bits comprimido de abajo hacia arriba (los DIB de arriba hacia abajo no se pueden comprimir). Puede ser uno de los siguientes valores:

- BI_RGB El formato no está comprimido. Especificar este valor `CImage::CreateEx` al llamar `CImage::Create`equivale a llamar a .

- BI_BITFIELDS El formato no está comprimido y la tabla de colores consta de tres máscaras de color DWORD que especifican los componentes rojo, verde y azul, respectivamente, de cada píxel. Esto es válido cuando se utiliza con mapas de bits de 16 y 32 bpp.

*pdwBitfields*<br/>
Solo se utiliza si *eCompression* se establece en BI_BITFIELDS, de lo contrario debe ser NULL. Puntero a una matriz de tres máscaras de bits DWORD, especificando qué bits de cada píxel se utilizan para los componentes rojo, verde y azul del color, respectivamente. Para obtener información sobre las restricciones de los campos de bits, vea [BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) en el Windows SDK.

*dwFlags*<br/>
Especifica si el objeto de mapa de bits tiene un canal alfa. Puede ser una combinación de cero o más de los siguientes valores:

- *createAlphaChannel* Solo se puede utilizar si *nBPP* es 32 y *eCompression* está BI_RGB. Si se especifica, la imagen creada tiene un valor alfa (transparencia) para cada píxel, almacenado en el 4o byte de cada píxel (sin usar en una imagen de 32 bits no alfa). Este canal alfa se utiliza automáticamente al llamar a [CImage::AlphaBlend](#alphablend).

   > [!NOTE]
   > En las llamadas a [CImage::Draw](#draw), las imágenes con un canal alfa se mezclan automáticamente alfa con el destino.

### <a name="return-value"></a>Valor devuelto

TRUESi se realiza correctamente. De lo contrario, FALSE.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un mapa de bits de 100x100 píxeles, utilizando 16 bits para codificar cada píxel. En un píxel de 16 bits dado, los bits 0-3 codifican el componente rojo, los bits 4-7 codifican en verde y los bits 8-11 codifican azul. Los 4 bits restantes no se utilizan.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a>CImage::Destroy

Separa el mapa `CImage` de bits del objeto y destruye el mapa de bits.

```
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a>CImage::Detach

Separa un mapa `CImage` de bits de un objeto.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Un identificador del mapa de bits separado, o NULL si no hay ningún mapa de bits asociado.

## <a name="cimagedraw"></a><a name="draw"></a>CImage::Draw

Copia un mapa de bits del contexto del dispositivo de origen en el contexto del dispositivo actual.

```
BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest) const throw();

BOOL Draw(
    HDC hDestDC,
    const POINT& pointDest) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest) const throw();
```

### <a name="parameters"></a>Parámetros

*hDestDC*<br/>
Identificador del contexto del dispositivo de destino.

*xDest*<br/>
Coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
Coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
La altura, en unidades lógicas, del rectángulo de destino.

*xSrc*<br/>
Coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
Coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
La altura, en unidades lógicas, del rectángulo de origen.

*rectDest*<br/>
Una referencia a una estructura [RECT,](/previous-versions/dd162897\(v=vs.85\)) identificando el destino.

*rectSrc*<br/>
Una referencia `RECT` a una estructura, identificando el origen.

*pointDest*<br/>
Una referencia a una estructura [POINT](/previous-versions/dd162805\(v=vs.85\)) que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

`Draw`realiza la misma operación que [StretchBlt](#stretchblt), a menos que la imagen contenga un color transparente o un canal alfa. En ese `Draw` caso, realiza la misma operación que [TransparentBlt](#transparentblt) o [AlphaBlend](#alphablend) según sea necesario.

Para las `Draw` versiones que no especifican un rectángulo de origen, toda la imagen de origen es el valor predeterminado. Para la `Draw` versión que no especifica un tamaño para el rectángulo de destino, el tamaño de la imagen de origen es el valor predeterminado y no se produce ningún estiramiento o reducción.

## <a name="cimagegetbits"></a><a name="getbits"></a>CImage::GetBits

Recupera un puntero a los valores de bits reales de un píxel determinado en un mapa de bits.

```
void* GetBits() throw();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al búfer de mapa de bits. Si el mapa de bits es un DIB de abajo hacia arriba, el puntero apunta cerca del final del búfer. Si el mapa de bits es un DIB de arriba hacia abajo, el puntero apunta al primer byte del búfer.

### <a name="remarks"></a>Observaciones

Con este puntero, junto con el valor devuelto por [GetPitch](#getpitch), puede buscar y cambiar píxeles individuales en una imagen.

> [!NOTE]
> Este método solo admite mapas de bits de sección DIB; por lo tanto, se `CImage` accede a los píxeles de un objeto de la misma manera que lo haría con los píxeles de una sección DIB. El puntero devuelto apunta al píxel en la ubicación (0, 0).

## <a name="cimagegetbpp"></a><a name="getbpp"></a>CImage::GetBPP

Recupera el valor de bits por píxel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Valor devuelto

El número de bits por píxel.

### <a name="remarks"></a>Observaciones

Este valor determina el número de bits que definen cada píxel y el número máximo de colores en el mapa de bits.

Los bits por píxel suelen ser 1, 4, 8, 16, 24 o 32. Consulte `biBitCount` el miembro de [BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) en el Windows SDK para obtener más información acerca de este valor.

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a>CImage::GetColorTable

Recupera valores de color rojo, verde, azul (RGB) de un rango de entradas en la paleta de la sección DIB.

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parámetros

*iFirstColor*<br/>
El índice de tabla de colores de la primera entrada que se va a recuperar.

*nColores*<br/>
El número de entradas de tabla de colores que se van a recuperar.

*prgbColors*<br/>
Puntero a la matriz de estructuras [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) para recuperar las entradas de la tabla de colores.

## <a name="cimagegetdc"></a><a name="getdc"></a>CImage::GetDC

Recupera el contexto del dispositivo que tiene la imagen seleccionada actualmente.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Valor devuelto

Identificador de un contexto de dispositivo.

### <a name="remarks"></a>Observaciones

Para cada `GetDC`llamada a , debe tener una llamada posterior a [ReleaseDC](#releasedc).

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a>CImage::GetExporterFilterString

Busca formatos de imagen disponibles para guardar imágenes.

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parámetros

*strExportadores*<br/>
Referencia a un objeto `CSimpleString`. Consulte **Comentarios** para obtener más información.

*aguidFileTypes*<br/>
Matriz de GUID, con cada elemento correspondiente a uno de los tipos de archivo de la cadena. En el ejemplo de *pszAllFilesDescription* siguiente, *aguidFileTypes*[0] es GUID_NULL y los valores de matriz restantes son los formatos de archivo de imagen admitidos por el sistema operativo actual.

> [!NOTE]
> Para obtener una lista completa de constantes, vea **Constantes** de formato de archivo de imagen en el Windows SDK.

*pszAllFilesDescription*<br/>
Si este parámetro no es NULL, la cadena de filtro tendrá un filtro adicional al principio de la lista. Este filtro tendrá el valor actual de *pszAllFilesDescription* para su descripción y acepta archivos de cualquier extensión compatible con cualquier otro exportador de la lista.

Por ejemplo:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Conjunto de indicadores de bits que especifican qué tipos de archivo se excluirán de la lista. Las marcas permitidas son:

- `excludeGIF`• 0x01 Excluye archivos GIF.

- `excludeBMP`0x02 Excluye archivos BMP (mapa de bits de Windows).

- `excludeEMF`0x04 Excluye archivos EMF (Enhanced Metafile).

- `excludeWMF`0x08 Excluye archivos WMF (Windows Metafile).

- `excludeJPEG`• 0x10 Excluye archivos JPEG.

- `excludePNG`• 0x20 Excluye archivos PNG.

- `excludeTIFF`• 0x40 Excluye archivos TIFF.

- `excludeIcon`• 0x80 Excluye archivos ICO (icono de Windows).

- `excludeOther`• 0x80000000 Excluye cualquier otro tipo de archivo no mencionado anteriormente.

- `excludeDefaultLoad`• 0 Para la carga, todos los tipos de archivo se incluyen de forma predeterminada

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Para guardar, estos archivos se excluyen de forma predeterminada porque suelen tener requisitos especiales.

*chSeparator*<br/>
El separador utilizado entre los formatos de imagen. Consulte **Comentarios** para obtener más información.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Observaciones

Puede pasar la cadena de formato resultante a su MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) objeto para exponer las extensiones de archivo de los formatos de imagen disponibles en el archivo guardar como cuadro de diálogo.

El parámetro *strExporter* tiene el formato:

descripción del \*archivo0&#124;.ext0&#124;filedescription1&#124;\*.ext1&#124;... descripción del \*archivo *n*&#124;.ext *n*&#124;&#124;

donde '&#124;' es el carácter separador especificado por `chSeparator`. Por ejemplo:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Utilice el separador predeterminado '&#124;' si pasa `CFileDialog` esta cadena a un objeto MFC. Utilice el separador nulo '-0' si pasa esta cadena a un cuadro de diálogo común de guardado de archivos.

## <a name="cimagegetheight"></a><a name="getheight"></a>CImage::GetHeight

Recupera la altura, en píxeles, de una imagen.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Valor devuelto

La altura, en píxeles, de una imagen.

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a>CImage::GetImporterFilterString

Busca formatos de imagen disponibles para cargar imágenes.

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parámetros

*strImporters*<br/>
Referencia a un objeto `CSimpleString`. Consulte **Comentarios** para obtener más información.

*aguidFileTypes*<br/>
Matriz de GUID, con cada elemento correspondiente a uno de los tipos de archivo de la cadena. En el ejemplo de *pszAllFilesDescription* siguiente, *aguidFileTypes*[0] se GUID_NULL con los valores de matriz restantes son los formatos de archivo de imagen admitidos por el sistema operativo actual.

> [!NOTE]
> Para obtener una lista completa de constantes, vea **Constantes** de formato de archivo de imagen en el Windows SDK.

*pszAllFilesDescription*<br/>
Si este parámetro no es NULL, la cadena de filtro tendrá un filtro adicional al principio de la lista. Este filtro tendrá el valor actual de *pszAllFilesDescription* para su descripción y acepta archivos de cualquier extensión compatible con cualquier otro exportador de la lista.

Por ejemplo:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Conjunto de indicadores de bits que especifican qué tipos de archivo se excluirán de la lista. Las marcas permitidas son:

- `excludeGIF`• 0x01 Excluye archivos GIF.

- `excludeBMP`0x02 Excluye archivos BMP (mapa de bits de Windows).

- `excludeEMF`0x04 Excluye archivos EMF (Enhanced Metafile).

- `excludeWMF`0x08 Excluye archivos WMF (Windows Metafile).

- `excludeJPEG`• 0x10 Excluye archivos JPEG.

- `excludePNG`• 0x20 Excluye archivos PNG.

- `excludeTIFF`• 0x40 Excluye archivos TIFF.

- `excludeIcon`• 0x80 Excluye archivos ICO (icono de Windows).

- `excludeOther`• 0x80000000 Excluye cualquier otro tipo de archivo no mencionado anteriormente.

- `excludeDefaultLoad`• 0 Para la carga, todos los tipos de archivo se incluyen de forma predeterminada

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Para guardar, estos archivos se excluyen de forma predeterminada porque suelen tener requisitos especiales.

*chSeparator*<br/>
El separador utilizado entre los formatos de imagen. Consulte **Comentarios** para obtener más información.

### <a name="remarks"></a>Observaciones

Puede pasar la cadena de formato resultante a su MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) objeto para exponer las extensiones de archivo de los formatos de imagen disponibles en el cuadro de diálogo **Abrir archivo.**

El parámetro *strImporter* tiene el formato:

descripción del \*archivo0&#124;.ext0&#124;filedescription1&#124;\*.ext1&#124;... descripción del \*archivo *n*&#124;.ext *n*&#124;&#124;

donde '&#124;' es el carácter separador especificado por *chSeparator*. Por ejemplo:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Utilice el separador predeterminado '&#124;' si pasa `CFileDialog` esta cadena a un objeto MFC. Utilice el separador nulo '-0' si pasa esta cadena a un cuadro de diálogo **común De abrir archivo.**

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a>CImage::GetMaxColorTableEntries

Recupera el número máximo de entradas en la tabla de colores.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Valor devuelto

El número de entradas en la tabla de colores.

### <a name="remarks"></a>Observaciones

Este método solo admite mapas de bits de sección DIB.

## <a name="cimagegetpitch"></a><a name="getpitch"></a>CImage::GetPitch

Recupera el tono de una imagen.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Valor devuelto

El tono de la imagen. Si el valor devuelto es negativo, el mapa de bits es un DIB de abajo hacia arriba y su origen es la esquina inferior izquierda. Si el valor devuelto es positivo, el mapa de bits es un DIB de arriba hacia abajo y su origen es la esquina superior izquierda.

### <a name="remarks"></a>Observaciones

El tono es la distancia, en bytes, entre dos direcciones de memoria que representan el principio de una línea de mapa de bits y el principio de la siguiente línea de mapa de bits. Dado que el tono se mide en bytes, el tono de una imagen le ayuda a determinar el formato de píxel. El tono también puede incluir memoria adicional, reservada para el mapa de bits.

Utilícelo `GetPitch` con [GetBits](#getbits) para buscar píxeles individuales de una imagen.

> [!NOTE]
> Este método solo admite mapas de bits de sección DIB.

## <a name="cimagegetpixel"></a><a name="getpixel"></a>CImage::GetPixel

Recupera el color del píxel en la ubicación especificada por *x* e *y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Coordenada x del píxel.

*y y*<br/>
Coordenada y del píxel.

### <a name="return-value"></a>Valor devuelto

El valor rojo, verde, azul (RGB) del píxel. Si el píxel está fuera de la región de recorte actual, el valor devuelto es CLR_INVALID.

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a>CImage::GetPixelAddress

Recupera la dirección exacta de un píxel.

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Coordenada x del píxel.

*y y*<br/>
Coordenada y del píxel.

### <a name="remarks"></a>Observaciones

La dirección se determina según las coordenadas de un píxel, el tono del mapa de bits y los bits por píxel.

Para los formatos que tienen menos de 8 bits por píxel, este método devuelve la dirección del byte que contiene el píxel. Por ejemplo, si el formato de `GetPixelAddress` imagen tiene 4 bits por píxel, devuelve la dirección del primer píxel del byte y debe calcular 2 píxeles por byte.

> [!NOTE]
> Este método solo admite mapas de bits de sección DIB.

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a>CImage::GetTransparentColor

Recupera la ubicación indizada del color transparente en la paleta de colores.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Valor devuelto

El índice del color transparente.

## <a name="cimagegetwidth"></a><a name="getwidth"></a>CImage::GetWidth

Recupera el ancho, en píxeles, de una imagen.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Valor devuelto

El ancho del mapa de bits, en píxeles.

## <a name="cimageisdibsection"></a><a name="isdibsection"></a>CImage::IsDIBSection

Determina si el mapa de bits adjunto es una sección DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Valor devuelto

TRUESi el mapa de bits adjunto es una sección DIB. De lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el mapa de bits no es una `CImage` sección DIB, no puede utilizar los métodos siguientes, que solo admiten mapas de bits de sección DIB:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a>CImage::IsIndexed

Determina si los píxeles de un mapa de bits se asignan a una paleta de colores.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Valor devuelto

TRUESi se indiza; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método devuelve TRUE solo si el mapa de bits es de 8 bits (256 colores) o menos.

> [!NOTE]
> Este método solo admite mapas de bits de sección DIB.

## <a name="cimageisnull"></a><a name="isnull"></a>CImage::IsNull

Determina si un mapa de bits está cargado actualmente.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Observaciones

Este método devuelve TRUE si un mapa de bits no está cargado actualmente; de lo contrario FALSO.

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a>CImage::IsTransparencySupported

Indica si la aplicación admite mapas de bits transparentes.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la plataforma actual admite transparencia. De lo contrario 0.

### <a name="remarks"></a>Observaciones

Si el valor devuelto es distinto de cero y se admite la transparencia, una llamada a [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt)o [Draw](#draw) controlará los colores transparentes.

## <a name="cimageload"></a><a name="load"></a>CImage::Load

Carga una imagen.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Parámetros

*pszFileName*<br/>
Puntero a una cadena que contiene el nombre del archivo de imagen que se va a cargar.

*pStream*<br/>
Puntero a una secuencia que contiene el nombre del archivo de imagen que se va a cargar.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Observaciones

Carga la imagen especificada por *pszFileName* o *pStream*.

Los tipos de imagen válidos son BMP, GIF, JPEG, PNG y TIFF.

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a>CImage::LoadFromResource

Carga una imagen desde un recurso BITMAP.

```
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
Controle una instancia del módulo que contiene la imagen que se va a cargar.

*pszResourceName*<br/>
Puntero a la cadena que contiene el nombre del recurso que contiene la imagen que se va a cargar.

*nIDResource*<br/>
Id. del recurso que se va a cargar.

### <a name="remarks"></a>Observaciones

El recurso debe ser de tipo BITMAP.

## <a name="cimagemaskblt"></a><a name="maskblt"></a>CImage::MaskBlt

Combina los datos de color de los mapas de bits de origen y destino utilizando la máscara especificada y la operación ráster.

```
BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    HBITMAP hbmMask,
    int xMask,
    int yMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    HBITMAP hbmMask,
    const POINT& pointMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const POINT& pointDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parámetros

*hDestDC*<br/>
El identificador del módulo cuyo ejecutable contiene el recurso.

*xDest*<br/>
Coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
Coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino y del mapa de bits de origen.

*nDestHeight*<br/>
Altura, en unidades lógicas, del rectángulo de destino y del mapa de bits de origen.

*xSrc*<br/>
Coordenada x lógica de la esquina superior izquierda del mapa de bits de origen.

*ySrc*<br/>
Coordenada y lógica de la esquina superior izquierda del mapa de bits de origen.

*hbmMask*<br/>
Controle el mapa de bits de máscara monocromo combinado con el mapa de bits de color en el contexto del dispositivo de origen.

*xMask*<br/>
Desplazamiento de píxel horizontal para el mapa de bits de máscara especificado por el parámetro *hbmMask.*

*yMask*<br/>
Desplazamiento de píxel vertical para el mapa de bits de máscara especificado por el parámetro *hbmMask.*

*dwROP*<br/>
Especifica los códigos de operación ráster ternaria de primer plano y de fondo que el método utiliza para controlar la combinación de datos de origen y destino. El código de operación ráster de fondo se almacena en el byte de orden superior de la palabra de orden superior de este valor; el código de operación ráster en primer plano se almacena en el byte de orden inferior de la palabra de orden superior de este valor; la palabra de orden bajo de este valor se omite y debe ser cero. Para obtener una explicación de primer plano `MaskBlt` y fondo en el contexto de este método, vea en el Windows SDK. Para obtener una lista de `BitBlt` códigos de operación ráster comunes, consulte en el Windows SDK.

*rectDest*<br/>
Una referencia `RECT` a una estructura, identificando el destino.

*pointSrc*<br/>
Estructura `POINT` que indica la esquina superior izquierda del rectángulo de origen.

*pointMask*<br/>
Estructura `POINT` que indica la esquina superior izquierda del mapa de bits de máscara.

*pointDest*<br/>
Una referencia `POINT` a una estructura que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método solo se aplica a Windows NT, versiones 4.0 y posteriores.

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a>CImage::operator HBITMAP

Utilice este operador para obtener el identificador `CImage` GDI de Windows adjunto del objeto. Este operador es un operador de conversión, que admite el uso directo de un objeto HBITMAP.

## <a name="cimageplgblt"></a><a name="plgblt"></a>CImage::PlgBlt

Realiza una transferencia de bloque de bits desde un rectángulo en un contexto de dispositivo de origen a un paralelogramo en un contexto de dispositivo de destino.

```
BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    HBITMAP hbmMask = NULL) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    HBITMAP hbmMask = NULL,
    int xMask = 0,
    int yMask = 0) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    const RECT& rectSrc,
    HBITMAP hbmMask = NULL,
    const POINT& pointMask = CPoint(0, 0)) const throw();
```

### <a name="parameters"></a>Parámetros

*hDestDC*<br/>
Identificador del contexto del dispositivo de destino.

*puntos p*<br/>
Puntero a una matriz de tres puntos en el espacio lógico que identifican tres esquinas del paralelogramo de destino. La esquina superior izquierda del rectángulo de origen se asigna al primer punto de esta matriz, la esquina superior derecha al segundo punto de esta matriz y la esquina inferior izquierda al tercer punto. La esquina inferior derecha del rectángulo de origen se asigna al cuarto punto implícito del paralelogramo.

*hbmMask*<br/>
Identificador de un mapa de bits monocromo opcional que se utiliza para enmascarar los colores del rectángulo de origen.

*xSrc*<br/>
Coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
Coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
La altura, en unidades lógicas, del rectángulo de origen.

*xMask*<br/>
Coordenada x de la esquina superior izquierda del mapa de bits monocromo.

*yMask*<br/>
Coordenada y de la esquina superior izquierda del mapa de bits monocromo.

*rectSrc*<br/>
Una referencia a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que especifica las coordenadas del rectángulo de origen.

*pointMask*<br/>
Estructura [POINT](/previous-versions/dd162805\(v=vs.85\)) que indica la esquina superior izquierda del mapa de bits de máscara.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si *hbmMask* identifica un mapa `PlgBit` de bits monocromo válido, utiliza este mapa de bits para enmascarar los bits de datos de color del rectángulo de origen.

Este método solo se aplica a Windows NT, versiones 4.0 y posteriores. Consulte [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) en el Windows SDK para obtener información más detallada.

## <a name="cimagereleasedc"></a><a name="releasedc"></a>CImage::ReleaseDC

Libera el contexto del dispositivo.

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Observaciones

Dado que solo se puede seleccionar un mapa de `ReleaseDC` bits en un contexto de dispositivo a la vez, debe llamar para cada llamada a [GetDC](#getdc).

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a>CImage::ReleaseGDIPlus

Libera los recursos utilizados por GDI+.

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Observaciones

Este método debe llamarse a los `CImage` recursos libres asignados por un objeto global. Vea [CImage::CImage](#cimage).

## <a name="cimagesave"></a><a name="save"></a>CImage::Guardar

Guarda una imagen en la secuencia o archivo especificado en el disco.

```
HRESULT Save(
    IStream* pStream,
    REFGUID guidFileType) const throw();

HRESULT Save(
    LPCTSTR pszFileName,
    REFGUID guidFileType = GUID_NULL) const throw();
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
Puntero a un objeto COM IStream que contiene los datos de imagen de archivo.

*pszFileName*<br/>
Un puntero al nombre de archivo de la imagen.

*guidFileType*<br/>
El tipo de archivo para guardar la imagen como. Puede ser uno de los siguientes:

- `ImageFormatBMP`Una imagen de mapa de bits sin comprimir.

- `ImageFormatPNG`Una imagen comprimida de gráfico de red portátil (PNG).

- `ImageFormatJPEG`Una imagen comprimida JPEG.

- `ImageFormatGIF`Una imagen comprimida GIF.

> [!NOTE]
> Para obtener una lista completa de constantes, vea **Constantes** de formato de archivo de imagen en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Observaciones

Llame a esta función para guardar la imagen con un nombre y un tipo especificados. Si no se incluye el parámetro *guidFileType,* se utilizará la extensión de archivo del nombre de archivo para determinar el formato de imagen. Si no se proporciona ninguna extensión, la imagen se guardará en formato BMP.

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a>CImage::SetColorTable

Establece los valores de color rojo, verde, azul (RGB) para un rango de entradas en la paleta de la sección DIB.

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parámetros

*iFirstColor*<br/>
El índice de la tabla de colores de la primera entrada que se ha establecido.

*nColores*<br/>
El número de entradas de tabla de colores que se han establecido.

*prgbColors*<br/>
Puntero a la matriz de estructuras [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) para establecer las entradas de la tabla de colores.

### <a name="remarks"></a>Observaciones

Este método solo admite mapas de bits de sección DIB.

## <a name="cimagesetpixel"></a><a name="setpixel"></a>CImage::SetPixel

Establece el color de un píxel en una ubicación determinada del mapa de bits.

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parámetros

*X*<br/>
La ubicación horizontal del píxel que se ha de establecer.

*y y*<br/>
La ubicación vertical del píxel que se ha establecido.

*color*<br/>
El color en el que se establece el píxel.

### <a name="remarks"></a>Observaciones

Este método produce un error si las coordenadas de píxel se encuentran fuera de la región de recorte seleccionada.

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a>CImage::SetPixelIndexed

Establece el color del píxel en el color situado en *iIndex* en la paleta de colores.

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parámetros

*X*<br/>
La ubicación horizontal del píxel que se ha de establecer.

*y y*<br/>
La ubicación vertical del píxel que se ha establecido.

*iIndex*<br/>
El índice de un color en la paleta de colores.

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a>CImage::SetPixelRGB

Establece el píxel en las ubicaciones especificadas por *x* e *y* en los colores indicados por *r*, *g*y *b*, en una imagen roja, verde, azul (RGB).

```
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Parámetros

*X*<br/>
La ubicación horizontal del píxel que se ha de establecer.

*y y*<br/>
La ubicación vertical del píxel que se ha establecido.

*R*<br/>
La intensidad del color rojo.

*G*<br/>
La intensidad del color verde.

*B*<br/>
La intensidad del color azul.

### <a name="remarks"></a>Observaciones

Los parámetros rojo, verde y azul están representados por un número entre 0 y 255. Si establece los tres parámetros en cero, el color resultante combinado es negro. Si establece los tres parámetros en 255, el color resultante combinado es blanco.

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a>CImage::SetTransparentColor

Establece un color en una ubicación indizada determinada como transparente.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parámetros

*iTransparentColor*<br/>
El índice, en una paleta de colores, del color que se establecerá en transparente. Si -1, no se establece ningún color en transparente.

### <a name="return-value"></a>Valor devuelto

El índice del color establecido previamente como transparente.

## <a name="cimagestretchblt"></a><a name="stretchblt"></a>CImage::StretchBlt

Copia un mapa de bits del contexto del dispositivo de origen a este contexto de dispositivo actual.

```
BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parámetros

*hDestDC*<br/>
Identificador del contexto del dispositivo de destino.

*xDest*<br/>
Coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
Coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
La altura, en unidades lógicas, del rectángulo de destino.

*dwROP*<br/>
La operación ráster que se va a realizar. Los códigos de operación ráster definen exactamente cómo combinar los bits del origen, el destino y el patrón (según lo definido por el pincel seleccionado actualmente) para formar el destino. Consulte [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) en el Windows SDK para obtener una lista de otros códigos de operación ráster y sus descripciones.

*rectDest*<br/>
Una referencia a una estructura [RECT,](/previous-versions/dd162897\(v=vs.85\)) identificando el destino.

*xSrc*<br/>
Coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
Coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
La altura, en unidades lógicas, del rectángulo de origen.

*rectSrc*<br/>
Una referencia `RECT` a una estructura, identificando el origen.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) en el Windows SDK.

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a>CImage::TransparentBlt

Copia un mapa de bits del contexto del dispositivo de origen a este contexto de dispositivo actual.

```
BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    UINT crTransparent = CLR_INVALID) const throw();
```

### <a name="parameters"></a>Parámetros

*hDestDC*<br/>
Identificador del contexto del dispositivo de destino.

*xDest*<br/>
Coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
Coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
La altura, en unidades lógicas, del rectángulo de destino.

*crTransparent*<br/>
El color del mapa de bits de origen para tratarcomo transparente. De forma predeterminada, CLR_INVALID, lo que indica que se debe utilizar el color establecido actualmente como color transparente de la imagen.

*rectDest*<br/>
Una referencia a una estructura [RECT,](/previous-versions/dd162897\(v=vs.85\)) identificando el destino.

*xSrc*<br/>
Coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
Coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
La altura, en unidades lógicas, del rectángulo de origen.

*rectSrc*<br/>
Una referencia `RECT` a una estructura, identificando el origen.

### <a name="return-value"></a>Valor devuelto

TRUESi se realiza correctamente, de lo contrario FALSE.

### <a name="remarks"></a>Observaciones

`TransparentBlt`es compatible con mapas de bits de origen de 4 bits por píxel y 8 bits por píxel. Utilice [CImage::AlphaBlend](#alphablend) para especificar mapas de bits de 32 bits por píxel con transparencia.

### <a name="example"></a>Ejemplo

```cpp
// Performs a transparent blit from the source image to the destination
// image using the images' current transparency settings
BOOL TransparentBlt(CImage* pSrcImage, CImage* pDstImage,
       int xDest, int yDest, int nDestWidth, int nDestHeight)
{
    HDC hDstDC = NULL;
    BOOL bResult;

    if(pSrcImage == NULL || pDstImage == NULL)
    {
        // Invalid parameter
        return FALSE;
    }

    // Obtain a DC to the destination image
    hDstDC = pDstImage->GetDC();
    // Perform the blit
    bResult = pSrcImage->TransparentBlt(hDstDC, xDest, yDest, nDestWidth, nDestHeight);

    // Release the destination DC
    pDstImage->ReleaseDC();

    return bResult;
}
```

## <a name="see-also"></a>Consulte también

[MMXSwarm Sample](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de SimpleImage](../../overview/visual-cpp-samples.md)<br/>
[Mapas de bits independientes del dispositivo](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)<br/>
[Mapas de bits independientes del dispositivo](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
