---
title: Clase CMFCToolBarImages | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarImages
- AFXTOOLBARIMAGES/CMFCToolBarImages
- AFXTOOLBARIMAGES/CMFCToolBarImages::CMFCToolBarImages
- AFXTOOLBARIMAGES/CMFCToolBarImages::AdaptColors
- AFXTOOLBARIMAGES/CMFCToolBarImages::AddIcon
- AFXTOOLBARIMAGES/CMFCToolBarImages::AddImage
- AFXTOOLBARIMAGES/CMFCToolBarImages::CleanUp
- AFXTOOLBARIMAGES/CMFCToolBarImages::Clear
- AFXTOOLBARIMAGES/CMFCToolBarImages::ConvertTo32Bits
- AFXTOOLBARIMAGES/CMFCToolBarImages::CopyImageToClipboard
- AFXTOOLBARIMAGES/CMFCToolBarImages::CopyTo
- AFXTOOLBARIMAGES/CMFCToolBarImages::CreateFromImageList
- AFXTOOLBARIMAGES/CMFCToolBarImages::CreateRegionFromImage
- AFXTOOLBARIMAGES/CMFCToolBarImages::DeleteImage
- AFXTOOLBARIMAGES/CMFCToolBarImages::Draw
- AFXTOOLBARIMAGES/CMFCToolBarImages::DrawEx
- AFXTOOLBARIMAGES/CMFCToolBarImages::EnableRTL
- AFXTOOLBARIMAGES/CMFCToolBarImages::EndDrawImage
- AFXTOOLBARIMAGES/CMFCToolBarImages::ExtractIcon
- AFXTOOLBARIMAGES/CMFCToolBarImages::FillDitheredRect
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetAlwaysLight
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetBitsPerPixel
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetCount
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetDisabledImageAlpha
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetFadedImageAlpha
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetImageSize
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetImageWell
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetImageWellLight
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetLastImageRect
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetLightPercentage
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetMapTo3DColors
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetMask
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetResourceOffset
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetScale
- AFXTOOLBARIMAGES/CMFCToolBarImages::GetTransparentColor
- AFXTOOLBARIMAGES/CMFCToolBarImages::GrayImages
- AFXTOOLBARIMAGES/CMFCToolBarImages::Is32BitTransparencySupported
- AFXTOOLBARIMAGES/CMFCToolBarImages::IsPreMultiplyAutoCheck
- AFXTOOLBARIMAGES/CMFCToolBarImages::IsRTL
- AFXTOOLBARIMAGES/CMFCToolBarImages::IsReadOnly
- AFXTOOLBARIMAGES/CMFCToolBarImages::IsScaled
- AFXTOOLBARIMAGES/CMFCToolBarImages::IsUserImagesList
- AFXTOOLBARIMAGES/CMFCToolBarImages::IsValid
- AFXTOOLBARIMAGES/CMFCToolBarImages::Load
- AFXTOOLBARIMAGES/CMFCToolBarImages::LoadStr
- AFXTOOLBARIMAGES/CMFCToolBarImages::MapFromSysColor
- AFXTOOLBARIMAGES/CMFCToolBarImages::MapTo3dColors
- AFXTOOLBARIMAGES/CMFCToolBarImages::MapToSysColor
- AFXTOOLBARIMAGES/CMFCToolBarImages::MapToSysColorAlpha
- AFXTOOLBARIMAGES/CMFCToolBarImages::Mirror
- AFXTOOLBARIMAGES/CMFCToolBarImages::MirrorBitmap
- AFXTOOLBARIMAGES/CMFCToolBarImages::MirrorBitmapVert
- AFXTOOLBARIMAGES/CMFCToolBarImages::MirrorVert
- AFXTOOLBARIMAGES/CMFCToolBarImages::OnSysColorChange
- AFXTOOLBARIMAGES/CMFCToolBarImages::PrepareDrawImage
- AFXTOOLBARIMAGES/CMFCToolBarImages::Save
- AFXTOOLBARIMAGES/CMFCToolBarImages::SetAlwaysLight
- AFXTOOLBARIMAGES/CMFCToolBarImages::SetDisabledImageAlpha
- AFXTOOLBARIMAGES/CMFCToolBarImages::SetFadedImageAlpha
- AFXTOOLBARIMAGES/CMFCToolBarImages::SetImageSize
- AFXTOOLBARIMAGES/CMFCToolBarImages::SetLightPercentage
- AFXTOOLBARIMAGES/CMFCToolBarImages::SetMapTo3DColors
- AFXTOOLBARIMAGES/CMFCToolBarImages::SetPreMultiplyAutoCheck
- AFXTOOLBARIMAGES/CMFCToolBarImages::SetSingleImage
- AFXTOOLBARIMAGES/CMFCToolBarImages::SetTransparentColor
- AFXTOOLBARIMAGES/CMFCToolBarImages::SmoothResize
- AFXTOOLBARIMAGES/CMFCToolBarImages::UpdateImage
- AFXTOOLBARIMAGES/CMFCToolBarImages::PreMultiplyAlpha
- AFXTOOLBARIMAGES/CMFCToolBarImages::m_bDisableTrueColorAlpha
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarImages class
ms.assetid: d4e50518-9ffc-406f-9996-f79e5cd38155
caps.latest.revision: 31
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ff94497108033b17d52b79594fdbe30e8ed7da03
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarimages-class"></a>Clase CMFCToolBarImages
Las imágenes en una barra de herramientas. La `CMFCToolBarImages` clase administra la carga de recursos de la aplicación o de archivos de imágenes de barra de herramientas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCToolBarImages : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarImages::CMFCToolBarImages](#cmfctoolbarimages)|Construye un objeto `CMFCToolBarImages`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarImages::AdaptColors](#adaptcolors)||  
|[CMFCToolBarImages::AddIcon](#addicon)|Agrega un icono a las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::AddImage](#addimage)|Agrega un mapa de bits a las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::CleanUp](#cleanup)||  
|[CMFCToolBarImages::Clear](#clear)|Libera los recursos del sistema que se asignaron a este objeto.|  
|[CMFCToolBarImages::ConvertTo32Bits](#convertto32bits)|Convierte subrayado mapas de bits para imágenes de 32 bpp.|  
|[CMFCToolBarImages::CopyImageToClipboard](#copyimagetoclipboard)||  
|[CMFCToolBarImages::CopyTo](#copyto)||  
|[CMFCToolBarImages::CreateFromImageList](#createfromimagelist)|Inicializa las imágenes de la barra de herramientas de una lista de imágenes ( [CImageList (clase)](../../mfc/reference/cimagelist-class.md)).|  
|[CMFCToolBarImages::CreateRegionFromImage](#createregionfromimage)||  
|[CMFCToolBarImages::DeleteImage](#deleteimage)|Elimina la imagen que tiene un índice especificado de las imágenes de la barra de herramientas si este conjunto de imágenes de la barra de herramientas contiene imágenes definidas por el usuario.|  
|[CMFCToolBarImages::Draw](#draw)|Dibuja una imagen única de la barra de herramientas (botón).|  
|[CMFCToolBarImages::DrawEx](#drawex)||  
|[CMFCToolBarImages::EnableRTL](#enablertl)||  
|[CMFCToolBarImages::EndDrawImage](#enddrawimage)|Libera los recursos del sistema cuando se dibuja una imagen de la barra de herramientas.|  
|[CMFCToolBarImages::ExtractIcon](#extracticon)|Devuelve el icono que tiene un índice de imagen especificados de las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::FillDitheredRect](#fillditheredrect)|Rellena un rectángulo utilizando un pincel con los colores de fondo de la barra de herramientas.|  
|[CMFCToolBarImages::GetAlwaysLight](#getalwayslight)||  
|[CMFCToolBarImages::GetBitsPerPixel](#getbitsperpixel)|Devuelve la resolución actual de imágenes de subrayado.|  
|[CMFCToolBarImages::GetCount](#getcount)|Devuelve el número de imágenes en la barra de herramientas.|  
|[CMFCToolBarImages::GetDisabledImageAlpha](#getdisabledimagealpha)|Devuelve el valor de canal alfa que se usa para imágenes deshabilitadas.|  
|[CMFCToolBarImages::GetFadedImageAlpha](#getfadedimagealpha)||  
|[CMFCToolBarImages::GetImageSize](#getimagesize)|Recupera el tamaño de las imágenes de la barra de herramientas que se almacenan en memoria (tamaño de fuente) o el tamaño de las imágenes de la barra de herramientas que se dibujan en la pantalla (tamaño de destino).|  
|[CMFCToolBarImages::GetImageWell](#getimagewell)|Devuelve el identificador del mapa de bits que contiene todas las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::GetImageWellLight](#getimagewelllight)||  
|[CMFCToolBarImages::GetLastImageRect](#getlastimagerect)||  
|[CMFCToolBarImages::GetLightPercentage](#getlightpercentage)||  
|[CMFCToolBarImages::GetMapTo3DColors](#getmapto3dcolors)||  
|[CMFCToolBarImages::GetMask](#getmask)||  
|[CMFCToolBarImages::GetResourceOffset](#getresourceoffset)|Devuelve el índice de imagen para un identificador de recurso especificado.|  
|[CMFCToolBarImages::GetScale](#getscale)|Devuelve la relación de escala actual de imágenes subrayadas.|  
|[CMFCToolBarImages::GetTransparentColor](#gettransparentcolor)||  
|[CMFCToolBarImages::GrayImages](#grayimages)|Atenúa las imágenes de la barra de herramientas para que su aspecto deshabilitado.|  
|[CMFCToolBarImages::Is32BitTransparencySupported](#is32bittransparencysupported)|Determina si el sistema operativo admite la combinación alfa de 32 bits.|  
|[CMFCToolBarImages::IsPreMultiplyAutoCheck](#ispremultiplyautocheck)||  
|[CMFCToolBarImages::IsRTL](#isrtl)|Determina si está habilitada la compatibilidad de derecha a izquierda (RTL).|  
|[CMFCToolBarImages::IsReadOnly](#isreadonly)|Determina si las imágenes de la barra de herramientas son de sólo lectura.|  
|[CMFCToolBarImages::IsScaled](#isscaled)|Indica si se escalan las imágenes de subrayado o no.|  
|[CMFCToolBarImages::IsUserImagesList](#isuserimageslist)|Determina si este conjunto de imágenes de la barra de herramientas contiene imágenes definidas por el usuario.|  
|[CMFCToolBarImages::IsValid](#isvalid)|Determina si este conjunto de imágenes de la barra de herramientas contiene una imagen válida de la barra de herramientas.|  
|[CMFCToolBarImages::Load](#load)|Carga las imágenes de la barra de herramientas de recursos del sistema o desde un archivo.|  
|[CMFCToolBarImages::LoadStr](#loadstr)||  
|[CMFCToolBarImages::MapFromSysColor](#mapfromsyscolor)||  
|[CMFCToolBarImages::MapTo3dColors](#mapto3dcolors)||  
|[CMFCToolBarImages::MapToSysColor](#maptosyscolor)||  
|[CMFCToolBarImages::MapToSysColorAlpha](#maptosyscoloralpha)||  
|[CMFCToolBarImages::Mirror](#mirror)|Horizontalmente refleja todas las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::MirrorBitmap](#mirrorbitmap)|Horizontalmente refleja un mapa de bits.|  
|[CMFCToolBarImages::MirrorBitmapVert](#mirrorbitmapvert)||  
|[CMFCToolBarImages::MirrorVert](#mirrorvert)||  
|[CMFCToolBarImages::OnSysColorChange](#onsyscolorchange)||  
|[CMFCToolBarImages::PrepareDrawImage](#preparedrawimage)|Asigna los recursos necesarios para dibujar una imagen de la barra de herramientas a un tamaño especificado.|  
|[CMFCToolBarImages::Save](#save)|Almacena las imágenes de la barra de herramientas en un archivo si este conjunto de imágenes de la barra de herramientas contiene imágenes definidas por el usuario.|  
|[CMFCToolBarImages::SetAlwaysLight](#setalwayslight)||  
|[CMFCToolBarImages::SetDisabledImageAlpha](#setdisabledimagealpha)|Establece el valor de canal alfa que se usa para imágenes deshabilitadas.|  
|[CMFCToolBarImages::SetFadedImageAlpha](#setfadedimagealpha)||  
|[CMFCToolBarImages::SetImageSize](#setimagesize)|Establece el tamaño de una imagen de la barra de herramientas (tamaño de fuente).|  
|[CMFCToolBarImages::SetLightPercentage](#setlightpercentage)||  
|[CMFCToolBarImages::SetMapTo3DColors](#setmapto3dcolors)||  
|[CMFCToolBarImages::SetPreMultiplyAutoCheck](#setpremultiplyautocheck)||  
|[CMFCToolBarImages::SetSingleImage](#setsingleimage)||  
|[CMFCToolBarImages::SetTransparentColor](#settransparentcolor)|Establece el color transparente de las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::SmoothResize](#smoothresize)|Cambia suavemente imágenes subrayadas.|  
|[CMFCToolBarImages::UpdateImage](#updateimage)|Actualiza una imagen de la barra de herramientas definidas por el usuario de un mapa de bits.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarImages::PreMultiplyAlpha](#premultiplyalpha)||  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCToolBarImages::m_bDisableTrueColorAlpha](#m_bdisabletruecoloralpha)|`TRUE`Si se deshabilita la combinación (color de&32; bits) de alfa de color verdadero.|  
  
## <a name="remarks"></a>Comentarios  
 El mapa de bits completo de imágenes de la barra de herramientas administrada por `CMFCToolbarImages` consta de una o más imágenes pequeñas de la barra de herramientas (botones) de un tamaño fijo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar un `CMFCToolBarImages` objeto utilizando varios métodos en la `CMFCToolBarImages` clase. En el ejemplo se muestra cómo establecer el tamaño de la imagen de la barra de herramientas, cargar una imagen y establecer el color transparente de la imagen. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#32;](../../mfc/codesnippet/cpp/cmfctoolbarimages-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo Nº&33;](../../mfc/codesnippet/cpp/cmfctoolbarimages-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCToolBarImages`   
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbarimages.h  
  
##  <a name="adaptcolors"></a>CMFCToolBarImages::AdaptColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void AdaptColors(
    COLORREF clrBase,  
    COLORREF clrTone);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `clrBase`  
 [in] `clrTone`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="addicon"></a>CMFCToolBarImages::AddIcon  
 Agrega un icono a la lista de imágenes de la barra de herramientas.  
  
```  
int AddIcon(
    HICON hIcon,  
    BOOL bAlphaBlend=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hIcon`  
 Identificador del icono que se va a agregar.  
  
 [in] `bAlphaBlend`  
 `TRUE`Si este icono se utiliza con mezcla alfa; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la imagen de la barra de herramientas que se agregó si el método es correcto; de lo contrario, devuelve-1.  
  
##  <a name="addimage"></a>CMFCToolBarImages::AddImage  
 Agrega un mapa de bits a las imágenes de la barra de herramientas.  
  
```  
int AddImage(
    HBITMAP hbmp,  
    BOOL bSetBitPerPixel=FALSE);

int AddImage(
    const CMFCToolBarImages& imageList,  
    int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hbmp`  
 El identificador del mapa de bits para agregar.  
  
 [in] `bSetBitPerPixel`  
 `TRUE`Si el `CMFCToolBarImages` objeto utiliza la profundidad de color (bits por píxel) de la nueva imagen. `FALSE` si la `CMFCToolbarImages` objeto mantiene la profundidad de color actual.  
  
 [in] `imageList`  
 Una referencia a un `CMFCToolbarImages` objeto que contiene la imagen para agregar.  
  
 [in] `nIndex`  
 El índice en el origen de `CMFCToolbarImages` objeto de la imagen para agregar.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de la barra de herramientas de imágenes que la `CMFCToolBarImages` objeto mantiene después de que el nuevo mapa de bits se ha agregado correctamente; -1 si la operación ha fallado.  
  
##  <a name="cleanup"></a>CMFCToolBarImages::CleanUp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall CleanUp();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="clear"></a>CMFCToolBarImages::Clear  
 Libera los recursos del sistema que la [CMFCToolbarImages](../../mfc/reference/cmfctoolbarimages-class.md) objeto asignado.  
  
```  
void Clear();
```  
  
##  <a name="cmfctoolbarimages"></a>CMFCToolBarImages::CMFCToolBarImages  
 Construye un objeto `CMFCToolBarImages`.  
  
```  
CMFCToolBarImages();
```  
  
### <a name="remarks"></a>Comentarios  
 Construye un `CMFCToolBarImages` objeto, inicializa su motor de representación y establece el tamaño de la imagen a su valor predeterminado de 16 x 15 píxeles. Utilice [CMFCToolBarImages::SetImageSize](#setimagesize) para cambiar el tamaño de la imagen antes de agregar imágenes.  
  
##  <a name="copyimagetoclipboard"></a>CMFCToolBarImages::CopyImageToClipboard  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyImageToClipboard(int iImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iImage`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="copyto"></a>CMFCToolBarImages::CopyTo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyTo(CMFCToolBarImages& imageList);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `imageList`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="createfromimagelist"></a>CMFCToolBarImages::CreateFromImageList  
 Inicializa las imágenes de la barra de herramientas desde un [CImageList (clase)](../../mfc/reference/cimagelist-class.md) objeto.  
  
```  
BOOL CreateFromImageList(const CImageList& imageList);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `imageList`  
 La lista de imágenes que se usará como origen para imágenes de la barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para inicializar rápidamente la lista de imágenes de la barra de herramientas de una lista de imágenes externas.  
  
##  <a name="createregionfromimage"></a>CMFCToolBarImages::CreateRegionFromImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static HRGN __stdcall CreateRegionFromImage(
    HBITMAP bmp,  
    COLORREF clrTransparent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bmp`  
 [in] `clrTransparent`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="deleteimage"></a>CMFCToolBarImages::DeleteImage  
 Elimina la imagen definida por el usuario que tiene un índice especificado de las imágenes de la barra de herramientas.  
  
```  
BOOL DeleteImage(int iImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iImage`  
 Especifica el índice de base cero de la imagen que desea eliminar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la imagen se ha eliminado correctamente; `FALSE` si el índice de imagen no es válido, el `CMFCToolbarImages` objeto es temporal, la `CMFCToolbarImages` objeto no contiene imágenes definidas por el usuario, o si algún otro error.  
  
##  <a name="draw"></a>CMFCToolBarImages::Draw  
 Dibuja una imagen única de la barra de herramientas.  
  
```  
BOOL Draw(
    CDC* pDC,  
    int x,  
    int y,  
    int iImageIndex,  
    BOOL bHilite=FALSE,  
    BOOL bDisabled=FALSE,  
    BOOL bIndeterminate=FALSE,  
    BOOL bShadow=FALSE,  
    BOOL bInactive=FALSE,  
    BYTE alphaSrc=255);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `x`  
 Coordenada X del lado izquierdo del rectángulo donde está la imagen para dibujar.  
  
 [in] `y`  
 Coordenada Y de la parte superior del rectángulo donde está la imagen para dibujar.  
  
 [in] `iImageIndex`  
 Índice de base cero de la imagen que se mostrará.  
  
 [in] `bHilite`  
 `TRUE`Si la imagen es que se resalte; de lo contrario, `FALSE`.  
  
 [in] `bDisabled`  
 `TRUE`Si es la imagen para dibujar en el estilo deshabilitado; de lo contrario, `FALSE`.  
  
 [in] `bIndeterminate`  
 `TRUE`Si la imagen para dibujar en el estilo de estado indeterminado; de lo contrario, `FALSE`.  
  
 [in] `bShadow`  
 `TRUE`Si la imagen es que se van a dibujar una sombra paralela; de lo contrario, `FALSE`.  
  
 [in] `bInactive`  
 `TRUE`Si la imagen para dibujar en el estilo de estado inactivo; de lo contrario, `FALSE`.  
  
 [in] `alphaSrc`  
 El valor de canal alfa (opacidad). Un valor de 255 significa que la imagen es opaca dibujada. Un valor de 0 significa que la imagen se dibuja transparente. Este valor se utiliza sólo para imágenes de color de 32 bits y para las imágenes que muestra un estilo glass de Windows Vista.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la imagen especificada se mostró correctamente; `FALSE` si el índice de imagen no es válido o algún otro error.  
  
##  <a name="drawex"></a>CMFCToolBarImages::DrawEx  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL DrawEx(
    CDC* pDC,  
    CRect rect,  
    int iImageIndex,  
    ImageAlignHorz horzAlign = ImageAlignHorzLeft,  
    ImageAlignVert vertAlign = ImageAlignVertTop,  
    CRect rectSrc = CRect(0,
    0,
    0,
    0),  
    BYTE alphaSrc = 255);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `iImageIndex`  
 [in] `horzAlign`  
 [in] `vertAlign`  
 [in] `rectSrc`  
 [in] `0`  
 [in] `0)`  
 [in] `alphaSrc`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enablertl"></a>CMFCToolBarImages::EnableRTL  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall EnableRTL(BOOL bIsRTL = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsRTL`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enddrawimage"></a>CMFCToolBarImages::EndDrawImage  
 Libera los recursos del sistema que [CMFCToolBarImages::PrepareDrawImage](#preparedrawimage) asignada después de dibujar una imagen de la barra de herramientas llamando a [CMFCToolBarImages::Draw](#draw).  
  
```  
void EndDrawImage(CAfxDrawState& ds);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ds`  
 Una referencia a la `CAfxDrawState` objeto que se pasó a la `PrepareDrawImage` (método).  
  
##  <a name="extracticon"></a>CMFCToolBarImages::ExtractIcon  
 Devuelve el icono que tiene un índice de imagen especificados de las imágenes de la barra de herramientas.  
  
```  
HICON ExtractIcon(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Índice de base cero en la lista de imágenes en el que se encuentra la imagen que se va a extraer como un icono.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el icono de extraído o `NULL` si `nIndex` está fuera del intervalo.  
  
##  <a name="fillditheredrect"></a>CMFCToolBarImages::FillDitheredRect  
 Rellena un rectángulo con los colores de fondo de la barra de herramientas.  
  
```  
static void FillDitheredRect(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Las coordenadas de un rectángulo que se va a rellenar.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para rellenar un rectángulo con un color que es el promedio de los colores del sistema COLOR_BTNFACE y COLOR_BTNHIGHLIGHT. Si el sistema usa 256 colores o menos, el rectángulo se rellenará con un patrón interpolado de esos dos colores.  
  
##  <a name="getalwayslight"></a>CMFCToolBarImages::GetAlwaysLight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetAlwaysLight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcount"></a>CMFCToolBarImages::GetCount  
 Devuelve el número de imágenes en la lista de imágenes de la barra de herramientas.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de imágenes en el `CMFCToolBarImages` objeto.  
  
##  <a name="getdisabledimagealpha"></a>CMFCToolBarImages::GetDisabledImageAlpha  
 Devuelve el valor de canal alfa (opacidad) que se usa para imágenes deshabilitadas.  
  
```  
static BYTE GetDisabledImageAlpha();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor actual del canal alfa.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a [CMFCToolBarImages::SetDisabledImageAlpha](#setdisabledimagealpha) para cambiar el valor de canal alfa.  
  
##  <a name="getfadedimagealpha"></a>CMFCToolBarImages::GetFadedImageAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BYTE __stdcall GetFadedImageAlpha();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getimagesize"></a>CMFCToolBarImages::GetImageSize  
 Recupera el tamaño de las imágenes de la barra de herramientas que se almacenan en memoria (tamaño de fuente) o el tamaño de las imágenes de la barra de herramientas que se dibujan en la pantalla (tamaño de destino).  
  
```  
SIZE GetImageSize(BOOL bDest=FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDest`  
 `TRUE`para recuperar el tamaño de destino; `FALSE` para recuperar el tamaño de la imagen de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `SIZE` estructura, que especifica el tamaño de una imagen en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de la imagen de origen es el tamaño de las imágenes que se almacenan en la [CMFCToolbarImages](../../mfc/reference/cmfctoolbarimages-class.md) objeto. Puede llamar a [CMFCToolBarImages::SetImageSize](#setimagesize) para establecer el tamaño de fuente. El valor predeterminado es 16 x 15 píxeles.  
  
 De forma predeterminada, el tamaño de la imagen de destino es 0 x 0. Especificar el tamaño de destino cuando se llama a [CMFCToolBarImages::PrepareDrawImage](#preparedrawimage). El [CMFCToolBarImages::EndDrawImage](#enddrawimage) método restablece el tamaño de destino con el valor predeterminado.  
  
##  <a name="getimagewell"></a>CMFCToolBarImages::GetImageWell  
 Devuelve el identificador del mapa de bits que contiene todas las imágenes de la barra de herramientas.  
  
```  
HBITMAP GetImageWell() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de un mapa de bits que contiene las imágenes de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Las imágenes de la barra de herramientas se almacenan en una fila en un único mapa de bits que se conoce como un *imagen bien*. Para buscar una imagen de la barra de herramientas en el cuadro de imagen, multiplique el índice de la imagen por el ancho de las imágenes de la barra de herramientas (consulte [CMFCToolBarImages::GetImageSize](#getimagesize)) para obtener el desplazamiento horizontal de la imagen dentro de la imagen también.  
  
##  <a name="getimagewelllight"></a>CMFCToolBarImages::GetImageWellLight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
HBITMAP GetImageWellLight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getlastimagerect"></a>CMFCToolBarImages::GetLastImageRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetLastImageRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getlightpercentage"></a>CMFCToolBarImages::GetLightPercentage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetLightPercentage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getmapto3dcolors"></a>CMFCToolBarImages::GetMapTo3DColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetMapTo3DColors() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getmask"></a>CMFCToolBarImages::GetMask  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
HBITMAP GetMask(int iImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iImage`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getresourceoffset"></a>CMFCToolBarImages::GetResourceOffset  
 Devuelve el índice de imagen para un identificador de recurso especificado.  
  
```  
int GetResourceOffset(UINT uiResId) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiResId`  
 Un identificador de recurso de imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 Un índice de imagen si el método se realizó correctamente; -1 si la imagen con el identificador de recurso especificado no existe.  
  
##  <a name="gettransparentcolor"></a>CMFCToolBarImages::GetTransparentColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
COLORREF GetTransparentColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="grayimages"></a>CMFCToolBarImages::GrayImages  
 Atenúa las imágenes de la barra de herramientas para que su aspecto deshabilitado.  
  
```  
BOOL GrayImages(int nGrayImageLuminancePercentage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nGrayImageLuminancePercentage`  
 Porcentaje de luminancia.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si las imágenes de la colección se han deshabilitado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método modifica las imágenes de la barra de herramientas al calcular el promedio de los componentes rojos, verde y azules de cada píxel y multiplicando el resultado por `nGrayImageLuminancePercentage` dividido por 100. Si `nGrayImageLuminancePercentage` es cero o negativo, el valor predeterminado de 130 se utiliza en su lugar.  
  
> [!NOTE]
>  Si desea deshacer el cambio, debe volver a cargar las imágenes desde el origen. Puede hacerlo mediante una llamada a [CMFCToolBarImages::Load](#load) o [CMFCToolBarImages::UpdateImage](#updateimage) (sólo para los definidos por el usuario imágenes), o mediante una llamada a [CMFCToolBarImages::Clear](#clear) y agregar las imágenes de nuevo mediante una llamada a [CMFCToolBarImages::AddIcon](#addicon) o [CMFCToolBarImages::AddImage](#addimage).  
  
##  <a name="is32bittransparencysupported"></a>CMFCToolBarImages::Is32BitTransparencySupported  
 Especifica si el sistema operativo admite la combinación alfa de 32 bits.  
  
```  
static BOOL Is32BitTransparencySupported();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se admite la combinación alfa de 32 bits; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método estático para determinar en tiempo de ejecución si el sistema operativo admite la combinación alfa de 32 bits. Esta característica se admite en [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] y versiones posteriores.  
  
##  <a name="ispremultiplyautocheck"></a>CMFCToolBarImages::IsPreMultiplyAutoCheck  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsPreMultiplyAutoCheck() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isreadonly"></a>CMFCToolBarImages::IsReadOnly  
 Especifica si las imágenes de la barra de herramientas son de solo lectura.  
  
```  
BOOL IsReadOnly() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si las imágenes de la barra de herramientas son de solo lectura, de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El `CMFCToolbarImages` objeto es de solo lectura cuando se carga el mapa de bits con imágenes de la barra de herramientas desde un archivo de sólo lectura, o cuando el mapa de bits se copió en el uso de la `CMFCToolBarImages::CopyTemp` (método).  
  
##  <a name="isrtl"></a>CMFCToolBarImages::IsRTL  
 Especifica si está habilitada la compatibilidad de derecha a izquierda (RTL).  
  
```  
static BOOL IsRTL();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la compatibilidad de derecha a izquierda; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Soporte de derecha a izquierda se utiliza cuando la aplicación está localizada en un idioma que se lee de derecha a izquierda, como el árabe, hebreo, persa o Urdu.  
  
##  <a name="isuserimageslist"></a>CMFCToolBarImages::IsUserImagesList  
 Especifica si este conjunto de imágenes de la barra de herramientas contiene imágenes definidas por el usuario.  
  
```  
BOOL IsUserImagesList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el `CMFCToolBarImages` objeto contiene imágenes de la barra de herramientas definidas por el usuario; en caso contrario `FALSE`.  
  
##  <a name="isvalid"></a>CMFCToolBarImages::IsValid  
 Indica si este conjunto de imágenes de la barra de herramientas contiene una imagen válida de la barra de herramientas.  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si un `CMFCToolBarImages` objeto es válido; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El `CMFCToolBarImages` objeto no es válido cuando su identificador a un mapa de bits con imágenes de la barra de herramientas está `NULL`.  
  
##  <a name="load"></a>CMFCToolBarImages::Load  
 Carga las imágenes de la barra de herramientas de recursos del sistema o desde un archivo.  
  
```  
BOOL Load(
    UINT uiResID,  
    HINSTANCE hinstRes=NULL,  
    BOOL bAdd=FALSE);

BOOL Load(
    LPCTSTR lpszBmpFileName,   
    DWORD nMaxFileSize = 819200);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiResID`  
 El identificador de un recurso de mapa de bits.  
  
 [in] `hinstRes`  
 Una instancia de la DLL de recursos.  
  
 [in] `bAdd`  
 `TRUE`Para agregar el mapa de bits cargada en el mapa de bits existente, o `FALSE` para reemplazar el mapa de bits existente.  
  
 [in] `lpszBmpFileName`  
 Una ruta de acceso a un archivo de disco desde donde cargar el mapa de bits.  
  
 [in] `nMaxFileSize`  
 Número máximo de bytes en el archivo de mapa de bits. o 0 para cargar el mapa de bits, independientemente del tamaño del archivo. Si el tamaño del archivo supera este tamaño máximo, el método devuelve `FALSE` y no se carga el mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el mapa de bits se ha cargado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si el archivo tiene el atributo de sólo lectura, la lista de imágenes está marcada como de sólo lectura.  
  
##  <a name="loadstr"></a>CMFCToolBarImages::LoadStr  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL LoadStr(
    LPCTSTR lpszResourceName,  
    HINSTANCE hinstRes = NULL,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszResourceName`  
 [in] `hinstRes`  
 [in] `bAdd`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="mapfromsyscolor"></a>CMFCToolBarImages::MapFromSysColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static COLORREF __stdcall MapFromSysColor(
    COLORREF color,  
    BOOL bUseRGBQUAD = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 [in] `bUseRGBQUAD`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="mapto3dcolors"></a>CMFCToolBarImages::MapTo3dColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL MapTo3dColors(
    BOOL bUseRGBQUAD = TRUE,  
    COLORREF clrSrc = (COLORREF)-1,  
    COLORREF clrDest = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bUseRGBQUAD`  
 [in] `clrSrc`  
 [in] `clrDest`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="maptosyscolor"></a>CMFCToolBarImages::MapToSysColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static COLORREF __stdcall MapToSysColor(
    COLORREF color,  
    BOOL bUseRGBQUAD = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 [in] `bUseRGBQUAD`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="maptosyscoloralpha"></a>CMFCToolBarImages::MapToSysColorAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static COLORREF __stdcall MapToSysColorAlpha(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="mirror"></a>CMFCToolBarImages::Mirror  
 Reemplaza las imágenes de la barra de herramientas con su imagen reflejada horizontal.  
  
```  
BOOL Mirror();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si las imágenes se ha reflejado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método se usa para admitir sistemas de escritura de derecha a izquierda.  
  
##  <a name="mirrorbitmap"></a>CMFCToolBarImages::MirrorBitmap  
 Reemplaza un mapa de bits con su imagen reflejada horizontal.  
  
```  
static BOOL MirrorBitmap(
    HBITMAP& hbmp,  
    int cxImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `hbmp`  
 Identificador de mapa de bits para reflejar.  
  
 [in] `cxImage`  
 Ancho de la imagen en píxeles.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la imagen se ha reflejado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para admitir los sistemas de escritura de derecha a izquierda.  
  
##  <a name="mirrorbitmapvert"></a>CMFCToolBarImages::MirrorBitmapVert  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall MirrorBitmapVert(
    HBITMAP& hbmp,  
    int cyImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hbmp`  
 [in] `cyImage`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="mirrorvert"></a>CMFCToolBarImages::MirrorVert  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL MirrorVert();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsyscolorchange"></a>CMFCToolBarImages::OnSysColorChange  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void OnSysColorChange();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="premultiplyalpha"></a>CMFCToolBarImages::PreMultiplyAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall PreMultiplyAlpha(
    HBITMAP hbmp,  
    BOOL bAutoCheckPremlt);

BOOL PreMultiplyAlpha(HBITMAP hbmp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hbmp`  
 [in] `bAutoCheckPremlt`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_bdisabletruecoloralpha"></a>CMFCToolBarImages::m_bDisableTrueColorAlpha  
 `TRUE`Si se deshabilita la combinación (color de&32; bits) de alfa de color verdadero.  
  
```  
static BOOL m_bDisableTrueColorAlpha;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer esta variable miembro en `FALSE` para habilitar la combinación alfa para las imágenes de la barra de herramientas de color verdadero.  
  
 El valor predeterminado es `TRUE` para compatibilidad con versiones anteriores.  
  
##  <a name="preparedrawimage"></a>CMFCToolBarImages::PrepareDrawImage  
 Asigna los recursos necesarios para dibujar una imagen de la barra de herramientas a un tamaño especificado.  
  
```  
BOOL PrepareDrawImage(
    CAfxDrawState& ds,  
    CSize sizeImageDest=CSize(0,
    0)  
    BOOL bFadeInactive=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ds`  
 Una referencia a `CAfxDrawState` estructura, que almacena los recursos asignados entre las fases de procesamiento de imagen.  
  
 [in] `sizeImageDest`  
 Especifica el tamaño de una imagen de destino.  
  
 [in] `bFadeInactive`  
 `TRUE`Si desea inactiva imágenes se dibujan atenuado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si los recursos necesarios para dibujar la imagen de la barra de herramientas se han asignado correctamente, de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a este método, se puede llamar a [CMFCToolBarImages::Draw](#draw) cualquier número de veces. Una vez finalizado el dibujo, debe llamar a [CMFCToolBarImages::EndDrawImage](#enddrawimage) para liberar los recursos asignados por `PrepareDrawImage`.  
  
##  <a name="save"></a>CMFCToolBarImages::Save  
 Almacena las imágenes de la barra de herramientas en un archivo si este conjunto de imágenes de la barra de herramientas contiene imágenes definidas por el usuario.  
  
```  
BOOL Save(LPCTSTR lpszBmpFileName=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszBmpFileName`  
 Ruta de acceso a un archivo de disco.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si las imágenes de la barra de herramientas se guardaron correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para almacenar las imágenes definidas por el usuario en un archivo de disco. Si `lpszBmpFileName` es `NULL`, el método almacena el mapa de bits en el archivo desde el que se cargó el mapa de bits mediante el [CMFCToolBarImages::Load](#load) método.  
  
##  <a name="setalwayslight"></a>CMFCToolBarImages::SetAlwaysLight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetAlwaysLight(BOOL bAlwaysLight = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAlwaysLight`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setdisabledimagealpha"></a>CMFCToolBarImages::SetDisabledImageAlpha  
 Establece el valor de canal alfa (opacidad) que se usa para imágenes deshabilitadas.  
  
```  
static void SetDisabledImageAlpha(BYTE nValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nValue`  
 El nuevo valor del canal alfa.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para establecer un valor alfa personalizado para las imágenes deshabilitados. El valor predeterminado es 127, lo que hace que las imágenes de botón deshabilitado en semitransparentes. Si establece un valor de 0, imágenes deshabilitadas será completamente transparentes. Si establece un valor de 255, imágenes deshabilitadas será completamente opacas.  
  
##  <a name="setfadedimagealpha"></a>CMFCToolBarImages::SetFadedImageAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall SetFadedImageAlpha(BYTE nValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nValue`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setimagesize"></a>CMFCToolBarImages::SetImageSize  
 Establece el tamaño de cada imagen de la barra de herramientas (tamaño de fuente).  
  
```  
void SetImageSize(
    SIZE sizeImage,  
    BOOL bUpdateCount=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `sizeImage`  
 El nuevo tamaño de imágenes de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el tamaño de la imagen de la barra de herramientas es 16 x 15 píxeles. Llamar a este método si desea utilizar imágenes de la barra de herramientas de un tamaño diferente.  
  
##  <a name="setlightpercentage"></a>CMFCToolBarImages::SetLightPercentage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetLightPercentage(int nValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nValue`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setmapto3dcolors"></a>CMFCToolBarImages::SetMapTo3DColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetMapTo3DColors(BOOL bMapTo3DColors);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMapTo3DColors`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setpremultiplyautocheck"></a>CMFCToolBarImages::SetPreMultiplyAutoCheck  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetPreMultiplyAutoCheck(BOOL bAuto = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAuto`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setsingleimage"></a>CMFCToolBarImages::SetSingleImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetSingleImage();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settransparentcolor"></a>CMFCToolBarImages::SetTransparentColor  
 Establece el color transparente de las imágenes de la barra de herramientas.  
  
```  
COLORREF SetTransparentColor(COLORREF clrTransparent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `clrTransparent`  
 Un valor RGB.  
  
### <a name="return-value"></a>Valor devuelto  
 El color transparente de la anterior.  
  
### <a name="remarks"></a>Comentarios  
 Cuando usted o el marco de trabajo llama a [CMFCToolBarImages::Draw](#draw), el método no dibuja cualquier píxel que coincida con el color especificado por `clrTransparent`.  
  
##  <a name="updateimage"></a>CMFCToolBarImages::UpdateImage  
 Actualiza una imagen de la barra de herramientas definidas por el usuario de un mapa de bits.  
  
```  
BOOL UpdateImage(
    int iImage,  
    HBITMAP hbmp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iImage`  
 Índice de base cero de la imagen para la actualización.  
  
 [in] `hbmp`  
 Identificador del mapa de bits desde el que se va a actualizar la imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la imagen se ha actualizado correctamente; `FALSE` si la lista de imágenes no está definido por el usuario o temporales.  
  
##  <a name="convertto32bits"></a>CMFCToolBarImages::ConvertTo32Bits  
 Convierte subrayado mapas de bits para imágenes de 32 bpp.  
  
```  
BOOL ConvertTo32Bits(COLORREF clrTransparent = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 `clrTransparent`  
 Especifica el color transparente de mapas de bits subrayado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getbitsperpixel"></a>CMFCToolBarImages::GetBitsPerPixel  
 Devuelve la resolución actual de imágenes de subrayado.  
  
```  
int GetBitsPerPixel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor entero que representa la resolución actual de imágenes de subrayado, en bits por píxel (bpp).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getscale"></a>CMFCToolBarImages::GetScale  
 Devuelve la relación de escala actual de imágenes de subrayado.  
  
```  
double GetScale() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que representa la relación de escala actual.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isscaled"></a>CMFCToolBarImages::IsScaled  
 Indica si se escalan las imágenes de subrayado o no.  
  
```  
BOOL IsScaled () const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se escalan las imágenes subrayadas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="smoothresize"></a>CMFCToolBarImages::SmoothResize  
 Cambia suavemente imágenes subrayadas.  
  
```  
BOOL SmoothResize(double dblImageScale);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblImageScale`  
 Relación de escala.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se realiza correctamente el cambio de tamaño; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

