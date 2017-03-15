---
title: CImage (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CImage
- ATL.CImage
- ATL::CImage
dev_langs:
- C++
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
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: f74e5952401d6f9608425681cd91120b648e7b13
ms.lasthandoff: 02/24/2017

---
# <a name="cimage-class"></a>CImage (clase)
`CImage`proporciona compatibilidad de mapa de bits mejorada, incluida la capacidad para cargar y guardar imágenes en formato JPEG, GIF, BMP y gráficos de red portátiles (PNG).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
|[CImage::AlphaBlend](#alphablend)|Muestra los mapas de bits transparentes o semitransparentes píxeles.|  
|[CImage::Attach](#attach)|Asocia un `HBITMAP` a una `CImage` objeto. Puede utilizarse con mapas de bits de sección no DIB o mapas de bits DIB sección.|  
|[CImage::BitBlt](#bitblt)|Copia un mapa de bits desde el contexto de dispositivo de origen en el contexto del dispositivo actual.|  
|[CImage::Create](#create)|Crea un mapa de bits de sección DIB y lo adjunta a construido anteriormente `CImage` objeto.|  
|[CImage::CreateEx](#createex)|Crea un mapa de bits de sección DIB (con parámetros adicionales) y lo adjunta a construido anteriormente `CImage` objeto.|  
|[CImage::Destroy](#destroy)|Desasocia el mapa de bits de la `CImage` del objeto y se destruye el mapa de bits.|  
|[CImage::Detach](#detach)|Desasocia el mapa de bits desde un `CImage` objeto.|  
|[CImage::Draw](#draw)|Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino. **Dibujar** estira o comprime el mapa de bits para ajustarse a las dimensiones del rectángulo de destino, si es necesario y controla la mezcla alfa y colores transparentes.|  
|[CImage::GetBits](#getbits)|Recupera un puntero a los valores de píxeles reales del mapa de bits.|  
|[CImage::GetBPP](#getbpp)|Recupera los bits por píxel.|  
|[CImage::GetColorTable](#getcolortable)|Recupera los valores de color rojos, verdes, azul (RGB) de un intervalo de entradas en la tabla de colores.|  
|[CImage::GetDC](#getdc)|Recupera el contexto de dispositivo en el que está seleccionado el mapa de bits actual.|  
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Busca los formatos de imagen disponibles y sus descripciones.|  
|[CImage::GetHeight](#getheight)|Recupera el alto de la imagen actual en píxeles.|  
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Busca los formatos de imagen disponibles y sus descripciones.|  
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Recupera el número máximo de entradas en la tabla de colores.|  
|[CImage::GetPitch](#getpitch)|Recupera el tono de la imagen actual, en bytes.|  
|[CImage::GetPixel](#getpixel)|Recupera el color del píxel especificado por *x* y *y*.|  
|[CImage::GetPixelAddress](#getpixeladdress)|Recupera la dirección de un píxel determinado.|  
|[CImage::GetTransparentColor](#gettransparentcolor)|Recupera la posición del color transparente de la tabla de colores.|  
|[CImage::GetWidth](#getwidth)|Recupera el ancho de la imagen actual en píxeles.|  
|[CImage::IsDIBSection](#isdibsection)|Determina si el mapa de bits adjunto es una sección DIB.|  
|[CImage::IsIndexed](#isindexed)|Indica que los colores del mapa de bits se asignan a una paleta indizada.|  
|[CImage::IsNull](#isnull)|Indica si un mapa de bits de origen está cargado actualmente.|  
|[CImage:: IsTransparencySupported](#istransparencysupported)|Indica si la aplicación admite mapas de bits transparentes y se compiló para Windows 2000 o posterior.|  
|[CImage::Load](#load)|Carga una imagen desde el archivo especificado.|  
|[CImage::LoadFromResource](#loadfromresource)|Carga una imagen desde el recurso especificado.|  
|[CImage:: MaskBlt](#maskblt)|Combina los datos de color para los mapas de bits de origen y destino con la máscara especificada y la operación de trama.|  
|[CImage::PlgBlt](#plgblt)|Realiza a una transferencia de bloque de bits de un rectángulo en un contexto de dispositivo de origen en un paralelogramo en un contexto de dispositivo de destino.|  
|[CImage::ReleaseDC](#releasedc)|Libera el contexto de dispositivo que se ha recuperado con [CImage::GetDC](#getdc).|  
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Libera los recursos utilizados por GDI +. Se debe llamar para liberar recursos creados por global `CImage` objeto.|  
|[CImage::Save](#save)|Guarda una imagen como el tipo especificado. **Guardar** no se puede especificar opciones de imagen.|  
|[CImage::SetColorTable](#setcolortable)|Establece el valor RGB rojo, verde, azul) los valores de un intervalo de entradas en la tabla de colores de la sección DIB de color.|  
|[CImage::SetPixel](#setpixel)|Establece el píxel en las coordenadas especificadas para el color especificado.|  
|[CImage::SetPixelIndexed](#setpixelindexed)|Establece el píxel en las coordenadas especificadas en el color en el índice especificado de la paleta.|  
|[CImage::SetPixelRGB](#setpixelrgb)|Establece el píxel en las coordenadas especificadas en el valor de especificado de rojo, verde, azul (RGB).|  
|[CImage::SetTransparentColor](#settransparentcolor)|Establece el índice del color que se va a tratar como transparente. Sólo un color de una paleta puede ser transparente.|  
|[CImage::StretchBlt](#stretchblt)|Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino, estirando o comprimiendo el mapa de bits para ajustarse a las dimensiones del rectángulo de destino, si es necesario.|  
|[CImage:: TransparentBlt](#transparentblt)|Copia un mapa de bits con color transparente desde el contexto de dispositivo de origen en el contexto del dispositivo actual.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CImage::operator HBITMAP](#operator_hbitmap)|Devuelve el identificador de Windows asociado a la `CImage` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CImage`toma los mapas de bits en secciones de mapa de bits independiente del dispositivo (DIB) o no. Sin embargo, puede usar [crear](#create) o [CImage::Load](#load) con secciones DIB solo. Puede adjuntar un mapa de bits de sección no DIB a un `CImage` objeto mediante [adjuntar](#attach), pero, a continuación, puede utilizar la siguiente `CImage` métodos que admiten los mapas de sección DIB solo:  
  
- [GetBits](#getbits)  
  
- [GetColorTable](#getcolortable)  
  
- [GetMaxColorTableEntries](#getmaxcolortableentries)  
  
- [GetPitch](#getpitch)  
  
- [GetPixelAddress](#getpixeladdress)  
  
- [Isindexed como](#isindexed)  
  
- [SetColorTable](#setcolortable)  
  
 Para determinar si un mapa de bits adjunto es una sección DIB, llame a [IsDibSection](#isdibsection)**.**  
  
> [!NOTE]
> **Nota** en Visual Studio .NET 2003, esta clase mantiene un recuento del número de `CImage` objetos creados. Cuando el recuento llega a 0, la función **GdiplusShutdown** llama automáticamente para liberar los recursos utilizados por GDI +. Esto garantiza que cualquier `CImage` objetos creados directa o indirectamente por archivos DLL siempre se destruyen correctamente y que **GdiplusShutdown** no se llama desde `DllMain`.  
  
> [!NOTE]
>  Uso global `CImage` objetos en un archivo DLL no se recomienda. Si necesita usar un global `CImage` objeto en un archivo DLL, llamada [CImage::ReleaseGDIPlus](#releasegdiplus) para liberar explícitamente los recursos utilizados por GDI +.  
  
 `CImage`no se pueden seleccionar en un nuevo [CDC](../../mfc/reference/cdc-class.md). `CImage`crea su propio **HDC** para la imagen. Porque un `HBITMAP` sólo se puede seleccionar en una **HDC** a la vez, el `HBITMAP` asociados con el `CImage` no se pueden seleccionar en otro **HDC**. Si necesita un `CDC`, recuperar el **HDC** desde el `CImage` y darle a [CDC::FromHandle] (.. /.. /MFC/Reference/CDC-Class.MD#cdc__fromhandle.  
  
## <a name="example"></a>Ejemplo  
```cpp  
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```  
  
 Al usar `CImage` en un proyecto MFC, tenga en cuenta qué funciones de miembro en el proyecto esperan un puntero a un [CBitmap](../../mfc/reference/cbitmap-class.md) objeto. Si desea usar `CImage` con dicha función, como [CMenu:: AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), utilice [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), pasa su `CImage` `HBITMAP`y utilizar el valor devuelto `CBitmap*`.  

  
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

  
 A través de `CImage`, tendrá acceso a los bits reales de una sección DIB. Puede usar un `CImage` en cualquier parte del objeto que utilizó anteriormente una sección HBITMAP Win32 o DIB.  
  
> [!NOTE]
>  La siguiente `CImage` métodos tienen limitaciones sobre su uso:  
  
|Método|Limitación|  
|------------|----------------|  
|[PlgBlt](#plgblt)|Funciona con sólo Windows NT 4.0 o posterior. No funcionará en aplicaciones que se ejecutan en Windows 95 ó 98 o posterior.|  
|[MaskBlt](#maskblt)|Funciona con sólo Windows NT 4.0 o posterior. No funcionará en aplicaciones que se ejecutan en Windows 95 ó 98 o posterior.|  
|[AlphaBlend](#alphablend)|Funciona con sólo Windows 2000, Windows 98 y sistemas posteriores.|  
|[TransparentBlt](#transparentblt)|Funciona con sólo Windows 2000, Windows 98 y sistemas posteriores.|  
|[Dibujar](#draw)|Admite la transparencia con sólo Windows 2000, Windows 98 y sistemas posteriores.|  
  
 Puede utilizar `CImage` de MFC o ATL.  
  
> [!NOTE]
>  Cuando se crea un proyecto con `CImage`, debe definir `CString` antes de incluir `atlimage.h`. Si el proyecto usa ATL sin MFC, incluir `atlstr.h` antes de incluir `atlimage.h`. Si el proyecto utiliza MFC (o si se trata de un proyecto ATL compatible con MFC), incluya `afxstr.h` antes de incluir `atlimage.h`.  
>   
>  Igualmente, debe incluir `atlimage.h` antes de incluir `atlimpl.cpp`. Para lograr esto fácilmente, incluyen `atlimage.h` en su `stdafx.h`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlimage.h  
  
##  <a name="a-namealphablenda--cimagealphablend"></a><a name="alphablend"></a>CImage::AlphaBlend  
 Muestra los mapas de bits transparentes o semitransparentes píxeles.  
  
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
 `hDestDC`  
 Identificador del contexto de dispositivo de destino.  
  
 `xDest`  
 La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `yDest`  
 La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 *bSrcAlpha*  
 Un valor de transparencia alfa que se utilizará en el mapa de bits de origen completa. 0xff (255), se supone que la imagen es opaca y que desea usar valores alfa de por píxel.  
  
 `bBlendOp`  
 La función de combinación alfa de origen y los mapas de bits de destino, un valor alfa global que se aplicará a la información de formato del mapa de bits de origen y el mapa de bits de origen completa. Las funciones de mezcla de origen y destino están limitadas actualmente a **AC_SRC_OVER**.  
  
 `pointDest`  
 Una referencia a un [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) estructura que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.  
  
 `nDestWidth`  
 El ancho, en unidades lógicas, del rectángulo de destino.  
  
 `nDestHeight`  
 Alto, en unidades lógicas, del rectángulo de destino.  
  
 `xSrc`  
 Coordenada x lógica de la esquina superior izquierda del rectángulo de origen.  
  
 `ySrc`  
 Coordenada y lógica de la esquina superior izquierda del rectángulo de origen.  
  
 `nSrcWidth`  
 El ancho, en unidades lógicas, del rectángulo de origen.  
  
 `nSrcHeight`  
 Alto, en unidades lógicas, del rectángulo de origen.  
  
 `rectDest`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura, que identifica el destino.  
  
 `rectSrc`  
 Una referencia a un `RECT` estructura, que identifica el origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Los mapas de bits de la mezcla alfa admiten la mezcla de color por píxel.  
  
 Cuando `bBlendOp` se establece en el valor predeterminado de **AC_SRC_OVER**, el mapa de bits de origen se coloca sobre el mapa de bits de destino basándose en los valores alfabéticos de los píxeles de origen.  

##  <a name="a-nameattacha--cimageattach"></a><a name="attach"></a>CImage::Attach  
 Adjunta `hBitmap` a una `CImage` objeto.  
  
```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hBitmap`  
 Un identificador de un `HBITMAP`.  
  
 *eOrientation*  
 Especifica la orientación del mapa de bits. Puede ser uno de los siguientes:  
  
- **DIBOR_DEFAULT** la orientación del mapa de bits viene determinada por el sistema operativo. Sin embargo, esto no siempre tenga los resultados previstos en todos los sistemas operativos. Para obtener más información, consulte el siguiente artículo de Knowledge Base ( **Q186586**): PRB: GetObject() siempre devuelve positivo alto de DIB secciones.  
  
- **DIBOR_BOTTOMUP** las líneas del mapa de bits están en orden inverso. Esto hace que [CImage::GetBits](#getbits) para devolver un puntero cerca del final del búfer de mapa de bits y [CImage::GetPitch](#getpitch) para devolver un número negativo.  
  
- **DIBOR_TOPDOWN** las líneas del mapa de bits están en orden descendente. Esto hace que [CImage::GetBits](#getbits) para devolver un puntero al primer byte del búfer de mapa de bits y [CImage::GetPitch](#getpitch) para devolver un número positivo.  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits puede ser un mapa de bits de la sección no DIB o un mapa de bits de la sección DIB. Consulte [IsDIBSection](#isdibsection) para obtener una lista de métodos que puede usar con DIB sección mapas de bits.  
  
##  <a name="a-namebitblta--cimagebitblt"></a><a name="bitblt"></a>CImage::BitBlt  
 Copia un mapa de bits desde el contexto de dispositivo de origen en el contexto del dispositivo actual.  
  
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
 `hDestDC`  
 El destino **HDC**.  
  
 `xDest`  
 Coordenada x lógica de la esquina superior izquierda del rectángulo de destino.  
  
 `yDest`  
 Coordenada y lógica de la esquina superior izquierda del rectángulo de destino.  
  
 `dwROP`  
 Para realizar la operación de trama. Los códigos de operación de trama definen exactamente cómo combinar los bits de origen, el destino y el patrón (como se define por el pincel seleccionado actualmente) para formar el destino. Consulte [BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370) en la [!INCLUDE[winSDK](./includes/winsdk_md.md)] para obtener una lista de otros códigos de operación de trama y sus descripciones.  
  
 `pointDest`  
 Un [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) estructura indicando la esquina superior izquierda del rectángulo de destino.  
  
 `nDestWidth`  
 El ancho, en unidades lógicas, del rectángulo de destino.  
  
 `nDestHeight`  
 Alto, en unidades lógicas, del rectángulo de destino.  
  
 `xSrc`  
 Coordenada x lógica de la esquina superior izquierda del rectángulo de origen.  
  
 `ySrc`  
 Coordenada y lógica de la esquina superior izquierda del rectángulo de origen.  
  
 `rectDest`  
 Un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que indica el rectángulo de destino.  
  
 `pointSrc`  
 Un **punto** estructura indicando la esquina superior izquierda del rectángulo de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370) en el [!INCLUDE[winSDK](./includes/winsdk_md.md)].  
  
##  <a name="a-namecimagea--cimagecimage"></a><a name="cimage"></a>CImage::CImage  
 Construye un objeto `CImage`.  
  
```
CImage() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Una vez creado el objeto, llame a [crear](#create), [carga](#load), [LoadFromResource](#loadfromresource), o [adjuntar](#attach) adjuntar un mapa de bits del objeto.  
  
 **Nota** en Visual Studio, esta clase mantiene un recuento del número de `CImage` objetos creados. Cuando el recuento llega a 0, la función **GdiplusShutdown** llama automáticamente para liberar los recursos utilizados por GDI +. Esto garantiza que cualquier `CImage` objetos creados directa o indirectamente por archivos DLL siempre se destruyen correctamente y que **GdiplusShutdown** no se llama desde DllMain.  
  
 Uso global `CImage` objetos en un archivo DLL no se recomienda. Si necesita usar un global `CImage` objeto en un archivo DLL, llamada [CImage::ReleaseGDIPlus](#releasegdiplus) para liberar explícitamente los recursos utilizados por GDI +.  
  
##  <a name="a-namecreatea--cimagecreate"></a><a name="create"></a>CImage::Create  
 Crea un `CImage` de mapa de bits y adjúntelo a construido anteriormente `CImage` objeto.  
  
```
BOOL Create(
 int nWidth,
 int nHeight,
 int nBPP,
 DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nWidth`  
 El ancho de la `CImage` mapa de bits, en píxeles.  
  
 `nHeight`  
 El alto de la `CImage` mapa de bits, en píxeles. Si `nHeight` es positivo, el mapa de bits es un DIB de abajo a arriba y su origen es la esquina inferior izquierda. Si `nHeight` es negativo, el mapa de bits es un DIB de arriba a abajo y su origen es la esquina superior izquierda.  
  
 `nBPP`  
 El número de bits por píxel del mapa de bits. Normalmente, 4, 8, 16, 24 o 32. Puede ser 1 para los mapas de bits monocromático o máscaras.  
  
 `dwFlags`  
 Especifica si el objeto de mapa de bits tiene un canal alfa. Puede ser una combinación de cero o más de los siguientes valores:  
  
- **createAlphaChannel** sólo puede utilizarse si `nBPP` es 32, y `eCompression` es **BI_RGB**. Si se especifica, la imagen creada tiene un valor de transparencia alfa para cada píxel, se almacenan en la 4ª bytes de cada píxel (sin utilizar en una imagen de 32 bits no alfabéticos). Este canal alfa se utiliza automáticamente cuando se llama a [CImage::AlphaBlend](#alphablend).  
  
> [!NOTE]
>  En las llamadas a [CImage::Draw](#draw), las imágenes con un canal alfa son automáticamente alfa mezclado en el destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="a-namecreateexa--cimagecreateex"></a><a name="createex"></a>CImage::CreateEx  
 Crea un `CImage` de mapa de bits y adjúntelo a construido anteriormente `CImage` objeto.  
  
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
 `nWidth`  
 El ancho de la `CImage` mapa de bits, en píxeles.  
  
 `nHeight`  
 El alto de la `CImage` mapa de bits, en píxeles. Si `nHeight` es positivo, el mapa de bits es un DIB de abajo a arriba y su origen es la esquina inferior izquierda. Si `nHeight` es negativo, el mapa de bits es un DIB de arriba a abajo y su origen es la esquina superior izquierda.  
  
 `nBPP`  
 El número de bits por píxel del mapa de bits. Normalmente, 4, 8, 16, 24 o 32. Puede ser 1 para los mapas de bits monocromático o máscaras.  
  
 `eCompression`  
 Especifica el tipo de compresión para un mapa de bits comprimido de abajo arriba (no se pueden comprimir DIB de arriba a abajo). Puede presentar uno de los siguientes valores:  
  
- **BI_RGB** el formato es sin comprimir. Especificación de este valor cuando se llama a `CImage::CreateEx` equivale a llamar a `CImage::Create`.  
  
- **BI_BITFIELDS** el formato sin comprimir y la tabla de colores se compone de tres `DWORD` máscaras de color que especifican el color rojo, verde y azul, respectivamente, componentes, de cada píxel. Esto es válido cuando se utiliza con los mapas de bits de 16 y 32 bpp.  
  
 *pdwBitfields*  
 Sólo se utiliza si `eCompression` está establecido en **BI_BITFIELDS**, de lo contrario, debe ser **NULL**. Un puntero a una matriz de tres `DWORD` máscaras de bits, especificando los bits de cada píxel se usan para el rojo, verde y azul del color, los componentes, respectivamente. Para obtener información acerca de restricciones para los campos de bits, consulte [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) en el [!INCLUDE[winSDK](./includes/winsdk_md.md)].  
  
 `dwFlags`  
 Especifica si el objeto de mapa de bits tiene un canal alfa. Puede ser una combinación de cero o más de los siguientes valores:  
  
- **createAlphaChannel** sólo puede utilizarse si `nBPP` es 32, y `eCompression` es **BI_RGB**. Si se especifica, la imagen creada tiene un valor de transparencia alfa para cada píxel, se almacenan en la 4ª bytes de cada píxel (sin utilizar en una imagen de 32 bits no alfabéticos). Este canal alfa se utiliza automáticamente cuando se llama a [CImage::AlphaBlend](#alphablend).  
  
    > [!NOTE]
    >  En las llamadas a [CImage::Draw](#draw), las imágenes con un canal alfa son automáticamente alfa mezclado en el destino.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si se realiza correctamente. De lo contrario, **FALSE**.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un mapa de bits de 100 x 100 píxeles, el uso de 16 bits para codificar cada píxel. En un píxel determinado de 16 bits, bits 0-3 codifican el componente rojo, bits 4-7 codifican verde y azul de codificar de bits del 8 al 11. Los 4 bits restantes no se utilizan.  

```cpp  
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```


##  <a name="a-namedestroya--cimagedestroy"></a><a name="destroy"></a>CImage::Destroy  
 Desasocia el mapa de bits de la `CImage` del objeto y se destruye el mapa de bits.  
  
```
void Destroy() throw();
```  
  
##  <a name="a-namedetacha--cimagedetach"></a><a name="detach"></a>CImage::Detach  
 Desasocia un mapa de bits desde un `CImage` objeto.  
  
```
HBITMAP Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el mapa de bits separado, o **NULL** si no está conectado a ningún mapa de bits.  
  
##  <a name="a-namedrawa--cimagedraw"></a><a name="draw"></a>CImage::Draw  
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
 `hDestDC`  
 Identificador del contexto de dispositivo de destino.  
  
 `xDest`  
 La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `yDest`  
 La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `nDestWidth`  
 El ancho, en unidades lógicas, del rectángulo de destino.  
  
 `nDestHeight`  
 Alto, en unidades lógicas, del rectángulo de destino.  
  
 `xSrc`  
 La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `ySrc`  
 La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `nSrcWidth`  
 El ancho, en unidades lógicas, del rectángulo de origen.  
  
 `nSrcHeight`  
 Alto, en unidades lógicas, del rectángulo de origen.  
  
 `rectDest`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura, que identifica el destino.  
  
 `rectSrc`  
 Una referencia a un `RECT` estructura, que identifica el origen.  
  
 `pointDest`  
 Una referencia a un [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) estructura que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 **Dibujar** realiza la misma operación que [StretchBlt](#stretchblt), a menos que la imagen contiene un canal alfa o color transparente. En ese caso, **dibujar** realiza la misma operación como [TransparentBlt](#transparentblt) o [AlphaBlend](#alphablend) según sea necesario.  
  
 Para las versiones de **dibujar** que no especifica un rectángulo de origen, la imagen de origen completa es el valor predeterminado. Para la versión de **dibujar** que no especifica un tamaño para el rectángulo de destino, el tamaño de la imagen de origen es el valor predeterminado y sin estiramiento o reducción se produce.  
  
##  <a name="a-namegetbitsa--cimagegetbits"></a><a name="getbits"></a>CImage::GetBits  
 Recupera un puntero a los valores de bits real de un píxel determinado en un mapa de bits.  
  
```
void* GetBits() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al búfer de mapa de bits. Si el mapa de bits es un DIB de abajo arriba, señala el puntero cerca del final del búfer. Si el mapa de bits es un DIB de arriba a abajo, el puntero señala al primer byte del búfer.  
  
### <a name="remarks"></a>Comentarios  
 Utilizando este puntero, junto con el valor devuelto por [GetPitch](#getpitch), puede buscar y cambiar los píxeles individuales de una imagen.  
  
> [!NOTE]
>  Este método admite sólo DIB sección mapas de bits. Por consiguiente, tener acceso a los píxeles de un `CImage` del mismo modo que lo haría con los píxeles de una sección DIB de objeto. El puntero devuelto apunta al píxel en la ubicación (0, 0).  
  
##  <a name="a-namegetbppa--cimagegetbpp"></a><a name="getbpp"></a>CImage::GetBPP  
 Recupera el valor de bits por píxel.  
  
```
int GetBPP() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bits por píxel.  
  
### <a name="remarks"></a>Comentarios  
 Este valor determina el número de bits que definen cada píxel y el número máximo de colores del mapa de bits.  
  
 Normalmente, los bits por píxel es 1, 4, 8, 16, 24 o 32. Consulte la **biBitCount** miembro de [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) en la [!INCLUDE[winSDK](./includes/winsdk_md.md)] para obtener más información acerca de este valor.  
  
##  <a name="a-namegetcolortablea--cimagegetcolortable"></a><a name="getcolortable"></a>CImage::GetColorTable  
 Recupera los valores de color rojos, verdes, azul (RGB) de un intervalo de entradas en la paleta de la sección DIB.  
  
```
void GetColorTable(UINT iFirstColor,
 UINT nColors,
 RGBQUAD* prgbColors) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `iFirstColor`  
 El índice de la tabla de color de la primera entrada a recuperar.  
  
 `nColors`  
 El número de entradas de la tabla de color para recuperar.  
  
 `prgbColors`  
 Un puntero a la matriz de [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) entradas estructuras para recuperar el color de la tabla.  
  
##  <a name="a-namegetdca--cimagegetdc"></a><a name="getdc"></a>CImage::GetDC  
 Recupera el contexto de dispositivo que tiene actualmente la imagen seleccionada en él.  
  
```
HDC GetDC() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 Para cada llamada a `GetDC`, debe tener una llamada subsiguiente a [ReleaseDC](#releasedc).  
  
##  <a name="a-namegetexporterfilterstringa--cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a>CImage::GetExporterFilterString  
 Busca los formatos de imagen disponibles para guardar las imágenes.  
  
```
static HRESULT GetExporterFilterString(CSimpleString& strExporters,
 CSimpleArray<GUID>& aguidFileTypes,
 LPCTSTR pszAllFilesDescription = NULL,
 DWORD dwExclude = excludeDefaultSave,
 TCHAR chSeparator = _T('|'));
```  
  
### <a name="parameters"></a>Parámetros  
 *strExporters*  
 Una referencia a un **CSimpleString** objeto. Consulte **comentarios** para obtener más información.  
  
 `aguidFileTypes`  
 Matriz de GUID, con cada elemento corresponde a uno de los tipos de archivo en la cadena. En el ejemplo de `pszAllFilesDescription` a continuación, `aguidFileTypes`[0] es `GUID_NULL` y los demás valores de la matriz son los formatos de archivo de imagen admitidos por el sistema operativo actual.  
  
> [!NOTE]
>  Para obtener una lista completa de constantes, consulte **constantes de formato de archivo de imagen** en el [!INCLUDE[winSDK](./includes/winsdk_md.md)].  
  
 `pszAllFilesDescription`  
 Si este parámetro no es **NULL**, la cadena de filtro tendrá un filtro adicional al principio de la lista. Este filtro tendrá el valor actual de `pszAllFilesDescription` para su descripción y acepta archivos de cualquier extensión compatible con cualquier otro exportador en la lista.  
  
 Por ejemplo:  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes, 
 _T("All Image Files"));
```  

  
 `dwExclude`  
 Conjunto de marcadores de bits que especifica qué tipos de archivo a excluir de la lista. Marcadores permitidos son:  
  
- **excludeGIF** = 0 x 01 GIF excluye los archivos.  
  
- **excludeBMP** = 0 x 02 excluye BMP (mapa de bits de Windows) de los archivos.  
  
- **excludeEMF** = 0 x 04 excluye EMF (metarchivo mejorado) archivos.  
  
- **excludeWMF** = 0 x 08 excluye WMF (metarchivo de Windows) de los archivos.  
  
- **excludeJPEG** = 0 x 10 JPEG excluye los archivos.  
  
- **excludePNG** = 0 x 20 PNG excluye los archivos.  
  
- **excludeTIFF** = 0 x 40 TIFF excluye los archivos.  
  
- **excludeIcon** = 0 x 80 excluye ICO (icono de Windows) de los archivos.  
  
- **excludeOther** = 0 x 80000000 excluye cualquier otro tipo de archivo no enumerado anteriormente.  
  
- **excludeDefaultLoad** = 0 para todos los archivos predeterminada se incluyen los tipos de carga  
  
- **excludeDefaultSave** = **excludeIcon | excludeEMF | excludeWMF** para guardar, estos archivos se excluyen de forma predeterminada porque normalmente tienen requisitos especiales.  
  
 `chSeparator`  
 El separador utilizado entre los formatos de imagen. Consulte **comentarios** para obtener más información.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Puede pasar la cadena de formato resultante a la MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) formatos de objeto que se va a exponer las extensiones de archivo de la imagen disponible en el cuadro de diálogo Guardar como.  
  
 El parámetro *strExporter* tiene el formato:  
  
 archivo description0 | \*.ext0 | filedescription1 | \*. ext1 |... Descripción de archivo *n*|\*. ext *n*||  
  
 donde ' |' es el carácter separador especificado por `chSeparator`. Por ejemplo:  
  
 `"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`  
  
 Use el separador predeterminado ' |' si se pasa esta cadena a MFC `CFileDialog` objeto. Use el separador null '\0' Si esta cadena se pasa a un cuadro de diálogo Guardar archivo común.  
  
##  <a name="a-namegetheighta--cimagegetheight"></a><a name="getheight"></a>CImage::GetHeight  
 Recupera el alto, en píxeles, de una imagen.  
  
```
int GetHeight() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Alto, en píxeles, de una imagen.  
  
##  <a name="a-namegetimporterfilterstringa--cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a>CImage::GetImporterFilterString  
 Busca los formatos de imagen disponibles para cargar imágenes.  
  
```
static HRESULT GetImporterFilterString(CSimpleString& strImporters,
 CSimpleArray<GUID>& aguidFileTypes,
 LPCTSTR pszAllFilesDescription = NULL,
 DWORD dwExclude = excludeDefaultLoad,
 TCHAR chSeparator = _T('|'));
```  
  
### <a name="parameters"></a>Parámetros  
 *strImporters*  
 Una referencia a un **CSimpleString** objeto. Consulte **comentarios** para obtener más información.  
  
 `aguidFileTypes`  
 Matriz de GUID, con cada elemento corresponde a uno de los tipos de archivo en la cadena. En el ejemplo de `pszAllFilesDescription` a continuación, `aguidFileTypes`[0] es `GUID_NULL` con la matriz restante valores son los formatos de archivo de imagen admitidos por el sistema operativo actual.  
  
> [!NOTE]
>  Para obtener una lista completa de constantes, consulte **constantes de formato de archivo de imagen** en el [!INCLUDE[winSDK](./includes/winsdk_md.md)].  
  
 `pszAllFilesDescription`  
 Si este parámetro no es **NULL**, la cadena de filtro tendrá un filtro adicional al principio de la lista. Este filtro tendrá el valor actual de `pszAllFilesDescription` para su descripción y acepta archivos de cualquier extensión compatible con cualquier otro exportador en la lista.  
  
 Por ejemplo:  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes, 
 _T("All Image Files"));
```  

  
 `dwExclude`  
 Conjunto de marcadores de bits que especifica qué tipos de archivo a excluir de la lista. Marcadores permitidos son:  
  
- **excludeGIF** = 0 x 01 GIF excluye los archivos.  
  
- **excludeBMP** = 0 x 02 excluye BMP (mapa de bits de Windows) de los archivos.  
  
- **excludeEMF** = 0 x 04 excluye EMF (metarchivo mejorado) archivos.  
  
- **excludeWMF** = 0 x 08 excluye WMF (metarchivo de Windows) de los archivos.  
  
- **excludeJPEG** = 0 x 10 JPEG excluye los archivos.  
  
- **excludePNG** = 0 x 20 PNG excluye los archivos.  
  
- **excludeTIFF** = 0 x 40 TIFF excluye los archivos.  
  
- **excludeIcon** = 0 x 80 excluye ICO (icono de Windows) de los archivos.  
  
- **excludeOther** = 0 x 80000000 excluye cualquier otro tipo de archivo no enumerado anteriormente.  
  
- **excludeDefaultLoad** = 0 para todos los archivos predeterminada se incluyen los tipos de carga  
  
- **excludeDefaultSave** = **excludeIcon | excludeEMF | excludeWMF** para guardar, estos archivos se excluyen de forma predeterminada porque normalmente tienen requisitos especiales.  
  
 `chSeparator`  
 El separador utilizado entre los formatos de imagen. Consulte **comentarios** para obtener más información.  
  
### <a name="remarks"></a>Comentarios  
 Puede pasar la cadena de formato resultante a la MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) formatos de objeto que se va a exponer las extensiones de archivo de la imagen disponible en la **abrir archivo** cuadro de diálogo.  
  
 El parámetro *strImporter* tiene el formato:  
  
 archivo description0 | \*.ext0 | filedescription1 | \*. ext1 |... Descripción de archivo *n*|\*. ext *n*||  
  
 donde ' |' es el carácter separador especificado por `chSeparator`. Por ejemplo:  
  
 `"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`  
  
 Use el separador predeterminado ' |' si se pasa esta cadena a MFC `CFileDialog` objeto. Use el separador null '\0' si se pasa esta cadena como un común **abrir archivo** cuadro de diálogo.  
  
##  <a name="a-namegetmaxcolortableentriesa--cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a>CImage::GetMaxColorTableEntries  
 Recupera el número máximo de entradas en la tabla de colores.  
  
```
int GetMaxColorTableEntries() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de entradas en la tabla de colores.  
  
### <a name="remarks"></a>Comentarios  
 Este método admite sólo DIB sección mapas de bits.  
  
##  <a name="a-namegetpitcha--cimagegetpitch"></a><a name="getpitch"></a>CImage::GetPitch  
 Recupera el tono de una imagen.  
  
```
int GetPitch() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tono de la imagen. Si el valor devuelto es negativo, el mapa de bits es un DIB de abajo a arriba y su origen es la esquina inferior izquierda. Si el valor devuelto es positivo, el mapa de bits es un DIB de arriba a abajo y su origen es la esquina superior izquierda.  
  
### <a name="remarks"></a>Comentarios  
 El paso es la distancia, en bytes, entre dos direcciones de memoria que representan el principio de una línea de mapa de bits y el comienzo de la siguiente línea de mapa de bits. Porque tono se mide en bytes, el tono de una imagen puede ayudarle a determinar el formato de píxel. El tono también puede incluir memoria adicional, que se reserva para el mapa de bits.  
  
 Utilice `GetPitch` con [GetBits](#getbits) para encontrar los píxeles individuales de una imagen.  
  
> [!NOTE]
>  Este método admite sólo DIB sección mapas de bits.  
  
##  <a name="a-namegetpixela--cimagegetpixel"></a><a name="getpixel"></a>CImage::GetPixel  
 Recupera el color del píxel en la ubicación especificada por *x* y *y*.  
  
```
COLORREF GetPixel(int x,int y) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Coordenada x del píxel.  
  
 *y*  
 Coordenada y del píxel.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de (RGB) de rojo, verde, azul del píxel. Si el píxel está fuera de la región de recorte actual, el valor devuelto es **CLR_INVALID**.  
  
##  <a name="a-namegetpixeladdressa--cimagegetpixeladdress"></a><a name="getpixeladdress"></a>CImage::GetPixelAddress  
 Recupera la dirección exacta de un píxel.  
  
```
void* GetPixelAddress(int x,int y) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Coordenada x del píxel.  
  
 *y*  
 Coordenada y del píxel.  
  
### <a name="remarks"></a>Comentarios  
 La dirección se determina según las coordenadas de un píxel, el tono de mapa de bits y los bits por píxel.  
  
 Para formatos que tienen menos de 8 bits por píxel, este método devuelve la dirección del byte que contiene el píxel. Por ejemplo, si el formato de imagen tiene 4 bits por píxel, `GetPixelAddress` devuelve la dirección del primer píxel en el byte y se debe calcular de 2 píxeles por byte.  
  
> [!NOTE]
>  Este método admite sólo DIB sección mapas de bits.  
  
##  <a name="a-namegettransparentcolora--cimagegettransparentcolor"></a><a name="gettransparentcolor"></a>CImage::GetTransparentColor  
 Recupera la ubicación indizada del color transparente en la paleta de colores.  
  
```
LONG GetTransparentColor() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de color transparente.  
  
##  <a name="a-namegetwidtha--cimagegetwidth"></a><a name="getwidth"></a>CImage::GetWidth  
 Recupera el ancho, en píxeles, de una imagen.  
  
```
int GetWidth() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho del mapa de bits, en píxeles.  
  
##  <a name="a-nameisdibsectiona--cimageisdibsection"></a><a name="isdibsection"></a>CImage::IsDIBSection  
 Determina si el mapa de bits adjunto es una sección DIB.  
  
```
bool IsDIBSection() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el mapa de bits adjunto es una sección DIB. De lo contrario, **false**.  
  
### <a name="remarks"></a>Comentarios  
 Si el mapa de bits no es una sección DIB, no puede utilizar la siguiente `CImage` métodos que admiten los mapas de sección DIB solo:  
  
- [GetBits](#getbits)  
  
- [GetColorTable](#getcolortable)  
  
- [GetMaxColorTableEntries](#getmaxcolortableentries)  
  
- [GetPitch](#getpitch)  
  
- [GetPixelAddress](#getpixeladdress)  
  
- [Isindexed como](#isindexed)  
  
- [SetColorTable](#setcolortable)  
  
##  <a name="a-nameisindexeda--cimageisindexed"></a><a name="isindexed"></a>CImage::IsIndexed  
 Determina si los píxeles del mapa de bits se asignan a una paleta de colores.  
  
```
bool IsIndexed() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si indizada; en caso contrario **false**.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve **true** sólo si el mapa de bits es de 8 bits (256 colores) o menos.  
  
> [!NOTE]
>  Este método admite sólo DIB sección mapas de bits.  
  
##  <a name="a-nameisnulla--cimageisnull"></a><a name="isnull"></a>CImage::IsNull  
 Determina si un mapa de bits está cargado actualmente.  
  
```
bool IsNull() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve **True** si un mapa de bits no está actualmente cargado; de lo contrario **False**.  
  
##  <a name="a-nameistransparencysupporteda--cimageistransparencysupported"></a><a name="istransparencysupported"></a>CImage:: IsTransparencySupported  
 Indica si la aplicación admite mapas de bits transparentes y se compiló para Windows 2000 o posterior.  
  
```
static BOOL IsTransparencySupported() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la plataforma actual admite la transparencia. En caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto es distinto de cero y se admite la transparencia, una llamada a [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt), o [dibujar](#draw) controlará colores transparentes.  
  
 Si la aplicación se compila para su uso con sistemas operativos antes de Windows 2000 o Windows 98, este método siempre devolverá 0, incluso en sistemas operativos más recientes.  
  

##  <a name="a-nameloada--cimageload"></a><a name="load"></a>CImage::Load  
 Carga una imagen.  
  
```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszFileName`  
 Un puntero a una cadena que contiene el nombre del archivo de imagen para cargar.  
  
 `pStream`  
 Puntero a una secuencia que contiene el nombre del archivo de imagen para cargar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Carga la imagen especificada por *pszFileName* o `pStream`.  
  
 Tipos de imagen válido son BMP, GIF, JPEG, PNG y TIFF.  
  
##  <a name="a-nameloadfromresourcea--cimageloadfromresource"></a><a name="loadfromresource"></a>CImage::LoadFromResource  
 Carga una imagen desde un `BITMAP` recursos.  
  
```
void LoadFromResource(
 HINSTANCE hInstance,
 LPCTSTR pszResourceName) throw();

void LoadFromResource(
 HINSTANCE hInstance,
 UINT nIDResource) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstance`  
 Identificador de una instancia del módulo que contiene la imagen que se va a cargar.  
  
 `pszResourceName`  
 Puntero a la cadena que contiene el nombre del recurso que contiene la imagen para cargar.  
  
 `nIDResource`  
 El identificador del recurso para cargar.  
  
### <a name="remarks"></a>Comentarios  
 El recurso debe ser de tipo `BITMAP`.  
  
##  <a name="a-namemaskblta--cimagemaskblt"></a><a name="maskblt"></a>CImage:: MaskBlt  
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
 `hDestDC`  
 El identificador para el módulo cuyo ejecutable contiene el recurso.  
  
 `xDest`  
 La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `yDest`  
 La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `nDestWidth`  
 El ancho, en unidades lógicas, del mapa de bits de origen y el rectángulo de destino.  
  
 `nDestHeight`  
 Alto, en unidades lógicas, del mapa de bits de origen y el rectángulo de destino.  
  
 `xSrc`  
 Coordenada x lógica de la esquina superior izquierda del mapa de bits de origen.  
  
 `ySrc`  
 Coordenada y lógica de la esquina superior izquierda del mapa de bits de origen.  
  
 `hbmMask`  
 Identificador del mapa de bits de máscara monocromática combinado con el mapa de bits de color en el contexto de dispositivo de origen.  
  
 `xMask`  
 El desplazamiento horizontal de píxel del mapa de bits de la máscara especificada por el `hbmMask` parámetro.  
  
 `yMask`  
 El desplazamiento vertical de píxel del mapa de bits de la máscara especificada por el `hbmMask` parámetro.  
  
 `dwROP`  
 Especifica el primer y segundo plano trama ternario los códigos de operación que utiliza el método para controlar la combinación de datos de origen y destino. El código de operación de trama de fondo se almacena en el byte de orden superior de la palabra de orden superior de este valor; el código de operación de trama de primer plano se almacena en el byte de orden inferior de la palabra de orden superior de este valor; la palabra de orden inferior de este valor se omite y debe ser cero. Para obtener una explicación del primer y segundo plano en el contexto de este método, consulte `MaskBlt` en el [!INCLUDE[winSDK](./includes/winsdk_md.md)]. Para obtener una lista de códigos de operación de trama comunes, consulte `BitBlt` en el [!INCLUDE[winSDK](./includes/winsdk_md.md)].  
  
 `rectDest`  
 Una referencia a un `RECT` estructura, que identifica el destino.  
  
 `pointSrc`  
 Un `POINT` estructura indicando la esquina superior izquierda del rectángulo de origen.  
  
 `pointMask`  
 Un **punto** estructura indicando la esquina superior izquierda del mapa de bits de máscara.  
  
 `pointDest`  
 Una referencia a un **punto** estructura que identifica la esquina superior izquierda del rectángulo de destino, en unidades lógicas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método se aplica a Windows NT, versiones 4.0 y versiones posteriores únicamente.  
  
##  <a name="a-nameoperatorhbitmapa--cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a>CImage::operator HBITMAP  
 Utilice este operador para obtener el identificador de Windows GDI adjunto de la `CImage` objeto. Este operador es un operador de conversión, que admite el uso directo de una `HBITMAP` objeto.  
  
##  <a name="a-nameplgblta--cimageplgblt"></a><a name="plgblt"></a>CImage::PlgBlt  
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
 `hDestDC`  
 Identificador del contexto de dispositivo de destino.  
  
 *pPoints*  
 Un puntero a una matriz de tres puntos en el espacio lógico que identifican los tres esquinas paralelogramo de destino. La esquina superior izquierda del rectángulo de origen se asigna al primer punto en la esquina inferior izquierda hasta el tercer punto, la esquina superior derecha hasta el segundo punto de la matriz y esta matriz. La esquina inferior derecha del rectángulo de origen se asigna hasta el cuarto punto implícito en el paralelogramo.  
  
 `hbmMask`  
 Identificador de un mapa de bits monocromo opcional que se utiliza para enmascarar los colores del rectángulo de origen.  
  
 `xSrc`  
 La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `ySrc`  
 La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `nSrcWidth`  
 El ancho, en unidades lógicas, del rectángulo de origen.  
  
 `nSrcHeight`  
 Alto, en unidades lógicas, del rectángulo de origen.  
  
 `xMask`  
 Coordenada x de la esquina superior izquierda del mapa de bits monocromático.  
  
 `yMask`  
 Coordenada y de la esquina superior izquierda del mapa de bits monocromático.  
  
 `rectSrc`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que especifica las coordenadas del rectángulo de origen.  
  
 `pointMask`  
 Un [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) estructura indicando la esquina superior izquierda del mapa de bits de máscara.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si `hbmMask` identifica un mapa de bits monocromático válido **PlgBit** utiliza este mapa de bits para enmascarar los bits de datos de color del rectángulo de origen.  
  
 Este método se aplica a Windows NT, versiones 4.0 y versiones posteriores únicamente. Consulte [PlgBlt](http://msdn.microsoft.com/library/windows/desktop/dd162804) en la [!INCLUDE[winSDK](./includes/winsdk_md.md)] para obtener más información.  
  
##  <a name="a-namereleasedca--cimagereleasedc"></a><a name="releasedc"></a>CImage::ReleaseDC  
 Libera el contexto de dispositivo.  
  
```
void ReleaseDC() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Dado que sólo un mapa de bits puede seleccionarse en un contexto de dispositivo a la vez, debe llamar a `ReleaseDC` para cada llamada a [GetDC](#getdc).  
  
##  <a name="a-namereleasegdiplusa--cimagereleasegdiplus"></a><a name="releasegdiplus"></a>CImage::ReleaseGDIPlus  
 Libera los recursos utilizados por GDI +.  
  
```
void ReleaseGDIPlus() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a este método para liberar los recursos asignados por global `CImage` objeto. Consulte [CImage::CImage](#cimage).  
  
##  <a name="a-namesavea--cimagesave"></a><a name="save"></a>CImage::Save  
 Guarda una imagen en la secuencia especificada o el archivo en disco.  
  
```
HRESULT Save(IStream* pStream,
 REFGUID guidFileType) const throw();

HRESULT Save(LPCTSTR pszFileName,
 REFGUID guidFileType= GUID_NULL) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 Puntero a un objeto IStream de COM que contiene los datos de archivo de imagen.  
  
 *pszFileName*  
 Puntero al nombre de archivo para la imagen.  
  
 `guidFileType`  
 El tipo de archivo para guardar la imagen como. Puede ser uno de los siguientes:  
  
- **ImageFormatBMP** una imagen de mapa de bits sin comprimir.  
  
- **ImageFormatPNG** imagen comprimida de un gráfico PNG (Portable Network).  
  
- **ImageFormatJPEG** imagen comprimida de un JPEG.  
  
- **ImageFormatGIF** A comprimido en formato GIF.  
  
> [!NOTE]
>  Para obtener una lista completa de constantes, consulte **constantes de formato de archivo de imagen** en el [!INCLUDE[winSDK](./includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para guardar la imagen con un nombre y tipo especificados. Si el `guidFileType` no se incluye el parámetro, se utilizará la extensión del nombre de archivo para determinar el formato de imagen. Si no se proporciona ninguna extensión, se guardará la imagen en formato BMP.  
  
##  <a name="a-namesetcolortablea--cimagesetcolortable"></a><a name="setcolortable"></a>CImage::SetColorTable  
 Establece los valores de color rojos, verdes, azul (RGB) de un intervalo de entradas de la paleta de la sección DIB.  
  
```
void SetColorTable(
  UINT iFirstColor, 
  UINT nColors,
  const RGBQUAD* prgbColors) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `iFirstColor`  
 El índice de la tabla de color de la primera entrada para establecer.  
  
 `nColors`  
 El número de entradas de la tabla de color para establecer.  
  
 `prgbColors`  
 Un puntero a la matriz de [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) estructuras para establecer el color de entradas de la tabla.  
  
### <a name="remarks"></a>Comentarios  
 Este método admite sólo DIB sección mapas de bits.  
  
##  <a name="a-namesetpixela--cimagesetpixel"></a><a name="setpixel"></a>CImage::SetPixel  
 Establece el color de un píxel en una ubicación determinada del mapa de bits.  
  
```
void SetPixel(int x, int y, COLORREF color) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 La ubicación horizontal del píxel que se va a establecer.  
  
 *y*  
 Ubicación vertical del píxel que se va a establecer.  
  
 `color`  
 El color al que se establece el píxel.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce un error si se encuentran fuera de la región de recorte seleccionado de coordenadas de píxel.  
  
##  <a name="a-namesetpixelindexeda--cimagesetpixelindexed"></a><a name="setpixelindexed"></a>CImage::SetPixelIndexed  
 Establece el color del píxel al color ubicado en `iIndex` en la paleta de colores.  
  
```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 La ubicación horizontal del píxel que se va a establecer.  
  
 *y*  
 Ubicación vertical del píxel que se va a establecer.  
  
 `iIndex`  
 El índice de un color en la paleta de colores.  
  
##  <a name="a-namesetpixelrgba--cimagesetpixelrgb"></a><a name="setpixelrgb"></a>CImage::SetPixelRGB  
 Establece el píxel en las ubicaciones especificadas por *x* y *y* a los colores indicados por *r*, *g*, y *b*, en una color rojo, verde, azul, imagen (RGB).  
  
```
void SetPixelRGB(  
 int x,
 int y,
 BYTE r,
 BYTE g,
 BYTE b) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 La ubicación horizontal del píxel que se va a establecer.  
  
 *y*  
 Ubicación vertical del píxel que se va a establecer.  
  
 *r*  
 La intensidad de color rojo.  
  
 *g*  
 La intensidad del color verde.  
  
 *b*  
 La intensidad del color azul.  
  
### <a name="remarks"></a>Comentarios  
 Los parámetros de rojos, verde y azules se representan mediante un número entre 0 y 255. Si establece los tres parámetros a cero, el color resultante combinado es negro. Si establece los tres parámetros a 255, el color resultante combinado es blanco.  
  
##  <a name="a-namesettransparentcolora--cimagesettransparentcolor"></a><a name="settransparentcolor"></a>CImage::SetTransparentColor  
 Establece el color en una ubicación indizada especificada como transparente.  
  
```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *iTransparentColor*  
 El índice en una paleta de colores del color para establecer a transparente. Si-1, ningún color se establece en transparente.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del color establecido previamente como transparente.  
  
##  <a name="a-namestretchblta--cimagestretchblt"></a><a name="stretchblt"></a>CImage::StretchBlt  
 Copia un mapa de bits desde el contexto de dispositivo de origen en el contexto del dispositivo actual.  
  
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
 `hDestDC`  
 Identificador del contexto de dispositivo de destino.  
  
 `xDest`  
 La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `yDest`  
 La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `nDestWidth`  
 El ancho, en unidades lógicas, del rectángulo de destino.  
  
 `nDestHeight`  
 Alto, en unidades lógicas, del rectángulo de destino.  
  
 `dwROP`  
 Para realizar la operación de trama. Los códigos de operación de trama definen exactamente cómo combinar los bits de origen, el destino y el patrón (como se define por el pincel seleccionado actualmente) para formar el destino. Consulte [BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370) en la [!INCLUDE[winSDK](./includes/winsdk_md.md)] para obtener una lista de otros códigos de operación de trama y sus descripciones.  
  
 `rectDest`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura, que identifica el destino.  
  
 `xSrc`  
 La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `ySrc`  
 La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `nSrcWidth`  
 El ancho, en unidades lógicas, del rectángulo de origen.  
  
 `nSrcHeight`  
 Alto, en unidades lógicas, del rectángulo de origen.  
  
 `rectSrc`  
 Una referencia a un `RECT` estructura, que identifica el origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [StretchBlt](http://msdn.microsoft.com/library/windows/desktop/dd145120) en el [!INCLUDE[winSDK](./includes/winsdk_md.md)].  
  
##  <a name="a-nametransparentblta--cimagetransparentblt"></a><a name="transparentblt"></a>CImage:: TransparentBlt  
 Copia un mapa de bits desde el contexto de dispositivo de origen en el contexto del dispositivo actual.  
  
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
 `hDestDC`  
 Identificador del contexto de dispositivo de destino.  
  
 `xDest`  
 La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `yDest`  
 La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `nDestWidth`  
 El ancho, en unidades lógicas, del rectángulo de destino.  
  
 `nDestHeight`  
 Alto, en unidades lógicas, del rectángulo de destino.  
  
 *crTransparent*  
 El color del mapa de bits de origen a tratar como transparente. De forma predeterminada, **CLR_INVALID**, que indica que se debe usar el color establecido actualmente como el color transparente de la imagen.  
  
 `rectDest`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura, que identifica el destino.  
  
 `xSrc`  
 La coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `ySrc`  
 La coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `nSrcWidth`  
 El ancho, en unidades lógicas, del rectángulo de origen.  
  
 `nSrcHeight`  
 Alto, en unidades lógicas, del rectángulo de origen.  
  
 `rectSrc`  
 Una referencia a un `RECT` estructura, que identifica el origen.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si se realiza correctamente, de lo contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 `TransparentBlt`se admite para los mapas de bits de origen de 4 bits por píxel y 8 bits por píxel. Utilice [CImage::AlphaBlend](#alphablend) para especificar los mapas de bits de 32 bits por píxel con transparencia.  
  
  
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
 [Ejemplo MMXSwarm](../../visual-cpp-samples.md)   
 [Ejemplo SimpleImage](../../visual-cpp-samples.md)   
 [Mapas de bits independientes del dispositivo](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   
 [Componentes de escritorio de COM de ATL](../../atl/atl-com-desktop-components.md)
 [mapas de bits independientes del dispositivo](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   










