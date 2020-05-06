---
title: CImage (clase)
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
ms.openlocfilehash: a79012e7f2750a4eab12318ffcd52e5e15c30c83
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825610"
---
# <a name="cimage-class"></a>CImage (clase)

`CImage`proporciona compatibilidad mejorada con mapas de bits, incluida la capacidad de cargar y guardar imágenes en formatos JPEG, GIF, BMP y Portable Network Graphics (PNG).

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CImage
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImage:: CImage](#cimage)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImage:: AlphaBlend](#alphablend)|Muestra los mapas de bits que tienen píxeles transparentes o semitransparentes.|
|[CImage:: Attach](#attach)|Adjunta un HBITMAP a un `CImage` objeto. Se puede usar con mapas de bits de sección no DIB o mapas de bits de sección DIB.|
|[CImage:: BitBlt](#bitblt)|Copia un mapa de bits desde el contexto de dispositivo de origen a este contexto de dispositivo actual.|
|[CImage:: Create](#create)|Crea un mapa de bits de sección DIB y lo adjunta al objeto `CImage` construido previamente.|
|[CImage:: CreateEx](#createex)|Crea un mapa de bits de sección DIB (con parámetros adicionales) y lo adjunta al objeto `CImage` construido previamente.|
|[CImage::D estroy](#destroy)|Desasocia el mapa de bits `CImage` del objeto y destruye el mapa de bits.|
|[CImage::D Etach](#detach)|Desasocia el mapa de bits `CImage` de un objeto.|
|[CImage::D RAW](#draw)|Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino. `Draw`estira o comprime el mapa de bits para ajustarse a las dimensiones del rectángulo de destino, si es necesario, y controla la combinación alfa y los colores transparentes.|
|[CImage:: GetBits](#getbits)|Recupera un puntero a los valores de píxel reales del mapa de bits.|
|[CImage:: GetBPP](#getbpp)|Recupera los bits por píxel.|
|[CImage:: GetColorTable](#getcolortable)|Recupera los valores de color rojo, verde y azul (RGB) de un intervalo de entradas de la tabla de colores.|
|[CImage:: GetDC](#getdc)|Recupera el contexto de dispositivo en el que está seleccionado el mapa de bits actual.|
|[CImage:: GetExporterFilterString](#getexporterfilterstring)|Busca los formatos de imagen disponibles y sus descripciones.|
|[CImage:: GetHeight](#getheight)|Recupera el alto de la imagen actual en píxeles.|
|[CImage:: GetImporterFilterString](#getimporterfilterstring)|Busca los formatos de imagen disponibles y sus descripciones.|
|[CImage:: GetMaxColorTableEntries](#getmaxcolortableentries)|Recupera el número máximo de entradas de la tabla de colores.|
|[CImage:: GetPitch](#getpitch)|Recupera el paso de la imagen actual, en bytes.|
|[CImage:: GetPixel](#getpixel)|Recupera el color del píxel especificado por *x* *e y*.|
|[CImage:: GetPixelAddress](#getpixeladdress)|Recupera la dirección de un píxel determinado.|
|[CImage:: GetTransparentColor](#gettransparentcolor)|Recupera la posición del color transparente en la tabla de colores.|
|[CImage:: GetWidth](#getwidth)|Recupera el ancho de la imagen actual en píxeles.|
|[CImage:: IsDIBSection](#isdibsection)|Determina si el mapa de bits adjunto es una sección DIB.|
|[CImage:: IsIndexed](#isindexed)|Indica que los colores de un mapa de bits están asignados a una paleta indizada.|
|[CImage:: IsNull](#isnull)|Indica si un mapa de bits de origen está cargado actualmente.|
|[CImage:: IsTransparencySupported](#istransparencysupported)|Indica si la aplicación admite mapas de bits transparentes.|
|[CImage:: Load](#load)|Carga una imagen desde el archivo especificado.|
|[CImage:: LoadFromResource](#loadfromresource)|Carga una imagen desde el recurso especificado.|
|[CImage:: MaskBlt](#maskblt)|Combina los datos de color de los mapas de bits de origen y de destino usando la máscara y la operación de trama especificadas.|
|[CImage::P lgBlt](#plgblt)|Realiza una transferencia de bloque de bits de un rectángulo en un contexto de dispositivo de origen a un paralelogramo en un contexto de dispositivo de destino.|
|[CImage:: ReleaseDC](#releasedc)|Libera el contexto de dispositivo que se recuperó con [CImage:: GetDC](#getdc).|
|[CImage:: ReleaseGDIPlus](#releasegdiplus)|Libera los recursos que usa GDI+. Se debe llamar a para liberar los recursos creados por `CImage` un objeto global.|
|[CImage:: Save](#save)|Guarda una imagen como el tipo especificado. `Save`no se pueden especificar opciones de imagen.|
|[CImage:: SetColorTable](#setcolortable)|Establece valores de color rojo, verde y azul RGB) en un intervalo de entradas de la tabla de colores de la sección DIB.|
|[CImage:: SetPixel](#setpixel)|Establece el píxel en las coordenadas especificadas en el color especificado.|
|[CImage:: SetPixelIndexed](#setpixelindexed)|Establece el píxel de las coordenadas especificadas en el color que se encuentra en el índice especificado de la paleta.|
|[CImage:: SetPixelRGB](#setpixelrgb)|Establece el píxel en las coordenadas especificadas en el valor rojo, verde y azul (RGB) especificado.|
|[CImage:: SetTransparentColor](#settransparentcolor)|Establece el índice del color que se va a tratar como transparente. Solo un color de una paleta puede ser transparente.|
|[CImage:: StretchBlt](#stretchblt)|Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino, ajustando o comprimiendo el mapa de bits para ajustarse a las dimensiones del rectángulo de destino, si es necesario.|
|[CImage:: TransparentBlt](#transparentblt)|Copia un mapa de bits con un color transparente desde el contexto del dispositivo de origen a este contexto de dispositivo actual.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImage:: Operator HBITMAP](#operator_hbitmap)|Devuelve el identificador de Windows asociado al `CImage` objeto.|

## <a name="remarks"></a>Observaciones

`CImage`toma los mapas de bits que son secciones de mapa de bits independientes del dispositivo (DIB) o no; sin embargo, puede usar [Create](#create) o [CImage:: Load](#load) solo con secciones Dib. Puede adjuntar un mapa de bits de sección no `CImage` DIB a un objeto mediante [Attach](#attach), pero después no puede `CImage` usar los métodos siguientes, que solo admiten mapas de bits de la sección DIB:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Para determinar si un mapa de bits adjunto es una sección DIB, llame a [IsDibSection](#isdibsection).

> [!NOTE]
> En Visual Studio .NET 2003, esta clase mantiene un recuento del número de `CImage` objetos creados. Siempre que el recuento llega a 0, `GdiplusShutdown` se llama automáticamente a la función para liberar los recursos utilizados por GDI+. Esto garantiza que los `CImage` objetos creados directa o indirectamente mediante archivos DLL se destruyan siempre `GdiplusShutdown` correctamente y que no `DllMain`se llame a desde.

> [!NOTE]
> No se `CImage` recomienda el uso de objetos globales en un archivo dll. Si necesita usar un objeto global `CImage` en un archivo dll, llame a [CImage:: ReleaseGDIPlus](#releasegdiplus) para liberar explícitamente los recursos utilizados por GDI+.

`CImage`no se puede seleccionar en un nuevo [CDC](../../mfc/reference/cdc-class.md). `CImage`crea su propio HDC para la imagen. Dado que un HBITMAP solo se puede seleccionar en una HDC a la vez, el HBITMAP asociado a `CImage` no se puede seleccionar en otra HDC. Si necesita un CDC, recupere la HDC desde `CImage` y proporciónele a [CDC:: FromHandle](../../mfc/reference/cdc-class.md#fromhandle).

## <a name="example"></a>Ejemplo

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Cuando se usa `CImage` en un proyecto MFC, tenga en cuenta qué funciones miembro del proyecto esperan un puntero a un objeto [CBitmap](../../mfc/reference/cbitmap-class.md) . Si desea `CImage` usar con este tipo de función, como [CMenu:: AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), use [CBitmap:: FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), pásele su `CImage` hBitmap y use el devuelto. `CBitmap*`

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

A `CImage`través de, tiene acceso a los bits reales de una sección Dib. Puede usar un `CImage` objeto en cualquier lugar en el que haya usado anteriormente una sección hBitmap o DIB de Win32.

Puede usar `CImage` desde MFC o ATL.

> [!NOTE]
> Al crear un proyecto mediante `CImage`, debe definir `CString` antes de incluir *atlimage. h*. Si el proyecto utiliza ATL sin MFC, incluya *atlstr. h* antes de incluir *atlimage. h*. Si el proyecto usa MFC (o si es un proyecto ATL con compatibilidad con MFC), incluya *afxstr. h* antes de incluir *atlimage. h*.
>
> Del mismo modo, debe incluir *atlimage. h* antes de incluir *atlimpl. cpp*. Para lograr esto fácilmente, incluya *atlimage. h* en *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlimage. h

## <a name="cimagealphablend"></a><a name="alphablend"></a>CImage:: AlphaBlend

Muestra los mapas de bits que tienen píxeles transparentes o semitransparentes.

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
Valor de transparencia alfa que se va a usar en todo el mapa de bits de origen. El valor predeterminado 0xFF (255) supone que la imagen es opaca y que solo quiere usar valores alfa por píxel.

*bBlendOp*<br/>
Función de combinación alfa para los mapas de bits de origen y de destino, un valor alfa global que se va a aplicar al mapa de bits de origen completo e información de formato para el mapa de bits de origen. Las funciones de mezcla de origen y de destino están limitadas actualmente a AC_SRC_OVER.

*pointDest*<br/>
Referencia a una estructura de [punto](/windows/win32/api/windef/ns-windef-point) que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.

*nDestWidth*<br/>
Ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
Alto, en unidades lógicas, del rectángulo de destino.

*xSrc*<br/>
Coordenada x lógica de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
Coordenada y lógica de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
Ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
Alto, en unidades lógicas, del rectángulo de origen.

*rectDest*<br/>
Referencia a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) , que identifica el destino.

*rectSrc*<br/>
Referencia a una `RECT` estructura, que identifica el origen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Los mapas de bits de Alpha-Blend admiten la combinación de colores por píxel.

Cuando *bBlendOp* se establece en el valor predeterminado de AC_SRC_OVER, el mapa de bits de origen se coloca sobre el mapa de bits de destino en función de los valores alfa de los píxeles de origen.

## <a name="cimageattach"></a><a name="attach"></a>CImage:: Attach

Adjunta *hBitmap* a un `CImage` objeto.

```cpp
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
Identificador de un HBITMAP.

*eOrientation*<br/>
Especifica la orientación del mapa de bits. Puede ser uno de los siguientes:

- DIBOR_DEFAULT la orientación del mapa de bits viene determinada por el sistema operativo.

- DIBOR_BOTTOMUP las líneas del mapa de bits están en orden inverso. Esto hace que [CImage:: GetBits](#getbits) devuelva un puntero cerca del final del búfer de mapa de bits y [CImage:: GetPitch](#getpitch) para devolver un número negativo.

- DIBOR_TOPDOWN las líneas del mapa de bits están en orden descendente. Esto hace que [CImage:: GetBits](#getbits) devuelva un puntero al primer byte del búfer de mapa de bits y [CImage:: GetPitch](#getpitch) para devolver un número positivo.

### <a name="remarks"></a>Observaciones

El mapa de bits puede ser un mapa de bits de sección no DIB o un mapa de bits de sección DIB. Consulte [IsDIBSection](#isdibsection) para obtener una lista de los métodos que solo se pueden usar con los mapas de bits de la sección Dib.

## <a name="cimagebitblt"></a><a name="bitblt"></a>CImage:: BitBlt

Copia un mapa de bits desde el contexto de dispositivo de origen a este contexto de dispositivo actual.

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
Operación de trama que se va a realizar. Los códigos de operación de trama definen exactamente cómo combinar los bits del origen, el destino y el patrón (tal y como se define en el pincel seleccionado actualmente) para formar el destino. Consulte [bitblt](/windows/win32/api/wingdi/nf-wingdi-bitblt) en el Windows SDK para obtener una lista de otros códigos de operación de trama y sus descripciones.

*pointDest*<br/>
Una estructura de [punto](/windows/win32/api/windef/ns-windef-point) que indica la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
Ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
Alto, en unidades lógicas, del rectángulo de destino.

*xSrc*<br/>
Coordenada x lógica de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
Coordenada y lógica de la esquina superior izquierda del rectángulo de origen.

*rectDest*<br/>
Estructura [Rect](/windows/win32/api/windef/ns-windef-rect) que indica el rectángulo de destino.

*pointSrc*<br/>
`POINT` Estructura que indica la esquina superior izquierda del rectángulo de origen.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [bitblt](/windows/win32/api/wingdi/nf-wingdi-bitblt) en el Windows SDK.

## <a name="cimagecimage"></a><a name="cimage"></a>CImage:: CImage

Construye un objeto `CImage`.

```
CImage() throw();
```

### <a name="remarks"></a>Observaciones

Una vez que haya construido el objeto, llame a [Create](#create), [Load](#load), [LoadFromResource](#loadfromresource)o [Attach](#attach) para adjuntar un mapa de bits al objeto.

**Nota:** En Visual Studio, esta clase mantiene un recuento del número de `CImage` objetos creados. Siempre que el recuento llega a 0, `GdiplusShutdown` se llama automáticamente a la función para liberar los recursos utilizados por GDI+. Esto garantiza que los `CImage` objetos creados directa o indirectamente mediante archivos DLL se destruyen siempre `GdiplusShutdown` correctamente y que no se llama desde DllMain.

No se `CImage` recomienda el uso de objetos globales en un archivo dll. Si necesita usar un objeto global `CImage` en un archivo dll, llame a [CImage:: ReleaseGDIPlus](#releasegdiplus) para liberar explícitamente los recursos utilizados por GDI+.

## <a name="cimagecreate"></a><a name="create"></a>CImage:: Create

Crea un `CImage` mapa de bits y lo adjunta al objeto `CImage` construido previamente.

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parámetros

*nWidth*<br/>
Ancho del `CImage` mapa de bits, en píxeles.

*nHeight*<br/>
Alto del `CImage` mapa de bits, en píxeles. Si *nHeight* es positivo, el mapa de bits es un DIB de nivel inferior y su origen es la esquina inferior izquierda. Si *nHeight* es negativo, el mapa de bits es un DIB de arriba abajo y su origen es la esquina superior izquierda.

*nBPP*<br/>
Números de bits por píxel del mapa de bits. Normalmente 4, 8, 16, 24 o 32. Puede ser 1 para los mapas de bits o las máscaras monocromáticos.

*dwFlags*<br/>
Especifica si el objeto de mapa de bits tiene un canal alfa. Puede ser una combinación de cero o más de los valores siguientes:

- *createAlphaChannel* Solo se puede usar si *nBPP* es 32 y *eCompression* es BI_RGB. Si se especifica, la imagen creada tiene un valor alfa (transparencia) para cada píxel, almacenado en el cuarto byte de cada píxel (sin usar en una imagen no alfa de 32 bits). Este canal alfa se usa automáticamente cuando se llama a [CImage:: AlphaBlend](#alphablend).

> [!NOTE]
> En las llamadas a [CImage::D RAW](#draw), las imágenes con un canal alfa se combinan automáticamente en el destino.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="cimagecreateex"></a><a name="createex"></a>CImage:: CreateEx

Crea un `CImage` mapa de bits y lo adjunta al objeto `CImage` construido previamente.

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
Ancho del `CImage` mapa de bits, en píxeles.

*nHeight*<br/>
Alto del `CImage` mapa de bits, en píxeles. Si *nHeight* es positivo, el mapa de bits es un DIB de nivel inferior y su origen es la esquina inferior izquierda. Si *nHeight* es negativo, el mapa de bits es un DIB de arriba abajo y su origen es la esquina superior izquierda.

*nBPP*<br/>
Números de bits por píxel del mapa de bits. Normalmente 4, 8, 16, 24 o 32. Puede ser 1 para los mapas de bits o las máscaras monocromáticos.

*eCompression*<br/>
Especifica el tipo de compresión de un mapa de bits comprimido de arriba abajo (no se pueden comprimir los DIB de arriba abajo). Puede ser uno de los siguientes valores:

- BI_RGB se descomprime el formato. Especificar este valor cuando se llama `CImage::CreateEx` a es equivalente a `CImage::Create`llamar a.

- BI_BITFIELDS se descomprime el formato y la tabla de colores consta de tres máscaras de color DWORD que especifican los componentes rojo, verde y azul, respectivamente, de cada píxel. Esto es válido cuando se usa con mapas de bits de 16 y 32-bpp.

*pdwBitfields*<br/>
Solo se usa si *eCompression* se establece en BI_BITFIELDS; de lo contrario, debe ser null. Puntero a una matriz de tres máscaras de bits DWORD, que especifican los bits de cada píxel que se usan para los componentes rojo, verde y azul del color, respectivamente. Para obtener información sobre las restricciones de los campos de campos, vea [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) en el Windows SDK.

*dwFlags*<br/>
Especifica si el objeto de mapa de bits tiene un canal alfa. Puede ser una combinación de cero o más de los valores siguientes:

- *createAlphaChannel* Solo se puede usar si *nBPP* es 32 y *eCompression* es BI_RGB. Si se especifica, la imagen creada tiene un valor alfa (transparencia) para cada píxel, almacenado en el cuarto byte de cada píxel (sin usar en una imagen no alfa de 32 bits). Este canal alfa se usa automáticamente cuando se llama a [CImage:: AlphaBlend](#alphablend).

   > [!NOTE]
   > En las llamadas a [CImage::D RAW](#draw), las imágenes con un canal alfa se combinan automáticamente en el destino.

### <a name="return-value"></a>Valor devuelto

TRUE si se realiza correctamente. En caso contrario, FALSE.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un mapa de bits de 100x100 píxeles, con 16 bits para codificar cada píxel. En un píxel de 16 bits determinado, bits 0-3 codifica el componente rojo, bits 4-7 codificados en verde y bits 8-11 codificados en azul. Los 4 bits restantes no se usan.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a>CImage::D estroy

Desasocia el mapa de bits `CImage` del objeto y destruye el mapa de bits.

```cpp
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a>CImage::D Etach

Desasocia un mapa de bits `CImage` de un objeto.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Identificador del mapa de bits desasociado, o NULL si no hay ningún mapa de bits asociado.

## <a name="cimagedraw"></a><a name="draw"></a>CImage::D RAW

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
Identificador del contexto de dispositivo de destino.

*xDest*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
Ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
Alto, en unidades lógicas, del rectángulo de destino.

*xSrc*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
Ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
Alto, en unidades lógicas, del rectángulo de origen.

*rectDest*<br/>
Referencia a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) , que identifica el destino.

*rectSrc*<br/>
Referencia a una `RECT` estructura, que identifica el origen.

*pointDest*<br/>
Referencia a una estructura de [punto](/windows/win32/api/windef/ns-windef-point) que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

`Draw`realiza la misma operación que [StretchBlt](#stretchblt), a menos que la imagen contenga un color transparente o un canal alfa. En ese caso, `Draw` realiza la misma operación que [TransparentBlt](#transparentblt) o [AlphaBlend](#alphablend) , según sea necesario.

En el caso `Draw` de las versiones de que no especifican un rectángulo de origen, la imagen de origen completa es el valor predeterminado. Para la versión de `Draw` que no especifica un tamaño para el rectángulo de destino, el tamaño de la imagen de origen es el valor predeterminado y no se produce la ampliación o la reducción.

## <a name="cimagegetbits"></a><a name="getbits"></a>CImage:: GetBits

Recupera un puntero a los valores de bit reales de un píxel determinado en un mapa de bits.

```cpp
void* GetBits() throw();
```

### <a name="return-value"></a>Valor devuelto

Puntero al búfer de mapa de bits. Si el mapa de bits es un DIB de arriba abajo, el puntero apunta cerca del final del búfer. Si el mapa de bits es un DIB de arriba abajo, el puntero apunta al primer byte del búfer.

### <a name="remarks"></a>Observaciones

Con este puntero, junto con el valor devuelto por [GetPitch](#getpitch), puede buscar y cambiar píxeles individuales en una imagen.

> [!NOTE]
> Este método solo admite los mapas de bits de la sección DIB; por consiguiente, el acceso a los píxeles de `CImage` un objeto se realiza de la misma forma que lo haría con los píxeles de una sección Dib. El puntero devuelto apunta al píxel en la ubicación (0,0).

## <a name="cimagegetbpp"></a><a name="getbpp"></a>CImage:: GetBPP

Recupera el valor de bits por píxel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Valor devuelto

Número de bits por píxel.

### <a name="remarks"></a>Observaciones

Este valor determina el número de bits que definen cada píxel y el número máximo de colores del mapa de bits.

Los bits por píxel suelen ser 1, 4, 8, 16, 24 o 32. Vea el `biBitCount` miembro de [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) en el Windows SDK para obtener más información sobre este valor.

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a>CImage:: GetColorTable

Recupera los valores de color rojo, verde y azul (RGB) de un intervalo de entradas de la paleta de la sección DIB.

```cpp
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parámetros

*iFirstColor*<br/>
Índice de la primera entrada que se va a recuperar.

*nColors*<br/>
Número de entradas de la tabla de colores que se van a recuperar.

*prgbColors*<br/>
Puntero a la matriz de estructuras [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) para recuperar las entradas de la tabla de colores.

## <a name="cimagegetdc"></a><a name="getdc"></a>CImage:: GetDC

Recupera el contexto de dispositivo que actualmente tiene la imagen seleccionada.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Valor devuelto

Identificador de un contexto de dispositivo.

### <a name="remarks"></a>Observaciones

Para cada llamada a `GetDC`, debe tener una llamada subsiguiente a [ReleaseDC](#releasedc).

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a>CImage:: GetExporterFilterString

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

*strExporters*<br/>
Referencia a un objeto `CSimpleString`. Vea la **sección Comentarios** para obtener más información.

*aguidFileTypes*<br/>
Matriz de GUID, donde cada elemento corresponde a uno de los tipos de archivo de la cadena. En el ejemplo de *pszAllFilesDescription* siguiente, se GUID_NULL *aguidFileTypes*[0] y los valores de la matriz restantes son los formatos de archivo de imagen admitidos por el sistema operativo actual.

> [!NOTE]
> Para obtener una lista completa de constantes, consulte **constantes de formato de archivo de imagen** en el Windows SDK.

*pszAllFilesDescription*<br/>
Si este parámetro no es NULL, la cadena de filtro tendrá un filtro adicional al principio de la lista. Este filtro tendrá el valor actual de *pszAllFilesDescription* para su descripción y aceptará archivos de cualquier extensión admitida por cualquier otro exportador de la lista.

Por ejemplo:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Conjunto de marcas de bits que especifican los tipos de archivo que se van a excluir de la lista. Las marcas permitidas son:

- `excludeGIF`= 0x01 excluye los archivos GIF.

- `excludeBMP`= 0x02 excluye los archivos BMP (mapa de bits de Windows).

- `excludeEMF`= 0x04 excluye los archivos EMF (metarchivo mejorado).

- `excludeWMF`= 0x08 excluye los archivos WMF (metarchivo de Windows).

- `excludeJPEG`= 0x10 excluye los archivos JPEG.

- `excludePNG`= 0x20 excluye los archivos PNG.

- `excludeTIFF`= 0x40 excluye los archivos TIFF.

- `excludeIcon`= 0x80 excluye los archivos ICO (icono de Windows).

- `excludeOther`= 0x80000000 excluye cualquier otro tipo de archivo que no aparezca en la lista anterior.

- `excludeDefaultLoad`= 0 para la carga, todos los tipos de archivo se incluyen de forma predeterminada

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Para guardar, estos archivos se excluyen de forma predeterminada porque suelen tener requisitos especiales.

*chSeparator*<br/>
El separador utilizado entre los formatos de imagen. Vea la **sección Comentarios** para obtener más información.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Puede pasar la cadena de formato resultante al objeto [CFileDialog](../../mfc/reference/cfiledialog-class.md) de MFC para exponer las extensiones de archivo de los formatos de imagen disponibles en el cuadro de diálogo Guardar como archivo.

El parámetro *strExporter* tiene el formato:

archivo description0&#124;\*. ext0&#124;filedescription1&#124;\*.&#124; EXT1... Descripción del *n* archivo n \*&#124;. ext *n*&#124;&#124;

donde ' &#124; ' es el carácter separador especificado `chSeparator`por. Por ejemplo:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Use el separador predeterminado ' &#124; ' si pasa esta cadena a un objeto `CFileDialog` MFC. Use el separador nulo ' \ 0 ' si pasa esta cadena a un cuadro de diálogo Guardar archivo común.

## <a name="cimagegetheight"></a><a name="getheight"></a>CImage:: GetHeight

Recupera el alto, en píxeles, de una imagen.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Valor devuelto

Alto, en píxeles, de una imagen.

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a>CImage:: GetImporterFilterString

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
Referencia a un objeto `CSimpleString`. Vea la **sección Comentarios** para obtener más información.

*aguidFileTypes*<br/>
Matriz de GUID, donde cada elemento corresponde a uno de los tipos de archivo de la cadena. En el ejemplo de *pszAllFilesDescription* a continuación, *aguidFileTypes*[0] se GUID_NULL con los valores de la matriz restantes son los formatos de archivo de imagen admitidos por el sistema operativo actual.

> [!NOTE]
> Para obtener una lista completa de constantes, consulte **constantes de formato de archivo de imagen** en el Windows SDK.

*pszAllFilesDescription*<br/>
Si este parámetro no es NULL, la cadena de filtro tendrá un filtro adicional al principio de la lista. Este filtro tendrá el valor actual de *pszAllFilesDescription* para su descripción y aceptará archivos de cualquier extensión admitida por cualquier otro exportador de la lista.

Por ejemplo:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Conjunto de marcas de bits que especifican los tipos de archivo que se van a excluir de la lista. Las marcas permitidas son:

- `excludeGIF`= 0x01 excluye los archivos GIF.

- `excludeBMP`= 0x02 excluye los archivos BMP (mapa de bits de Windows).

- `excludeEMF`= 0x04 excluye los archivos EMF (metarchivo mejorado).

- `excludeWMF`= 0x08 excluye los archivos WMF (metarchivo de Windows).

- `excludeJPEG`= 0x10 excluye los archivos JPEG.

- `excludePNG`= 0x20 excluye los archivos PNG.

- `excludeTIFF`= 0x40 excluye los archivos TIFF.

- `excludeIcon`= 0x80 excluye los archivos ICO (icono de Windows).

- `excludeOther`= 0x80000000 excluye cualquier otro tipo de archivo que no aparezca en la lista anterior.

- `excludeDefaultLoad`= 0 para la carga, todos los tipos de archivo se incluyen de forma predeterminada

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Para guardar, estos archivos se excluyen de forma predeterminada porque suelen tener requisitos especiales.

*chSeparator*<br/>
El separador utilizado entre los formatos de imagen. Vea la **sección Comentarios** para obtener más información.

### <a name="remarks"></a>Observaciones

Puede pasar la cadena de formato resultante al objeto [CFileDialog](../../mfc/reference/cfiledialog-class.md) de MFC para exponer las extensiones de archivo de los formatos de imagen disponibles en el cuadro de diálogo **Abrir archivo** .

El parámetro *strImporter* tiene el formato:

archivo description0&#124;\*. ext0&#124;filedescription1&#124;\*.&#124; EXT1... Descripción del *n* archivo n \*&#124;. ext *n*&#124;&#124;

donde ' &#124; ' es el carácter separador especificado por *chSeparator*. Por ejemplo:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Use el separador predeterminado ' &#124; ' si pasa esta cadena a un objeto `CFileDialog` MFC. Use el separador nulo "\ 0" Si pasa esta cadena a un cuadro de diálogo **Abrir archivo** común.

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a>CImage:: GetMaxColorTableEntries

Recupera el número máximo de entradas de la tabla de colores.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Valor devuelto

Número de entradas de la tabla de colores.

### <a name="remarks"></a>Observaciones

Este método solo admite los mapas de bits de la sección DIB.

## <a name="cimagegetpitch"></a><a name="getpitch"></a>CImage:: GetPitch

Recupera el tono de una imagen.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Valor devuelto

El tono de la imagen. Si el valor devuelto es negativo, el mapa de bits es un DIB de nivel inferior y su origen es la esquina inferior izquierda. Si el valor devuelto es positivo, el mapa de bits es un DIB de arriba abajo y su origen es la esquina superior izquierda.

### <a name="remarks"></a>Observaciones

El paso es la distancia, en bytes, entre dos direcciones de memoria que representan el principio de una línea de mapa de bits y el principio de la siguiente línea de mapa de bits. Dado que el paso se mide en bytes, el paso de una imagen le ayuda a determinar el formato de píxel. El paso también puede incluir memoria adicional, reservada para el mapa de bits.

Use `GetPitch` with [GetBits](#getbits) para buscar píxeles individuales de una imagen.

> [!NOTE]
> Este método solo admite los mapas de bits de la sección DIB.

## <a name="cimagegetpixel"></a><a name="getpixel"></a>CImage:: GetPixel

Recupera el color del píxel en la ubicación especificada por *x* *e y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Coordenada x del píxel.

*sí*<br/>
Coordenada y del píxel.

### <a name="return-value"></a>Valor devuelto

Valor rojo, verde y azul (RGB) del píxel. Si el píxel está fuera de la región de recorte actual, el valor devuelto es CLR_INVALID.

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a>CImage:: GetPixelAddress

Recupera la dirección exacta de un píxel.

```cpp
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Coordenada x del píxel.

*sí*<br/>
Coordenada y del píxel.

### <a name="remarks"></a>Observaciones

La dirección se determina según las coordenadas de un píxel, el tono y los bits por píxel.

En el caso de los formatos que tienen menos de 8 bits por píxel, este método devuelve la dirección del byte que contiene el píxel. Por ejemplo, si el formato de imagen tiene 4 bits por píxel `GetPixelAddress` , devuelve la dirección del primer píxel del byte y debe calcular 2 píxeles por byte.

> [!NOTE]
> Este método solo admite los mapas de bits de la sección DIB.

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a>CImage:: GetTransparentColor

Recupera la ubicación indizada del color transparente en la paleta de colores.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Valor devuelto

Índice del color transparente.

## <a name="cimagegetwidth"></a><a name="getwidth"></a>CImage:: GetWidth

Recupera el ancho, en píxeles, de una imagen.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Valor devuelto

Ancho del mapa de bits, en píxeles.

## <a name="cimageisdibsection"></a><a name="isdibsection"></a>CImage:: IsDIBSection

Determina si el mapa de bits adjunto es una sección DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el mapa de bits adjunto es una sección DIB. En caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el mapa de bits no es una sección DIB, no puede usar `CImage` los métodos siguientes, que solo admiten mapas de bits de la sección DIB:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a>CImage:: IsIndexed

Determina si los píxeles de un mapa de bits están asignados a una paleta de colores.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Valor devuelto

TRUE si se indiza; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método devuelve TRUE solo si el mapa de bits es de 8 bits (256 colores) o menos.

> [!NOTE]
> Este método solo admite los mapas de bits de la sección DIB.

## <a name="cimageisnull"></a><a name="isnull"></a>CImage:: IsNull

Determina si un mapa de bits está cargado actualmente.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Observaciones

Este método devuelve TRUE si no se ha cargado un mapa de bits actualmente; en caso contrario, FALSE.

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a>CImage:: IsTransparencySupported

Indica si la aplicación admite mapas de bits transparentes.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la plataforma actual admite transparencia. De lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Si el valor devuelto es distinto de cero y se admite la transparencia, una llamada a [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt)o [Draw](#draw) controlará los colores transparentes.

## <a name="cimageload"></a><a name="load"></a>CImage:: Load

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

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Carga la imagen especificada por *pszFileName* o *pStream*.

Los tipos de imagen válidos son BMP, GIF, JPEG, PNG y TIFF.

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a>CImage:: LoadFromResource

Carga una imagen desde un recurso de mapa de bits.

```cpp
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
Un puntero a la cadena que contiene el nombre del recurso que contiene la imagen que se va a cargar.

*nIDResource*<br/>
Id. del recurso que se va a cargar.

### <a name="remarks"></a>Observaciones

El recurso debe ser de tipo BITMAP.

## <a name="cimagemaskblt"></a><a name="maskblt"></a>CImage:: MaskBlt

Combina los datos de color de los mapas de bits de origen y de destino usando la máscara y la operación de trama especificadas.

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
Identificador del módulo cuyo ejecutable contiene el recurso.

*xDest*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*yDest*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.

*nDestWidth*<br/>
Ancho, en unidades lógicas, del rectángulo de destino y el mapa de bits de origen.

*nDestHeight*<br/>
Alto, en unidades lógicas, del rectángulo de destino y el mapa de bits de origen.

*xSrc*<br/>
Coordenada x lógica de la esquina superior izquierda del mapa de bits de origen.

*ySrc*<br/>
Coordenada y lógica de la esquina superior izquierda del mapa de bits de origen.

*hbmMask*<br/>
Identificador del mapa de bits de máscara monocromática combinado con el mapa de bits de color en el contexto del dispositivo de origen.

*xMask*<br/>
Desplazamiento de píxeles horizontal para el mapa de bits de la máscara especificado por el parámetro *hbmMask* .

*yMask*<br/>
Desplazamiento de píxeles vertical para el mapa de bits de la máscara especificado por el parámetro *hbmMask* .

*dwROP*<br/>
Especifica los códigos de operación de trama ternaria de primer y segundo plano que utiliza el método para controlar la combinación de datos de origen y de destino. El código de operación de trama de fondo se almacena en el byte de orden superior de la palabra de orden superior de este valor; el código de operación de trama de primer plano se almacena en el byte de orden inferior de la palabra de orden superior de este valor; la palabra de orden inferior de este valor se omite y debe ser cero. Para obtener una explicación sobre el primer plano y el fondo en el contexto de `MaskBlt` este método, vea en el Windows SDK. Para obtener una lista de códigos de operación de trama `BitBlt` comunes, vea en el Windows SDK.

*rectDest*<br/>
Referencia a una `RECT` estructura, que identifica el destino.

*pointSrc*<br/>
`POINT` Estructura que indica la esquina superior izquierda del rectángulo de origen.

*pointMask*<br/>
`POINT` Estructura que indica la esquina superior izquierda del mapa de bits de la máscara.

*pointDest*<br/>
Referencia a una `POINT` estructura que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Este método solo se aplica a las versiones 4,0 y posteriores de Windows NT.

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a>CImage:: Operator HBITMAP

Utilice este operador para obtener el identificador de GDI de Windows asociado `CImage` del objeto. Este operador es un operador de conversión, que admite el uso directo de un objeto HBITMAP.

## <a name="cimageplgblt"></a><a name="plgblt"></a>CImage::P lgBlt

Realiza una transferencia de bloque de bits de un rectángulo en un contexto de dispositivo de origen a un paralelogramo en un contexto de dispositivo de destino.

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
Puntero a una matriz de tres puntos en el espacio lógico que identifica tres esquinas del paralelogramo de destino. La esquina superior izquierda del rectángulo de origen se asigna al primer punto de esta matriz, la esquina superior derecha al segundo punto de esta matriz y la esquina inferior izquierda al tercer punto. La esquina inferior derecha del rectángulo de origen se asigna al cuarto punto implícito del paralelogramo.

*hbmMask*<br/>
Identificador de un mapa de bits monocromo opcional que se usa para enmascarar los colores del rectángulo de origen.

*xSrc*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
Ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
Alto, en unidades lógicas, del rectángulo de origen.

*xMask*<br/>
Coordenada x de la esquina superior izquierda del mapa de bits monocromo.

*yMask*<br/>
Coordenada y de la esquina superior izquierda del mapa de bits monocromo.

*rectSrc*<br/>
Referencia a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) que especifica las coordenadas del rectángulo de origen.

*pointMask*<br/>
Una estructura de [punto](/windows/win32/api/windef/ns-windef-point) que indica la esquina superior izquierda del mapa de bits de la máscara.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Si *hbmMask* identifica un mapa de bits monocromo `PlgBit` válido, utiliza este mapa de bits para enmascarar los bits de los datos de color del rectángulo de origen.

Este método solo se aplica a las versiones 4,0 y posteriores de Windows NT. Consulte [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) en el Windows SDK para obtener información más detallada.

## <a name="cimagereleasedc"></a><a name="releasedc"></a>CImage:: ReleaseDC

Libera el contexto del dispositivo.

```cpp
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Observaciones

Dado que solo se puede seleccionar un mapa de bits en un contexto de dispositivo cada vez, `ReleaseDC` debe llamar a para cada llamada a [GetDC](#getdc).

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a>CImage:: ReleaseGDIPlus

Libera los recursos que usa GDI+.

```cpp
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Observaciones

Se debe llamar a este método para liberar los recursos asignados `CImage` por un objeto global. Vea [CImage:: CImage](#cimage).

## <a name="cimagesave"></a><a name="save"></a>CImage:: Save

Guarda una imagen en la secuencia o el archivo especificados en el disco.

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
Un puntero a un objeto IStream COM que contiene los datos de la imagen de archivo.

*pszFileName*<br/>
Puntero al nombre de archivo de la imagen.

*guidFileType*<br/>
Tipo de archivo en el que se guardará la imagen. Puede ser uno de los siguientes:

- `ImageFormatBMP`Imagen de mapa de bits sin comprimir.

- `ImageFormatPNG`Imagen comprimida PNG (Portable Network Graphics).

- `ImageFormatJPEG`Imagen comprimida JPEG.

- `ImageFormatGIF`Imagen comprimida GIF.

> [!NOTE]
> Para obtener una lista completa de constantes, consulte **constantes de formato de archivo de imagen** en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Llame a esta función para guardar la imagen con un nombre y tipo especificados. Si no se incluye el parámetro *guidFileType* , se utilizará la extensión de archivo del nombre de archivo para determinar el formato de la imagen. Si no se proporciona ninguna extensión, la imagen se guardará en formato BMP.

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a>CImage:: SetColorTable

Establece los valores de color rojo, verde y azul (RGB) de un intervalo de entradas en la paleta de la sección DIB.

```cpp
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parámetros

*iFirstColor*<br/>
Índice de la tabla de colores de la primera entrada que se va a establecer.

*nColors*<br/>
Número de entradas de la tabla de colores que se van a establecer.

*prgbColors*<br/>
Puntero a la matriz de estructuras [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) para establecer las entradas de la tabla de colores.

### <a name="remarks"></a>Observaciones

Este método solo admite los mapas de bits de la sección DIB.

## <a name="cimagesetpixel"></a><a name="setpixel"></a>CImage:: SetPixel

Establece el color de un píxel en una ubicación determinada del mapa de bits.

```cpp
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Ubicación horizontal del píxel que se va a establecer.

*sí*<br/>
Ubicación vertical del píxel que se va a establecer.

*color*<br/>
Color en el que se establece el píxel.

### <a name="remarks"></a>Observaciones

Este método produce un error si las coordenadas de píxeles se encuentran fuera de la región de recorte seleccionada.

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a>CImage:: SetPixelIndexed

Establece el color de píxel en el color que se encuentra en *iIndex* en la paleta de colores.

```cpp
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Ubicación horizontal del píxel que se va a establecer.

*sí*<br/>
Ubicación vertical del píxel que se va a establecer.

*iIndex*<br/>
Índice de un color de la paleta de colores.

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a>CImage:: SetPixelRGB

Establece el *píxel en las* ubicaciones especificadas por *x* e y con los colores indicados por *r*, *g*y *b*, en una imagen roja, verde, azul (RGB).

```cpp
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Ubicación horizontal del píxel que se va a establecer.

*sí*<br/>
Ubicación vertical del píxel que se va a establecer.

*r*<br/>
Intensidad del color rojo.

*i*<br/>
Intensidad del color verde.

*b*<br/>
Intensidad del color azul.

### <a name="remarks"></a>Observaciones

Los parámetros rojo, verde y azul se representan mediante un número comprendido entre 0 y 255. Si establece los tres parámetros en cero, el color resultante combinado es negro. Si establece los tres parámetros en 255, el color resultante combinado será blanco.

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a>CImage:: SetTransparentColor

Establece un color en una ubicación indizada determinada como transparente.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parámetros

*iTransparentColor*<br/>
Índice de la paleta de colores del color que se va a establecer en transparente. Si es-1, no se establece ningún color como transparente.

### <a name="return-value"></a>Valor devuelto

Índice del color establecido previamente como transparente.

## <a name="cimagestretchblt"></a><a name="stretchblt"></a>CImage:: StretchBlt

Copia un mapa de bits desde el contexto de dispositivo de origen a este contexto de dispositivo actual.

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
Ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
Alto, en unidades lógicas, del rectángulo de destino.

*dwROP*<br/>
Operación de trama que se va a realizar. Los códigos de operación de trama definen exactamente cómo combinar los bits del origen, el destino y el patrón (tal y como se define en el pincel seleccionado actualmente) para formar el destino. Consulte [bitblt](/windows/win32/api/wingdi/nf-wingdi-bitblt) en el Windows SDK para obtener una lista de otros códigos de operación de trama y sus descripciones.

*rectDest*<br/>
Referencia a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) , que identifica el destino.

*xSrc*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
Ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
Alto, en unidades lógicas, del rectángulo de origen.

*rectSrc*<br/>
Referencia a una `RECT` estructura, que identifica el origen.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) en el Windows SDK.

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a>CImage:: TransparentBlt

Copia un mapa de bits desde el contexto de dispositivo de origen a este contexto de dispositivo actual.

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
Ancho, en unidades lógicas, del rectángulo de destino.

*nDestHeight*<br/>
Alto, en unidades lógicas, del rectángulo de destino.

*crTransparent*<br/>
Color del mapa de bits de origen que se va a tratar como transparente. De forma predeterminada, CLR_INVALID, que indica que se debe usar el color establecido actualmente como color transparente de la imagen.

*rectDest*<br/>
Referencia a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) , que identifica el destino.

*xSrc*<br/>
La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*ySrc*<br/>
La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.

*nSrcWidth*<br/>
Ancho, en unidades lógicas, del rectángulo de origen.

*nSrcHeight*<br/>
Alto, en unidades lógicas, del rectángulo de origen.

*rectSrc*<br/>
Referencia a una `RECT` estructura, que identifica el origen.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

`TransparentBlt`es compatible con los mapas de bits de origen de 4 bits por píxel y 8 bits por píxel. Use [CImage:: AlphaBlend](#alphablend) para especificar mapas de bits de 32 bits por píxel con transparencia.

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

[Ejemplo de MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de SimpleImage](../../overview/visual-cpp-samples.md)<br/>
[Mapas de bits independientes del dispositivo](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)<br/>
[Mapas de bits independientes del dispositivo](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
