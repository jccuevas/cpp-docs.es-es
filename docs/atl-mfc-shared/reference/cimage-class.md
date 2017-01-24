---
title: "CImage Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CImage"
  - "ATL.CImage"
  - "ATL::CImage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".gif (archivos), ATL and MFC support"
  - "mapas de bits [C++], ATL and MFC support for"
  - "CImage class"
  - "gif (archivos), ATL and MFC support"
  - "imágenes [C++], ATL and MFC support for"
  - "jpeg (archivos)"
  - "PNG (archivos), ATL and MFC support"
  - "transparent color"
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
caps.latest.revision: 20
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CImage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CImage` proporciona compatibilidad mejorada del mapa de bits, incluida la capacidad de cargar y guardar imágenes en JPEG, GIF, BMP, y los formatos de \(PNG\) de gráficos de red de Portable.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CImage  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImage::CImage](../Topic/CImage::CImage.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImage::AlphaBlend](../Topic/CImage::AlphaBlend.md)|Muestra los mapas de bits que tienen píxeles transparentes o semitransparentes.|  
|[CImage::Attach](../Topic/CImage::Attach.md)|Asocia `HBITMAP` a un objeto de `CImage` .  Se puede utilizar con los mapas de bits de mapas de bits de la sección de no DIB o la sección DIB.|  
|[CImage::BitBlt](../Topic/CImage::BitBlt.md)|Copia un mapa de bits de contexto del dispositivo de origen a este contexto actual del dispositivo.|  
|[CImage::Create](../Topic/CImage::Create.md)|Crea un mapa de bits de la sección del archivo DIB y lo asocia al objeto previamente construido de `CImage` .|  
|[CImage::CreateEx](../Topic/CImage::CreateEx.md)|Crea un mapa de bits de la sección del archivo DIB \(con parámetros adicionales\) y lo asocia al objeto previamente construido de `CImage` .|  
|[CImage::Destroy](../Topic/CImage::Destroy.md)|Desasocia el mapa de bits del objeto de `CImage` y destruye el mapa de bits.|  
|[CImage::Detach](../Topic/CImage::Detach.md)|Desasocia el mapa de bits de un objeto de `CImage` .|  
|[CImage::Draw](../Topic/CImage::Draw.md)|Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino.  **Dibujo** ajusta o comprime el mapa de bits para ajustarse las dimensiones del rectángulo de destino en caso necesario, y controlar la mezcla alfa y colores transparentes.|  
|[CImage::GetBits](../Topic/CImage::GetBits.md)|Recupera un puntero a los valores de píxel de mapa de bits.|  
|[CImage::GetBPP](../Topic/CImage::GetBPP.md)|Recupera los bits por píxel.|  
|[CImage::GetColorTable](../Topic/CImage::GetColorTable.md)|Recupera el rojo, verde, valores de color azul de \(RGB\) de un intervalo de entradas en la paleta de colores.|  
|[CImage::GetDC](../Topic/CImage::GetDC.md)|Recupera el contexto de dispositivo en el que se selecciona el mapa de bits actual.|  
|[CImage::GetExporterFilterString](../Topic/CImage::GetExporterFilterString.md)|Busque los formatos de imágenes disponibles y sus descripciones.|  
|[CImage::GetHeight](../Topic/CImage::GetHeight.md)|Recupera el alto de la imagen actual en píxeles.|  
|[CImage::GetImporterFilterString](../Topic/CImage::GetImporterFilterString.md)|Busque los formatos de imágenes disponibles y sus descripciones.|  
|[CImage::GetMaxColorTableEntries](../Topic/CImage::GetMaxColorTableEntries.md)|Recupera el número máximo de entradas en la paleta de colores.|  
|[CImage::GetPitch](../Topic/CImage::GetPitch.md)|Recupera el paso de la imagen actual, en bytes.|  
|[CImage::GetPixel](../Topic/CImage::GetPixel.md)|Recupera color de píxel especificado *x* e y *.*|  
|[CImage::GetPixelAddress](../Topic/CImage::GetPixelAddress.md)|Recupera la dirección de un píxel determinado.|  
|[CImage::GetTransparentColor](../Topic/CImage::GetTransparentColor.md)|Recupera la posición del color transparente en la paleta de colores.|  
|[CImage::GetWidth](../Topic/CImage::GetWidth.md)|Recupera el ancho de la imagen actual en píxeles.|  
|[CImage::IsDIBSection](../Topic/CImage::IsDIBSection.md)|Determina si el mapa de bits asociado es una sección DIB.|  
|[CImage::IsIndexed](../Topic/CImage::IsIndexed.md)|Indica que los colores de un mapa de bits están asignados a una paleta indizada.|  
|[CImage::IsNull](../Topic/CImage::IsNull.md)|Indica si un mapa de bits de origen está cargado actualmente.|  
|[CImage::IsTransparencySupported](../Topic/CImage::IsTransparencySupported.md)|Indica si la aplicación admite mapas de bits transparentes y fue compilado para Windows 2000 o posterior.|  
|[CImage::Load](../Topic/CImage::Load.md)|Carga una imagen del archivo especificado.|  
|[CImage::LoadFromResource](../Topic/CImage::LoadFromResource.md)|Carga una imagen de recursos especificado.|  
|[CImage::MaskBlt](../Topic/CImage::MaskBlt.md)|Combina los datos de color de mapas de bits de origen y de destino utilizando la operación especificada de máscara y la trama.|  
|[CImage::PlgBlt](../Topic/CImage::PlgBlt.md)|Realiza una transferencia de bloque de bits de un rectángulo en un contexto del dispositivo de origen en un paralelogramo en un contexto del dispositivo de destino.|  
|[CImage::ReleaseDC](../Topic/CImage::ReleaseDC.md)|Libera el contexto del dispositivo que se ha recuperado con [CImage::GetDC](../Topic/CImage::GetDC.md).|  
|[CImage::ReleaseGDIPlus](../Topic/CImage::ReleaseGDIPlus.md)|Libera los recursos utilizados por GDI\+.  Debe llamar a para liberar los recursos creados por un objeto de `CImage` .|  
|[CImage::Save](../Topic/CImage::Save.md)|Guarda una imagen como el tipo especificado.  **Guardar** no puede especificar opciones de la imagen.|  
|[CImage::SetColorTable](../Topic/CImage::SetColorTable.md)|Establece rojo, verde, los valores de color azul RGB\) de un intervalo de entradas en la tabla de colores de la sección DIB.|  
|[CImage::SetPixel](../Topic/CImage::SetPixel.md)|Establece el píxel en las coordenadas especificadas al color especificado.|  
|[CImage::SetPixelIndexed](../Topic/CImage::SetPixelIndexed.md)|Establece el píxel en las coordenadas especificadas al color en el índice especificado de la paleta.|  
|[CImage::SetPixelRGB](../Topic/CImage::SetPixelRGB.md)|Establece el píxel en las coordenadas especificadas en rojo especificado, verde, azul valor de \(RGB\).|  
|[CImage::SetTransparentColor](../Topic/CImage::SetTransparentColor.md)|Establece el índice del color que se tratará como transparente.  Sólo un color de una paleta puede ser transparente.|  
|[CImage::StretchBlt](../Topic/CImage::StretchBlt.md)|Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino, estirando o comprima el mapa de bits para ajustarse las dimensiones del rectángulo de destino, en caso necesario.|  
|[CImage::TransparentBlt](../Topic/CImage::TransparentBlt.md)|Copia un mapa de bits con un color transparente de contexto del dispositivo de origen a este contexto actual del dispositivo.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImage::operator HBITMAP](../Topic/CImage::operator%20HBITMAP.md)|Devuelve el identificador de Windows asociado al objeto de `CImage` .|  
  
## Comentarios  
 `CImage` toma los mapas de bits que son secciones de \(DIB\) de mapa de bits independiente del dispositivo o no; sin embargo, puede utilizar [cree](../Topic/CImage::Create.md) o [CImage::Load](../Topic/CImage::Load.md) con sólo las secciones del archivo DIB.  Puede adjuntar un mapa de bits de la sección de no DIB a un objeto de `CImage` mediante [Asociar](../Topic/CImage::Attach.md), pero después no puede utilizar los siguientes métodos de `CImage` , que solo admiten mapas de bits de la sección del archivo DIB:  
  
-   [GetBits](../Topic/CImage::GetBits.md)  
  
-   [GetColorTable](../Topic/CImage::GetColorTable.md)  
  
-   [GetMaxColorTableEntries](../Topic/CImage::GetMaxColorTableEntries.md)  
  
-   [GetPitch](../Topic/CImage::GetPitch.md)  
  
-   [GetPixelAddress](../Topic/CImage::GetPixelAddress.md)  
  
-   [IsIndexed](../Topic/CImage::IsIndexed.md)  
  
-   [SetColorTable](../Topic/CImage::SetColorTable.md)  
  
 Para determinar si un mapa de bits asociado es una sección del archivo DIB, llame a [IsDibSection](../Topic/CImage::IsDIBSection.md)**.**  
  
> [!NOTE]
>  **Note** en Visual Studio .NET 2003, esta clase mantiene un recuento del número de objetos de `CImage` creado.  Siempre que el recuento vaya a 0, la función [GdiplusShutdown](_gdiplus_func_gdiplusshutdown_) automáticamente se denomina para liberar los recursos utilizados por GDI\+.  Esto asegura que cualquier objeto de `CImage` creado directa o indirectamente por los archivos DLL se destruirá siempre correctamente y que **GdiplusShutdown** no se llama de `DllMain`.  
  
> [!NOTE]
>  Mediante `CImage` global los objetos de DLL no se recomienda.  Si necesita utilizar un objeto de `CImage` en un archivo DLL, la llamada [CImage:: ReleaseGDIPlus](../Topic/CImage::ReleaseGDIPlus.md) explícitamente para liberar los recursos utilizados por GDI\+.  
  
 `CImage` no se puede seleccionar en el nuevo [CDC](../../mfc/reference/cdc-class.md).  `CImage` crea su propio **HDC** para la imagen.  Dado que `HBITMAP` puede seleccionarse solo en un **HDC** al mismo tiempo, `HBITMAP` asociado a `CImage` no puede seleccionarse en otro **HDC**.  Si necesita `CDC`, recupere **HDC** de `CImage` y darle a [CDC::FromHandle](../Topic/CDC::FromHandle.md).  
  
## Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#70](../../atl-mfc-shared/codesnippet/CPP/cimage-class_1.cpp)]  
  
 Cuando se utiliza `CImage` en un proyecto MFC, la nota que las funciones miembro del proyecto espera recibir un puntero a un objeto de [CBitmap](../../mfc/reference/cbitmap-class.md) .  Si desea utilizar `CImage` con esta función, como [CMenu::AppendMenu](../Topic/CMenu::AppendMenu.md), el uso [CBitmap::FromHandle](../Topic/CBitmap::FromHandle.md), para pasar el `CImage``HBITMAP`, y utilizar `CBitmap*`devuelto.  
  
## Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#71](../../atl-mfc-shared/codesnippet/CPP/cimage-class_2.cpp)]  
  
 Con `CImage`, tiene acceso a los bits reales de una sección DIB.  Puede utilizar un objeto de `CImage` dondequiera que utilizó anteriormente HBITMAP de Win32 o la sección DIB.  
  
> [!NOTE]
>  Los siguientes métodos de `CImage` tienen limitaciones en el uso:  
  
|Método|Limitación|  
|------------|----------------|  
|[PlgBlt](../Topic/CImage::PlgBlt.md)|Trabajos sólo con Windows NT 4.0 o posterior.  No funcionará en aplicaciones ejecutándose en Windows 95 \/98 o posterior.|  
|[MaskBlt](../Topic/CImage::MaskBlt.md)|Trabajos sólo con Windows NT 4.0 o posterior.  No funcionará en aplicaciones ejecutándose en Windows 95 \/98 o posterior.|  
|[AlphaBlend](../Topic/CImage::AlphaBlend.md)|Trabajos sólo con Windows 2000, Windows 98, y sistemas posteriores.|  
|[TransparentBlt](../Topic/CImage::TransparentBlt.md)|Trabajos sólo con Windows 2000, Windows 98, y sistemas posteriores.|  
|[Dibujo](../Topic/CImage::Draw.md)|Admite la transparencia solo con Windows 2000, Windows 98, y sistemas posteriores.|  
  
 Vea [CImage Limitaciones con sistemas operativos anteriores](../../mfc/cimage-limitations-with-earlier-operating-systems.md) para obtener información detallada sobre las limitaciones de estos métodos.  
  
 Puede utilizar `CImage` MFC o ATL.  
  
> [!NOTE]
>  Cuando se crea un proyecto mediante `CImage`, debe definir `CString` antes de que incluye `atlimage.h`.  Si el proyecto usa ATL sin MFC, incluyen `atlstr.h` antes de que incluye `atlimage.h`.  Si el proyecto utiliza MFC \(o si es un proyecto ATL con compatibilidad con MFC\), incluya `afxstr.h` antes de que incluye `atlimage.h`.  
>   
>  Igualmente, debe incluir `atlimage.h` antes de que incluye `atlimpl.cpp`.  Para realizarlo fácilmente, incluya `atlimage.h` en su `stdafx.h`.  
  
## Requisitos  
 **Header:** atlimage.h  
  
## Vea también  
 [Ejemplo MMXSwarm](../../top/visual-cpp-samples.md)   
 [Ejemplo SimpleImage](../../top/visual-cpp-samples.md)   
 [Device\-Independent Bitmaps](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)