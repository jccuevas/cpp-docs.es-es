---
title: CImage (clase)
ms.date: 02/01/2018
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
ms.openlocfilehash: 14a4691e0c1f25a8f9e8b2b652c6e582f51c954a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775951"
---
# <a name="cimage-class"></a>CImage (clase)

`CImage` proporciona compatibilidad con mapas de bits mejorada, incluida la capacidad para cargar y guardar imágenes en los formatos GIF, JPEG, BMP y gráficos de red portátiles (PNG).

> [!IMPORTANT]
> Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CImage
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CImage::CImage](#cimage)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CImage::AlphaBlend](#alphablend)|Muestra los mapas de bits con píxeles transparentes o semitransparentes.|
|[CImage::Attach](#attach)|Asocia un HBITMAP para un `CImage` objeto. Puede utilizarse con mapas de bits de sección no DIB o mapas de bits DIB sección.|
|[CImage::BitBlt](#bitblt)|Copia un mapa de bits desde el contexto de dispositivo de origen en este contexto de dispositivo actual.|
|[CImage::Create](#create)|Crea un mapa de bits de la sección DIB y lo adjunta a construido anteriormente `CImage` objeto.|
|[CImage::CreateEx](#createex)|Crea un mapa de bits de sección DIB (con parámetros adicionales) y lo adjunta a construido anteriormente `CImage` objeto.|
|[CImage::Destroy](#destroy)|Desasocia el mapa de bits desde el `CImage` de objetos y destruye el mapa de bits.|
|[CImage::Detach](#detach)|Desasocia el mapa de bits desde un `CImage` objeto.|
|[CImage::Draw](#draw)|Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino. `Draw` se expande o comprime el mapa de bits para ajustarse a las dimensiones del rectángulo de destino, si es necesario y controla la mezcla alfa y colores transparentes.|
|[CImage::GetBits](#getbits)|Recupera un puntero a los valores reales, en píxeles del mapa de bits.|
|[CImage::GetBPP](#getbpp)|Recupera los bits por píxel.|
|[CImage::GetColorTable](#getcolortable)|Recupera los valores de color rojos, verdes y azules (RGB) de un intervalo de entradas en la tabla de colores.|
|[CImage::GetDC](#getdc)|Recupera el contexto de dispositivo en el que está seleccionado el mapa de bits actual.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Busca los formatos de imagen disponibles y sus descripciones.|
|[CImage::GetHeight](#getheight)|Recupera el alto de la imagen actual en píxeles.|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Busca los formatos de imagen disponibles y sus descripciones.|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Recupera el número máximo de entradas en la tabla de colores.|
|[CImage::GetPitch](#getpitch)|Recupera el tono de la imagen actual, en bytes.|
|[CImage::GetPixel](#getpixel)|Recupera el color del píxel especificado por *x* y *y*.|
|[CImage::GetPixelAddress](#getpixeladdress)|Recupera la dirección de un píxel determinado.|
|[CImage::GetTransparentColor](#gettransparentcolor)|Recupera la posición del color transparente en la tabla de colores.|
|[CImage::GetWidth](#getwidth)|Recupera el ancho de la imagen actual en píxeles.|
|[CImage::IsDIBSection](#isdibsection)|Determina si el mapa de bits adjunta es una sección DIB.|
|[CImage::IsIndexed](#isindexed)|Indica que los colores de un mapa de bits se asignan a una paleta indizada.|
|[CImage::IsNull](#isnull)|Indica si un mapa de bits de origen está cargada actualmente.|
|[CImage::IsTransparencySupported](#istransparencysupported)|Indica si la aplicación admite mapas de bits transparentes.|
|[CImage::Load](#load)|Carga una imagen desde el archivo especificado.|
|[CImage::LoadFromResource](#loadfromresource)|Carga una imagen desde el recurso especificado.|
|[CImage::MaskBlt](#maskblt)|Combina los datos de color para los mapas de bits de origen y destino con la máscara especificada y la operación de trama.|
|[CImage::PlgBlt](#plgblt)|Realiza a una transferencia de bloque de bits de un rectángulo en un contexto de dispositivo de origen en un paralelogramo en un contexto de dispositivo de destino.|
|[CImage::ReleaseDC](#releasedc)|Libera el contexto de dispositivo que se ha recuperado con [CImage::GetDC](#getdc).|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Libera los recursos utilizados por GDI +. Debe llamarse para liberar recursos creados por un global `CImage` objeto.|
|[CImage::Save](#save)|Guarda una imagen como el tipo especificado. `Save` no se puede especificar opciones de imagen.|
|[CImage::SetColorTable](#setcolortable)|Establece el valor RGB de rojo, verde y azul) los valores en un intervalo de entradas en la tabla de colores de la sección DIB de color.|
|[CImage::SetPixel](#setpixel)|Establece el píxel en las coordenadas especificadas en el color especificado.|
|[CImage::SetPixelIndexed](#setpixelindexed)|Establece el píxel en las coordenadas especificadas en el color en el índice especificado de la paleta.|
|[CImage::SetPixelRGB](#setpixelrgb)|Establece el píxel en las coordenadas especificadas al valor especificado de rojo, verde, azul (RGB).|
|[CImage::SetTransparentColor](#settransparentcolor)|Establece el índice del color se traten como transparente. Solo un color de una paleta puede ser transparente.|
|[CImage::StretchBlt](#stretchblt)|Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino, estirando o comprimiendo el mapa de bits para ajustarse a las dimensiones del rectángulo de destino, si es necesario.|
|[CImage::TransparentBlt](#transparentblt)|Copia un mapa de bits con color transparente desde el contexto de dispositivo de origen en este contexto de dispositivo actual.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CImage::operator HBITMAP](#operator_hbitmap)|Devuelve el identificador de Windows asociado a la `CImage` objeto.|

## <a name="remarks"></a>Comentarios

`CImage` toma los mapas de bits que son secciones de cualquier mapa de bits independientes del dispositivo (DIB) o no. Sin embargo, puede usar [crear](#create) o [CImage::Load](#load) con secciones DIB solo. Puede adjuntar un mapa de bits de sección no DIB para un `CImage` objeto [adjuntar](#attach), pero, a continuación, no puede usar el siguiente `CImage` métodos, que admiten solo DIB sección mapas de bits:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Para determinar si un mapa de bits adjunta es una sección DIB, llame a [IsDibSection](#isdibsection).

> [!NOTE]
> En Visual Studio .NET 2003, esta clase mantiene un recuento del número de `CImage` los objetos creados. Cada vez que el recuento llega a 0, la función `GdiplusShutdown` se llama automáticamente para liberar los recursos utilizados por GDI +. Esto garantiza que cualquier `CImage` objetos creados directa o indirectamente por archivos DLL siempre se destruyen correctamente y que `GdiplusShutdown` no se llama desde `DllMain`.

> [!NOTE]
> Uso global `CImage` objetos en un archivo DLL no se recomienda. Si necesita usar un global `CImage` objeto en un archivo DLL, llamada [CImage::ReleaseGDIPlus](#releasegdiplus) liberar explícitamente los recursos utilizados por GDI +.

`CImage` no se pueden seleccionar en un nuevo [CDC](../../mfc/reference/cdc-class.md). `CImage` crea su propio HDC para la imagen. Dado que solo se puede seleccionar un HBITMAP en uno HDC a la vez, HBITMAP asociado con el `CImage` no se pueden seleccionar en otro HDC. Si necesita un CDC, recupere el HDC desde el `CImage` y darle a [CDC::FromHandle] (.. /.. /MFC/Reference/CDC-Class.MD#cdc__fromhandle.

## <a name="example"></a>Ejemplo

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Cuando usas `CImage` en un proyecto MFC, tenga en cuenta que las funciones miembro en el proyecto esperan un puntero a un [CBitmap](../../mfc/reference/cbitmap-class.md) objeto. Si desea usar `CImage` con este tipo de función, como [CMenu:: AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), utilice [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), pasarlo su `CImage` HBITMAP y usar el valor devuelto `CBitmap*`.

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

A través de `CImage`, tendrá acceso a los bits reales de una sección DIB. Puede usar un `CImage` en cualquier parte de objeto usó anteriormente un HBITMAP Win32 o DIB una sección.

Puede usar `CImage` de MFC o ATL.

> [!NOTE]
> Cuando se crea un proyecto mediante `CImage`, debe definir `CString` antes de incluir `atlimage.h`. Si el proyecto usa ATL sin MFC, incluya `atlstr.h` antes de incluir `atlimage.h`. Si el proyecto utiliza MFC (o si es un proyecto ATL con compatibilidad con MFC), incluya `afxstr.h` antes de incluir `atlimage.h`.<br/>
> <br/>
> Del mismo modo, se debe incluir `atlimage.h` antes de incluir `atlimpl.cpp`. Para lograr esto fácilmente, incluir `atlimage.h` en su `stdafx.h`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlimage.h

##  <a name="alphablend"></a>  CImage::AlphaBlend

Muestra los mapas de bits con píxeles transparentes o semitransparentes.

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
Identificador del contexto de dispositivo de destino.

*xDest*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*bSrcAlpha*<br/>
Un valor de transparencia alfa que se usará en el mapa de bits de código fuente. El valor predeterminado de 0xff (255) se da por supuesto que la imagen es opaca y que desea usar solo valores alfa de por píxel.

*bBlendOp*<br/>
La función de combinación alfa para el origen y los mapas de bits de destino, un valor alfa global que se aplicará a la información de formato del mapa de bits de origen y el mapa de bits de código fuente completo. Las funciones de mezcla de origen y destino están limitadas actualmente a AC_SRC_OVER.

*pointDest*<br/>
Una referencia a un [punto](/previous-versions/dd162805\(v=vs.85\)) estructura que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
El alto, en unidades lógicas, del rectángulo de destino.

*xSrc*<br/>
Coordenada x lógica de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
Coordenada y lógica de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
El alto, en unidades lógicas, del rectángulo de origen.

*rectDest*<br/>
Una referencia a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura, que identifica el destino.

*rectSrc*<br/>
Una referencia a un `RECT` estructura, que identifica el origen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Los mapas de bits de la mezcla alfa admiten la mezcla de color por píxel.

Cuando *bBlendOp* se establece en el valor predeterminado de AC_SRC_OVER, el mapa de bits de origen se sitúa sobre el mapa de bits de destino según los valores alfabéticos de los píxeles de origen.

##  <a name="attach"></a>  CImage::Attach

Adjunta *hBitmap* a un `CImage` objeto.

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
Un identificador a un HBITMAP.

*eOrientation*<br/>
Especifica la orientación del mapa de bits. Puede ser uno de los siguientes:

- La orientación del mapa de bits DIBOR_DEFAULT viene determinada por el sistema operativo.

- DIBOR_BOTTOMUP las líneas de mapa de bits están en orden inverso. Esto hace que [CImage::GetBits](#getbits) para devolver un puntero cerca del final del búfer de mapa de bits y [CImage::GetPitch](#getpitch) para devolver un número negativo.

- DIBOR_TOPDOWN las líneas de mapa de bits están en orden descendente. Esto hace que [CImage::GetBits](#getbits) para devolver un puntero al primer byte del búfer de mapa de bits y [CImage::GetPitch](#getpitch) para devolver un número positivo.

### <a name="remarks"></a>Comentarios

El mapa de bits puede ser un mapa de bits de la sección no DIB o un mapa de bits de la sección DIB. Consulte [IsDIBSection](#isdibsection) para obtener una lista de métodos que puede usar solo con DIB sección mapas de bits.

##  <a name="bitblt"></a>  CImage::BitBlt

Copia un mapa de bits desde el contexto de dispositivo de origen en este contexto de dispositivo actual.

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
El destino HDC.

*xDest*<br/>
Coordenada x lógica de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
Coordenada y lógica de la esquina superior izquierda del rectángulo de destino.

*dwROP*<br/>
Para realizar la operación de trama. Códigos de operación de trama definen exactamente cómo combinar los bits de origen, el destino y el patrón (tal y como se define por el pincel actualmente seleccionado) para formar el destino. Consulte [BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) en el SDK de Windows para obtener una lista de otros códigos de operación de trama y sus descripciones.

*pointDest*<br/>
Un [punto](/previous-versions/dd162805\(v=vs.85\)) estructura que indica la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
El alto, en unidades lógicas, del rectángulo de destino.

*xSrc*<br/>
Coordenada x lógica de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
Coordenada y lógica de la esquina superior izquierda del rectángulo de origen.

*rectDest*<br/>
Un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que indica el rectángulo de destino.

*pointSrc*<br/>
Un `POINT` estructura que indica la esquina superior izquierda del rectángulo de origen.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) en el SDK de Windows.

##  <a name="cimage"></a>  CImage::CImage

Construye un objeto `CImage`.

```
CImage() throw();
```

### <a name="remarks"></a>Comentarios

Una vez creado el objeto, llame a [crear](#create), [carga](#load), [LoadFromResource](#loadfromresource), o [adjuntar](#attach) para adjuntar un mapa de bits para el objeto.

**Tenga en cuenta** en Visual Studio, esta clase mantiene un recuento del número de `CImage` los objetos creados. Cada vez que el recuento llega a 0, la función `GdiplusShutdown` se llama automáticamente para liberar los recursos utilizados por GDI +. Esto garantiza que cualquier `CImage` objetos creados directa o indirectamente por archivos DLL siempre se destruyen correctamente y que `GdiplusShutdown` no se llama desde DllMain.

Uso global `CImage` objetos en un archivo DLL no se recomienda. Si necesita usar un global `CImage` objeto en un archivo DLL, llamada [CImage::ReleaseGDIPlus](#releasegdiplus) liberar explícitamente los recursos utilizados por GDI +.

##  <a name="create"></a>  CImage::Create

Crea un `CImage` de mapa de bits y adjuntarlo a construido anteriormente `CImage` objeto.

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parámetros

*nWidth*<br/>
El ancho de la `CImage` mapa de bits, en píxeles.

*nHeight*<br/>
El alto de la `CImage` mapa de bits, en píxeles. Si *nHeight* es positivo, el mapa de bits es un DIB de abajo a arriba y su origen es la esquina inferior izquierda. Si *nHeight* es negativo, el mapa de bits es un DIB de arriba a abajo y su origen es la esquina superior izquierda.

*nBPP*<br/>
El número de bits por píxel del mapa de bits. Normalmente, 4, 8, 16, 24 o 32. Puede ser 1 para los mapas de bits monocromático o máscaras.

*dwFlags*<br/>
Especifica si el objeto de mapa de bits tiene un canal alfa. Puede ser una combinación de cero o más de los siguientes valores:

- *createAlphaChannel* sólo puede utilizarse si *nBPP* es 32, y *eCompression* es BI_RGB. Si se especifica, la imagen creada tiene un valor alfa (transparencia) para cada píxel, almacenado en la 4ª bytes de cada píxel (sin usar en una imagen de 32 bits no son alfanuméricos). Este canal alfa se usa automáticamente cuando se llama a [CImage::AlphaBlend](#alphablend).

> [!NOTE]
> En las llamadas a [CImage::Draw](#draw), las imágenes con un canal alfa son automáticamente alfa mezclado en el destino.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="createex"></a>  CImage::CreateEx

Crea un `CImage` de mapa de bits y adjuntarlo a construido anteriormente `CImage` objeto.

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

*nWidth*<br/>
El ancho de la `CImage` mapa de bits, en píxeles.

*nHeight*<br/>
El alto de la `CImage` mapa de bits, en píxeles. Si *nHeight* es positivo, el mapa de bits es un DIB de abajo a arriba y su origen es la esquina inferior izquierda. Si *nHeight* es negativo, el mapa de bits es un DIB de arriba a abajo y su origen es la esquina superior izquierda.

*nBPP*<br/>
El número de bits por píxel del mapa de bits. Normalmente, 4, 8, 16, 24 o 32. Puede ser 1 para los mapas de bits monocromático o máscaras.

*eCompression*<br/>
Especifica el tipo de compresión para un mapa de bits comprimida de abajo a arriba (no se puede comprimir DIB de arriba a abajo). Puede presentar uno de los siguientes valores:

- El formato BI_RGB están comprimidos. Especificación de este valor cuando se llama a `CImage::CreateEx` equivale a llamar a `CImage::Create`.

- El formato BI_BITFIELDS están comprimidos y la tabla de colores consta de tres de las máscaras de color DWORD que especifican los componentes rojos, verde y azules, respectivamente, de cada píxel. Esto es válido cuando se usa con los mapas de bits de 16 y 32 bpp.

*pdwBitfields*<br/>
Solo se usa si *eCompression* se establece a BI_BITFIELDS, en caso contrario, debe ser NULL. Un puntero a una matriz de tres DWORD las máscaras de bits, especifica los bits de cada píxel se utilizan para los componentes rojos, verde y azules del color, respectivamente. Para obtener información sobre las restricciones para los campos de bits, consulte [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) en el SDK de Windows.

*dwFlags*<br/>
Especifica si el objeto de mapa de bits tiene un canal alfa. Puede ser una combinación de cero o más de los siguientes valores:

- *createAlphaChannel* sólo puede utilizarse si *nBPP* es 32, y *eCompression* es BI_RGB. Si se especifica, la imagen creada tiene un valor alfa (transparencia) para cada píxel, almacenado en la 4ª bytes de cada píxel (sin usar en una imagen de 32 bits no son alfanuméricos). Este canal alfa se usa automáticamente cuando se llama a [CImage::AlphaBlend](#alphablend).

   > [!NOTE]
   > En las llamadas a [CImage::Draw](#draw), las imágenes con un canal alfa son automáticamente alfa mezclado en el destino.

### <a name="return-value"></a>Valor devuelto

TRUE si se realiza correctamente. En caso contrario, FALSE.

### <a name="example"></a>Ejemplo

El ejemplo siguiente crea un mapa de bits de 100 x 100 píxeles, con 16 bits para codificar cada píxel. En un píxel determinado de 16 bits, bits 0-3 codifican el componente rojo, verde de codificación de bits 4-7 y 8-11 bits codifican el azul. Los 4 bits restantes se usan.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>  CImage::Destroy

Desasocia el mapa de bits desde el `CImage` de objetos y destruye el mapa de bits.

```
void Destroy() throw();
```

##  <a name="detach"></a>  CImage::Detach

Desasocia un mapa de bits desde un `CImage` objeto.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Un identificador para el mapa de bits desasociar, o NULL si no se adjunta ningún mapa de bits.

##  <a name="draw"></a>  CImage::Draw

Copia un mapa de bits desde el contexto de dispositivo de origen en el contexto de dispositivo actual.

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
Identificador del contexto de dispositivo de destino.

*xDest*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
El alto, en unidades lógicas, del rectángulo de destino.

*xSrc*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
El alto, en unidades lógicas, del rectángulo de origen.

*rectDest*<br/>
Una referencia a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura, que identifica el destino.

*rectSrc*<br/>
Una referencia a un `RECT` estructura, que identifica el origen.

*pointDest*<br/>
Una referencia a un [punto](/previous-versions/dd162805\(v=vs.85\)) estructura que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

`Draw` realiza la misma operación que [StretchBlt](#stretchblt), a menos que la imagen contiene un color transparente o un canal alfa. En ese caso, `Draw` realiza la misma operación como [TransparentBlt](#transparentblt) o [AlphaBlend](#alphablend) según sea necesario.

Para las versiones de `Draw` que no especifican un rectángulo de origen, la imagen de origen completo es el valor predeterminado. Para la versión de `Draw` que no especifica un tamaño para el rectángulo de destino, el tamaño de la imagen de origen es el valor predeterminado y sin estiramiento o compresión se produce.

##  <a name="getbits"></a>  CImage::GetBits

Recupera un puntero a los valores de bits real de un píxel determinado en un mapa de bits.

```
void* GetBits() throw();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al búfer de mapa de bits. Si el mapa de bits es un DIB de abajo arriba, señala el puntero cerca del final del búfer. Si el mapa de bits es un DIB de arriba a abajo, el puntero apunta al primer byte del búfer.

### <a name="remarks"></a>Comentarios

Mediante este puntero, junto con el valor devuelto por [GetPitch](#getpitch), puede buscar y cambiar los píxeles individuales de una imagen.

> [!NOTE]
> Este método admite solo DIB sección mapas de bits. por lo tanto, tener acceso a los píxeles de un `CImage` la misma manera que lo haría con los píxeles de una sección DIB de objeto. El puntero devuelto señala al píxel en la ubicación (0, 0).

##  <a name="getbpp"></a>  CImage::GetBPP

Recupera el valor de bits por píxel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Valor devuelto

El número de bits por píxel.

### <a name="remarks"></a>Comentarios

Este valor determina el número de bits que definen cada píxel y el número máximo de colores del mapa de bits.

Normalmente, los bits por píxel es 1, 4, 8, 16, 24 o 32. Consulte la `biBitCount` miembro de [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) en el SDK de Windows para obtener más información acerca de este valor.

##  <a name="getcolortable"></a>  CImage::GetColorTable

Recupera los valores de color rojos, verdes y azules (RGB) de un intervalo de entradas en la paleta de la sección DIB.

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parámetros

*iFirstColor*<br/>
El índice de la tabla de color de la primera entrada a recuperar.

*nColors*<br/>
El número de entradas de tabla de color que se recuperarán.

*prgbColors*<br/>
Un puntero a la matriz de [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) estructuras para recuperar el color de entradas de la tabla.

##  <a name="getdc"></a>  CImage::GetDC

Recupera el contexto de dispositivo que tiene actualmente la imagen seleccionada en él.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Valor devuelto

Identificador de un contexto de dispositivo.

### <a name="remarks"></a>Comentarios

Para cada llamada a `GetDC`, debe tener una llamada subsiguiente a [ReleaseDC](#releasedc).

##  <a name="getexporterfilterstring"></a>  CImage::GetExporterFilterString

Busca los formatos de imagen disponible para guardar las imágenes.

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parámetros

*strExporters*<br/>
Referencia a un objeto `CSimpleString`. Consulte **comentarios** para obtener más información.

*aguidFileTypes*<br/>
Una matriz de GUID, con cada elemento que corresponde a uno de los tipos de archivo en la cadena. En el ejemplo de *pszAllFilesDescription* a continuación, *aguidFileTypes*[0] es GUID_NULL y los restantes valores de matriz son los formatos de archivo de imagen admitidos por el sistema operativo actual.

> [!NOTE]
> Para obtener una lista completa de las constantes, consulte **constantes de formato de archivo de imagen** en el SDK de Windows.

*pszAllFilesDescription*<br/>
Si este parámetro no es NULL, la cadena de filtro tendrá un filtro adicional al principio de la lista. Este filtro tendrá el valor actual de *pszAllFilesDescription* para su descripción y acepta archivos de cualquier extensión compatible con cualquier otro exportador en la lista.

Por ejemplo:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Conjunto de marcas de bits que especifica qué tipos de archivo a excluir de la lista. Marcadores permitidos son:

- `excludeGIF` = archivos GIF excluye de 0 x 01.

- `excludeBMP` = archivos BMP excluye (mapa de bits de Windows) de 0 x 02.

- `excludeEMF` = 0 x 04 archivos de excluye EMF (metarchivo mejorado).

- `excludeWMF` = 0 x 08 archivos de excluye WMF (metarchivo de Windows).

- `excludeJPEG` = 0 x 10 archivos de JPEG excluye.

- `excludePNG` = 0 x 20 archivos de excluye PNG.

- `excludeTIFF` = archivos TIFF excluye de 0 x 40.

- `excludeIcon` = 0 x 80 archivos de excluye ICO (icono de Windows).

- `excludeOther` = 0 x 80000000 excluye cualquier otro tipo de archivo no enumerado anteriormente.

- `excludeDefaultLoad` = 0 para la carga, el archivo de todos los tipos se incluyen de forma predeterminada

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Para guardar, estos archivos se excluyen de forma predeterminada porque normalmente tienen requisitos especiales.

*chSeparator*<br/>
El separador usado entre los formatos de imagen. Consulte **comentarios** para obtener más información.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Puede pasar la cadena de formato resultante a la MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) da formato a objetos para exponer las extensiones de archivo de la imagen disponible en el cuadro de diálogo Guardar archivo como.

El parámetro *strExporter* tiene el formato:

archivo description0&#124;\*.ext0&#124;filedescription1&#124;\*. ext1&#124;.. .file descripción *n*&#124;\*.ext *n*&#124;&#124;

donde '&#124;' se especifica el carácter separador por `chSeparator`. Por ejemplo:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Use el separador predeterminado '&#124;' si se pasa esta cadena a una MFC `CFileDialog` objeto. Use el separador nulo '\0' si se pasa esta cadena a un cuadro de diálogo Guardar archivo común.

##  <a name="getheight"></a>  CImage::GetHeight

Recupera el alto, en píxeles, de una imagen.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Valor devuelto

El alto, en píxeles, de una imagen.

##  <a name="getimporterfilterstring"></a>  CImage::GetImporterFilterString

Busca los formatos de imagen disponible para cargar imágenes.

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
Referencia a un objeto `CSimpleString`. Consulte **comentarios** para obtener más información.

*aguidFileTypes*<br/>
Una matriz de GUID, con cada elemento que corresponde a uno de los tipos de archivo en la cadena. En el ejemplo de *pszAllFilesDescription* a continuación, *aguidFileTypes*[0] es GUID_NULL con los valores de matriz restantes son los formatos de archivo de imagen admitidos por el sistema operativo actual.

> [!NOTE]
> Para obtener una lista completa de las constantes, consulte **constantes de formato de archivo de imagen** en el SDK de Windows.

*pszAllFilesDescription*<br/>
Si este parámetro no es NULL, la cadena de filtro tendrá un filtro adicional al principio de la lista. Este filtro tendrá el valor actual de *pszAllFilesDescription* para su descripción y acepta archivos de cualquier extensión compatible con cualquier otro exportador en la lista.

Por ejemplo:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Conjunto de marcas de bits que especifica qué tipos de archivo a excluir de la lista. Marcadores permitidos son:

- `excludeGIF` = archivos GIF excluye de 0 x 01.

- `excludeBMP` = archivos BMP excluye (mapa de bits de Windows) de 0 x 02.

- `excludeEMF` = 0 x 04 archivos de excluye EMF (metarchivo mejorado).

- `excludeWMF` = 0 x 08 archivos de excluye WMF (metarchivo de Windows).

- `excludeJPEG` = 0 x 10 archivos de JPEG excluye.

- `excludePNG` = 0 x 20 archivos de excluye PNG.

- `excludeTIFF` = archivos TIFF excluye de 0 x 40.

- `excludeIcon` = 0 x 80 archivos de excluye ICO (icono de Windows).

- `excludeOther` = 0 x 80000000 excluye cualquier otro tipo de archivo no enumerado anteriormente.

- `excludeDefaultLoad` = 0 para la carga, el archivo de todos los tipos se incluyen de forma predeterminada

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Para guardar, estos archivos se excluyen de forma predeterminada porque normalmente tienen requisitos especiales.

*chSeparator*<br/>
El separador usado entre los formatos de imagen. Consulte **comentarios** para obtener más información.

### <a name="remarks"></a>Comentarios

Puede pasar la cadena de formato resultante a la MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) los formatos de objeto que se va a exponer las extensiones de archivo de la imagen disponible en el **abrir archivo** cuadro de diálogo.

El parámetro *strImporter* tiene el formato:

archivo description0&#124;\*.ext0&#124;filedescription1&#124;\*. ext1&#124;.. .file descripción *n*&#124;\*.ext *n*&#124;&#124;

donde '&#124;' es el carácter separador especificado por *chSeparator*. Por ejemplo:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Use el separador predeterminado '&#124;' si se pasa esta cadena a una MFC `CFileDialog` objeto. Use el separador nulo '\0' si se pasa esta cadena a un común **abrir archivo** cuadro de diálogo.

##  <a name="getmaxcolortableentries"></a>  CImage::GetMaxColorTableEntries

Recupera el número máximo de entradas en la tabla de colores.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Valor devuelto

El número de entradas en la tabla de colores.

### <a name="remarks"></a>Comentarios

Este método admite solo DIB sección mapas de bits.

##  <a name="getpitch"></a>  CImage::GetPitch

Recupera el tono de una imagen.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Valor devuelto

El tono de la imagen. Si el valor devuelto es negativo, el mapa de bits es un DIB de abajo a arriba y su origen es la esquina inferior izquierda. Si el valor devuelto es positivo, el mapa de bits es un DIB de arriba a abajo y su origen es la esquina superior izquierda.

### <a name="remarks"></a>Comentarios

El cabeceo es la distancia, en bytes, entre las dos direcciones de memoria que representan el principio de una línea de mapa de bits y el comienzo de la siguiente línea de mapa de bits. Dado que pitch se mide en bytes, el tono de una imagen le ayudará a determinar el formato de píxel. El tono también puede incluir memoria adicional, reservado para el mapa de bits.

Use `GetPitch` con [GetBits](#getbits) para encontrar los píxeles individuales de una imagen.

> [!NOTE]
> Este método admite solo DIB sección mapas de bits.

##  <a name="getpixel"></a>  CImage::GetPixel

Recupera el color del píxel en la ubicación especificada por *x* y *y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
La coordenada x del píxel.

*y*<br/>
Coordenada y del píxel.

### <a name="return-value"></a>Valor devuelto

El valor de (RGB) de color rojo, verde y azul del píxel. Si es el píxel fuera de la región de recorte actual, el valor devuelto es CLR_INVALID.

##  <a name="getpixeladdress"></a>  CImage::GetPixelAddress

Recupera la dirección exacta de un píxel.

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
La coordenada x del píxel.

*y*<br/>
Coordenada y del píxel.

### <a name="remarks"></a>Comentarios

La dirección se determina según las coordenadas de un píxel, el tono de mapa de bits y los bits por píxel.

Para formatos que tienen menos de 8 bits por píxel, este método devuelve la dirección del byte que contiene el píxel. Por ejemplo, si el formato de imagen tiene 4 bits por píxel, `GetPixelAddress` devuelve la dirección del primer píxel en el byte y debe calcular de 2 píxeles por byte.

> [!NOTE]
> Este método admite solo DIB sección mapas de bits.

##  <a name="gettransparentcolor"></a>  CImage::GetTransparentColor

Recupera la ubicación indizada del color transparente en la paleta de colores.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Valor devuelto

El índice de color transparente.

##  <a name="getwidth"></a>  CImage::GetWidth

Recupera el ancho, en píxeles, de una imagen.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Valor devuelto

El ancho del mapa de bits, en píxeles.

##  <a name="isdibsection"></a>  CImage::IsDIBSection

Determina si el mapa de bits adjunta es una sección DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el mapa de bits adjunta una sección DIB. En caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si el mapa de bits no es una sección DIB, no se puede usar el siguiente `CImage` métodos, que admiten solo DIB sección mapas de bits:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>  CImage::IsIndexed

Determina si los píxeles del mapa de bits se asignan a una paleta de colores.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Valor devuelto

TRUE si indizada; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método devuelve TRUE solo si el mapa de bits es de 8 bits (256 colores) o menos.

> [!NOTE]
> Este método admite solo DIB sección mapas de bits.

##  <a name="isnull"></a>  CImage::IsNull

Determina si un mapa de bits está cargada actualmente.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Comentarios

Este método devuelve TRUE si un mapa de bits no está cargada actualmente; en caso contrario, FALSE.

##  <a name="istransparencysupported"></a>  CImage::IsTransparencySupported

Indica si la aplicación admite mapas de bits transparentes.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la plataforma actual admite la transparencia. En caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si el valor devuelto es distinto de cero y se admite la transparencia, una llamada a [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt), o [dibujar](#draw) controlará colores transparentes.

##  <a name="load"></a>  CImage::Load

Carga una imagen.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Parámetros

*pszFileName*<br/>
Un puntero a una cadena que contiene el nombre del archivo de imagen para cargar.

*pStream*<br/>
Un puntero a una secuencia que contiene el nombre del archivo de imagen para cargar.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Carga la imagen especificada por *pszFileName* o *pStream*.

Tipos de imagen válido son BMP, GIF, JPEG, PNG y TIFF.

##  <a name="loadfromresource"></a>  CImage::LoadFromResource

Carga una imagen desde un recurso de mapa de bits.

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
Identificador de una instancia del módulo que contiene la imagen que se va a cargar.

*pszResourceName*<br/>
Un puntero a la cadena que contiene el nombre del recurso que contiene la imagen para cargar.

*nIDResource*<br/>
El identificador del recurso para cargar.

### <a name="remarks"></a>Comentarios

El recurso debe ser de tipo de mapa de bits.

##  <a name="maskblt"></a>  CImage::MaskBlt

Combina los datos de color para los mapas de bits de origen y destino con la máscara especificada y la operación de trama.

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
El identificador para el módulo cuyo archivo ejecutable contiene el recurso.

*xDest*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del mapa de bits de origen y el rectángulo de destino.

*nDestHeight*<br/>
El alto, en unidades lógicas, del mapa de bits de origen y el rectángulo de destino.

*xSrc*<br/>
Coordenada x lógica de la esquina superior izquierda del mapa de bits de origen.

*ySrc*<br/>
Coordenada y lógica de la esquina superior izquierda del mapa de bits de origen.

*hbmMask*<br/>
Identificador del mapa de bits de máscara monocromática combinado con el mapa de bits de color en el contexto de dispositivo de origen.

*xMask*<br/>
El desplazamiento horizontal de píxel del mapa de bits de máscara especificado por el *hbmMask* parámetro.

*yMask*<br/>
El desplazamiento vertical de píxel del mapa de bits de máscara especificado por el *hbmMask* parámetro.

*dwROP*<br/>
Especifica el primer y segundo plano códigos de operación ternario rasterizado que utiliza el método para controlar la combinación de datos de origen y destino. El código de operación de trama de fondo se almacena en el byte de orden superior de la palabra de orden superior de este valor. el código de operación de trama de primer plano se almacena en el byte de orden inferior de la palabra de orden superior de este valor. la palabra de orden inferior de este valor se omite y debe ser cero. Para obtener una explicación del primer y segundo plano en el contexto de este método, consulte `MaskBlt` en el SDK de Windows. Para obtener una lista de códigos de operación de trama comunes, consulte `BitBlt` en el SDK de Windows.

*rectDest*<br/>
Una referencia a un `RECT` estructura, que identifica el destino.

*pointSrc*<br/>
Un `POINT` estructura que indica la esquina superior izquierda del rectángulo de origen.

*pointMask*<br/>
Un `POINT` estructura que indica la esquina superior izquierda del mapa de bits de máscara.

*pointDest*<br/>
Una referencia a un `POINT` estructura que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Este método se aplica a Windows NT, las versiones 4.0 y versiones posteriores únicamente.

##  <a name="operator_hbitmap"></a>  CImage::operator HBITMAP

Utilice este operador para obtener el identificador de Windows GDI adjunto de la `CImage` objeto. Este es un operador de conversión, que admite el uso directo de un objeto HBITMAP.

##  <a name="plgblt"></a>  CImage::PlgBlt

Realiza a una transferencia de bloque de bits de un rectángulo en un contexto de dispositivo de origen en un paralelogramo en un contexto de dispositivo de destino.

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
Identificador del contexto de dispositivo de destino.

*pPoints*<br/>
Un puntero a una matriz de tres puntos en el espacio lógico que identifican las tres esquinas paralelogramo de destino. La esquina superior izquierda del rectángulo de origen se asigna al primer punto en la esquina inferior izquierda en el tercer punto, la esquina superior derecha para el segundo punto de la matriz y esta matriz. La esquina inferior derecha del rectángulo de origen se asigna al cuarto punto implícito en el paralelogramo.

*hbmMask*<br/>
Identificador de un mapa de bits monocromático opcional que se utiliza para enmascarar los colores del rectángulo de origen.

*xSrc*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
El alto, en unidades lógicas, del rectángulo de origen.

*xMask*<br/>
La coordenada x de la esquina superior izquierda del mapa de bits monocromo.

*yMask*<br/>
Coordenada y de la esquina superior izquierda del mapa de bits monocromo.

*rectSrc*<br/>
Una referencia a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que especifica las coordenadas del rectángulo de origen.

*pointMask*<br/>
Un [punto](/previous-versions/dd162805\(v=vs.85\)) estructura que indica la esquina superior izquierda del mapa de bits de máscara.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Si *hbmMask* identifica un mapa de bits monocromático válido `PlgBit` usa este mapa de bits para enmascarar los bits de datos de color del rectángulo de origen.

Este método se aplica a Windows NT, las versiones 4.0 y versiones posteriores únicamente. Consulte [PlgBlt](/windows/desktop/api/wingdi/nf-wingdi-plgblt) en el SDK de Windows para obtener información más detallada.

##  <a name="releasedc"></a>  CImage::ReleaseDC

Libera el contexto de dispositivo.

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Comentarios

Dado que sólo un mapa de bits se puede seleccionar en un contexto de dispositivo a la vez, debe llamar a `ReleaseDC` para cada llamada a [GetDC](#getdc).

##  <a name="releasegdiplus"></a>  CImage::ReleaseGDIPlus

Libera los recursos utilizados por GDI +.

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Comentarios

Debe llamar a este método para liberar recursos asignados por un global `CImage` objeto. Consulte [CImage::CImage](#cimage).

##  <a name="save"></a>  CImage::Save

Guarda una imagen en la secuencia especificada o el archivo en disco.

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
Un puntero a un objeto COM IStream que contiene los datos de archivo de imagen.

*pszFileName*<br/>
Un puntero al nombre de archivo para la imagen.

*guidFileType*<br/>
El tipo de archivo para guardar la imagen. Puede ser uno de los siguientes:

- `ImageFormatBMP` Una imagen de mapa de bits sin comprimir.

- `ImageFormatPNG` Una imagen comprimida de gráficos de red portátiles (PNG).

- `ImageFormatJPEG` Una imagen JPEG comprimida.

- `ImageFormatGIF` Una imagen GIF comprimida.

> [!NOTE]
> Para obtener una lista completa de las constantes, consulte **constantes de formato de archivo de imagen** en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Llame a esta función para guardar la imagen con un nombre y tipo especificados. Si el *guidFileType* no se incluye el parámetro, se utilizará la extensión de archivo del nombre de archivo para determinar el formato de imagen. Si no se proporciona ninguna extensión, se guardará la imagen en formato BMP.

##  <a name="setcolortable"></a>  CImage::SetColorTable

Establece los valores de color rojos, verdes y azules (RGB) para un intervalo de entradas de la paleta de la sección DIB.

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parámetros

*iFirstColor*<br/>
El índice de la tabla de color de la primera entrada para establecer.

*nColors*<br/>
El número de entradas de la tabla de colores para establecer.

*prgbColors*<br/>
Un puntero a la matriz de [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) entradas estructuras para establecer el color de la tabla.

### <a name="remarks"></a>Comentarios

Este método admite solo DIB sección mapas de bits.

##  <a name="setpixel"></a>  CImage::SetPixel

Establece el color de un píxel en una ubicación especificada en el mapa de bits.

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
La ubicación horizontal del píxel que se va a establecer.

*y*<br/>
Ubicación vertical del píxel que se va a establecer.

*color*<br/>
El color que establecer el píxel.

### <a name="remarks"></a>Comentarios

Este método produce un error si el píxel coordina se encuentran fuera de la región de recorte seleccionado.

##  <a name="setpixelindexed"></a>  CImage::SetPixelIndexed

Establece el color de píxel en el color que se encuentra en *iÍndice* en la paleta de colores.

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
La ubicación horizontal del píxel que se va a establecer.

*y*<br/>
Ubicación vertical del píxel que se va a establecer.

*iIndex*<br/>
El índice de un color en la paleta de colores.

##  <a name="setpixelrgb"></a>  CImage::SetPixelRGB

Establece el píxel en las ubicaciones especificadas por *x* y *y* a los colores indicados por *r*, *g*, y *b*, en una color rojo, verde, azul de la imagen (RGB).

```
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
La ubicación horizontal del píxel que se va a establecer.

*y*<br/>
Ubicación vertical del píxel que se va a establecer.

*r*<br/>
La intensidad del color rojo.

*g*<br/>
La intensidad del color verde.

*b*<br/>
La intensidad del color azul.

### <a name="remarks"></a>Comentarios

Los parámetros de color rojo, verdes y azules se representan mediante un número comprendido entre 0 y 255. Si los tres parámetros se establece en cero, el color resultante combinado es negro. Si los tres parámetros se establece en 255, el color resultante combinado es blanco.

##  <a name="settransparentcolor"></a>  CImage::SetTransparentColor

Establece el color en una ubicación indizada determinada como transparente.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parámetros

*iTransparentColor*<br/>
El índice en una paleta de colores, del color para establecer a transparente. Si-1, ningún color se establece en transparente.

### <a name="return-value"></a>Valor devuelto

El índice del color establecido previamente como transparente.

##  <a name="stretchblt"></a>  CImage::StretchBlt

Copia un mapa de bits desde el contexto de dispositivo de origen en este contexto de dispositivo actual.

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
Identificador del contexto de dispositivo de destino.

*xDest*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
El alto, en unidades lógicas, del rectángulo de destino.

*dwROP*<br/>
Para realizar la operación de trama. Códigos de operación de trama definen exactamente cómo combinar los bits de origen, el destino y el patrón (tal y como se define por el pincel actualmente seleccionado) para formar el destino. Consulte [BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) en el SDK de Windows para obtener una lista de otros códigos de operación de trama y sus descripciones.

*rectDest*<br/>
Una referencia a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura, que identifica el destino.

*xSrc*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
El alto, en unidades lógicas, del rectángulo de origen.

*rectSrc*<br/>
Una referencia a un `RECT` estructura, que identifica el origen.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [StretchBlt](/windows/desktop/api/wingdi/nf-wingdi-stretchblt) en el SDK de Windows.

##  <a name="transparentblt"></a>  CImage::TransparentBlt

Copia un mapa de bits desde el contexto de dispositivo de origen en este contexto de dispositivo actual.

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
Identificador del contexto de dispositivo de destino.

*xDest*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
El alto, en unidades lógicas, del rectángulo de destino.

*crTransparent*<br/>
El color del mapa de bits de origen debe tratar como transparente. De forma predeterminada, CLR_INVALID, que indica que el color actualmente establecido como el color transparente de la imagen debe usarse.

*rectDest*<br/>
Una referencia a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura, que identifica el destino.

*xSrc*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
El ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
El alto, en unidades lógicas, del rectángulo de origen.

*rectSrc*<br/>
Una referencia a un `RECT` estructura, que identifica el origen.

### <a name="return-value"></a>Valor devuelto

TRUE si se realizó correctamente, de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

`TransparentBlt` se admite para los mapas de bits de origen de 4 bits por píxel y 8 bits por píxel. Use [CImage::AlphaBlend](#alphablend) para especificar los mapas de bits de 32 bits por píxel con transparencia.

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

## <a name="see-also"></a>Vea también

[Ejemplo MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[SimpleImage Sample](../../overview/visual-cpp-samples.md)<br/>
[Mapas de bits independientes del dispositivo](/windows/desktop/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)<br/>
[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)<br/>
[Mapas de bits independientes del dispositivo](/windows/desktop/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)
