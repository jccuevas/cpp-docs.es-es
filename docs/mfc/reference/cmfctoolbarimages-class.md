---
title: "CMFCToolBarImages Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarImages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarImages class"
ms.assetid: d4e50518-9ffc-406f-9996-f79e5cd38155
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCToolBarImages Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las imágenes de una barra de herramientas.  La clase de `CMFCToolBarImages` administra las imágenes de la barra de herramientas cargan de recursos de la aplicación o archivos.  
  
## Sintaxis  
  
```  
class CMFCToolBarImages : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarImages::CMFCToolBarImages](../Topic/CMFCToolBarImages::CMFCToolBarImages.md)|Crea un objeto `CMFCToolBarImages`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarImages::AdaptColors](../Topic/CMFCToolBarImages::AdaptColors.md)||  
|[CMFCToolBarImages::AddIcon](../Topic/CMFCToolBarImages::AddIcon.md)|agrega un icono a las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::AddImage](../Topic/CMFCToolBarImages::AddImage.md)|agrega un mapa de bits a las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::CleanUp](../Topic/CMFCToolBarImages::CleanUp.md)||  
|[CMFCToolBarImages::Clear](../Topic/CMFCToolBarImages::Clear.md)|Libera los recursos del sistema asignados a este objeto.|  
|[CMFCToolBarImages::ConvertTo32Bits](../Topic/CMFCToolBarImages::ConvertTo32Bits.md)|Convierte mapas de bits subrayado a 32 imágenes de bpp.|  
|[CMFCToolBarImages::CopyImageToClipboard](../Topic/CMFCToolBarImages::CopyImageToClipboard.md)||  
|[CMFCToolBarImages::CopyTo](../Topic/CMFCToolBarImages::CopyTo.md)||  
|[CMFCToolBarImages::CreateFromImageList](../Topic/CMFCToolBarImages::CreateFromImageList.md)|Inicialice las imágenes de la barra de herramientas de una imagen \([CImageList Class](../../mfc/reference/cimagelist-class.md)\).|  
|[CMFCToolBarImages::CreateRegionFromImage](../Topic/CMFCToolBarImages::CreateRegionFromImage.md)||  
|[CMFCToolBarImages::DeleteImage](../Topic/CMFCToolBarImages::DeleteImage.md)|elimina la imagen que tiene un índice especificado de las imágenes de la barra de herramientas si este conjunto de imágenes de la barra de herramientas contiene imágenes definido por el usuario.|  
|[CMFCToolBarImages::Draw](../Topic/CMFCToolBarImages::Draw.md)|Dibuja una imagen única de la barra de herramientas \(botón\).|  
|[CMFCToolBarImages::DrawEx](../Topic/CMFCToolBarImages::DrawEx.md)||  
|[CMFCToolBarImages::EnableRTL](../Topic/CMFCToolBarImages::EnableRTL.md)||  
|[CMFCToolBarImages::EndDrawImage](../Topic/CMFCToolBarImages::EndDrawImage.md)|Libera los recursos del sistema después de dibujar una imagen de la barra de herramientas.|  
|[CMFCToolBarImages::ExtractIcon](../Topic/CMFCToolBarImages::ExtractIcon.md)|devuelve el icono que tiene un índice especificado de la imagen de las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::FillDitheredRect](../Topic/CMFCToolBarImages::FillDitheredRect.md)|Rellena un rectángulo con un pincel con los colores de fondo de la barra de herramientas.|  
|[CMFCToolBarImages::GetAlwaysLight](../Topic/CMFCToolBarImages::GetAlwaysLight.md)||  
|[CMFCToolBarImages::GetBitsPerPixel](../Topic/CMFCToolBarImages::GetBitsPerPixel.md)|devuelve la resolución actual de imágenes subrayadas.|  
|[CMFCToolBarImages::GetCount](../Topic/CMFCToolBarImages::GetCount.md)|devuelve el número de imágenes en la barra de herramientas.|  
|[CMFCToolBarImages::GetDisabledImageAlpha](../Topic/CMFCToolBarImages::GetDisabledImageAlpha.md)|Devuelve el valor de canal alfa que se utiliza para las imágenes deshabilitadas.|  
|[CMFCToolBarImages::GetFadedImageAlpha](../Topic/CMFCToolBarImages::GetFadedImageAlpha.md)||  
|[CMFCToolBarImages::GetImageSize](../Topic/CMFCToolBarImages::GetImageSize.md)|Recupera el tamaño de las imágenes de la barra de herramientas que se almacenan en memoria \(tamaño de origen\), o el tamaño de las imágenes de la barra de herramientas que se dibujan en la presentación \(tamaño de destino\).|  
|[CMFCToolBarImages::GetImageWell](../Topic/CMFCToolBarImages::GetImageWell.md)|Devuelve el identificador del mapa de bits que contiene todas las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::GetImageWellLight](../Topic/CMFCToolBarImages::GetImageWellLight.md)||  
|[CMFCToolBarImages::GetLastImageRect](../Topic/CMFCToolBarImages::GetLastImageRect.md)||  
|[CMFCToolBarImages::GetLightPercentage](../Topic/CMFCToolBarImages::GetLightPercentage.md)||  
|[CMFCToolBarImages::GetMapTo3DColors](../Topic/CMFCToolBarImages::GetMapTo3DColors.md)||  
|[CMFCToolBarImages::GetMask](../Topic/CMFCToolBarImages::GetMask.md)||  
|[CMFCToolBarImages::GetResourceOffset](../Topic/CMFCToolBarImages::GetResourceOffset.md)|Devuelve el índice de la imagen para un identificador especificada de recursos|  
|[CMFCToolBarImages::GetScale](../Topic/CMFCToolBarImages::GetScale.md)|Devuelve la proporción actual de escala de imágenes subrayadas.|  
|[CMFCToolBarImages::GetTransparentColor](../Topic/CMFCToolBarImages::GetTransparentColor.md)||  
|[CMFCToolBarImages::GrayImages](../Topic/CMFCToolBarImages::GrayImages.md)|Atenuadas las imágenes de la barra de herramientas para que parecen deshabilitados.|  
|[CMFCToolBarImages::Is32BitTransparencySupported](../Topic/CMFCToolBarImages::Is32BitTransparencySupported.md)|Determina si el sistema operativo admite mezcla alfa de 32 bits.|  
|[CMFCToolBarImages::IsPreMultiplyAutoCheck](../Topic/CMFCToolBarImages::IsPreMultiplyAutoCheck.md)||  
|[CMFCToolBarImages::IsRTL](../Topic/CMFCToolBarImages::IsRTL.md)|Determina si de derecha \(RTL\) a izquierda compatibilidad está habilitado.|  
|[CMFCToolBarImages::IsReadOnly](../Topic/CMFCToolBarImages::IsReadOnly.md)|Determina si las imágenes de la barra de herramientas son de solo lectura.|  
|[CMFCToolBarImages::IsScaled](../Topic/CMFCToolBarImages::IsScaled.md)|Indica si las imágenes subrayadas se soliciten o no.|  
|[CMFCToolBarImages::IsUserImagesList](../Topic/CMFCToolBarImages::IsUserImagesList.md)|determina si este conjunto de imágenes de la barra de herramientas contiene imágenes definido por el usuario.|  
|[CMFCToolBarImages::IsValid](../Topic/CMFCToolBarImages::IsValid.md)|determina si este conjunto de imágenes de la barra de herramientas contiene una imagen válida de la barra de herramientas.|  
|[CMFCToolBarImages::Load](../Topic/CMFCToolBarImages::Load.md)|Imágenes de la barra de herramientas de carga de recursos del sistema o de un archivo.|  
|[CMFCToolBarImages::LoadStr](../Topic/CMFCToolBarImages::LoadStr.md)||  
|[CMFCToolBarImages::MapFromSysColor](../Topic/CMFCToolBarImages::MapFromSysColor.md)||  
|[CMFCToolBarImages::MapTo3dColors](../Topic/CMFCToolBarImages::MapTo3dColors.md)||  
|[CMFCToolBarImages::MapToSysColor](../Topic/CMFCToolBarImages::MapToSysColor.md)||  
|[CMFCToolBarImages::MapToSysColorAlpha](../Topic/CMFCToolBarImages::MapToSysColorAlpha.md)||  
|[CMFCToolBarImages::Mirror](../Topic/CMFCToolBarImages::Mirror.md)|horizontalmente refleja todas las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::MirrorBitmap](../Topic/CMFCToolBarImages::MirrorBitmap.md)|horizontalmente refleja un mapa de bits.|  
|[CMFCToolBarImages::MirrorBitmapVert](../Topic/CMFCToolBarImages::MirrorBitmapVert.md)||  
|[CMFCToolBarImages::MirrorVert](../Topic/CMFCToolBarImages::MirrorVert.md)||  
|[CMFCToolBarImages::OnSysColorChange](../Topic/CMFCToolBarImages::OnSysColorChange.md)||  
|[CMFCToolBarImages::PrepareDrawImage](../Topic/CMFCToolBarImages::PrepareDrawImage.md)|Asigna los recursos necesarios para dibujar una imagen de la barra de herramientas del tamaño especificado.|  
|[CMFCToolBarImages::Save](../Topic/CMFCToolBarImages::Save.md)|almacena las imágenes de la barra de herramientas en un archivo si este conjunto de imágenes de la barra de herramientas contiene imágenes definido por el usuario.|  
|[CMFCToolBarImages::SetAlwaysLight](../Topic/CMFCToolBarImages::SetAlwaysLight.md)||  
|[CMFCToolBarImages::SetDisabledImageAlpha](../Topic/CMFCToolBarImages::SetDisabledImageAlpha.md)|Establece el valor de canal alfa que se utiliza para las imágenes deshabilitadas.|  
|[CMFCToolBarImages::SetFadedImageAlpha](../Topic/CMFCToolBarImages::SetFadedImageAlpha.md)||  
|[CMFCToolBarImages::SetImageSize](../Topic/CMFCToolBarImages::SetImageSize.md)|Establece el tamaño de la imagen de la barra de herramientas \(tamaño de origen\).|  
|[CMFCToolBarImages::SetLightPercentage](../Topic/CMFCToolBarImages::SetLightPercentage.md)||  
|[CMFCToolBarImages::SetMapTo3DColors](../Topic/CMFCToolBarImages::SetMapTo3DColors.md)||  
|[CMFCToolBarImages::SetPreMultiplyAutoCheck](../Topic/CMFCToolBarImages::SetPreMultiplyAutoCheck.md)||  
|[CMFCToolBarImages::SetSingleImage](../Topic/CMFCToolBarImages::SetSingleImage.md)||  
|[CMFCToolBarImages::SetTransparentColor](../Topic/CMFCToolBarImages::SetTransparentColor.md)|establece el color transparente de las imágenes de la barra de herramientas.|  
|[CMFCToolBarImages::SmoothResize](../Topic/CMFCToolBarImages::SmoothResize.md)|Cambia el tamaño fácilmente imágenes subrayadas.|  
|[CMFCToolBarImages::UpdateImage](../Topic/CMFCToolBarImages::UpdateImage.md)|Actualizar una imagen definido por el usuario de la barra de herramientas de un mapa de bits.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarImages::PreMultiplyAlpha](../Topic/CMFCToolBarImages::PreMultiplyAlpha.md)||  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarImages::m\_bDisableTrueColorAlpha](../Topic/CMFCToolBarImages::m_bDisableTrueColorAlpha.md)|`TRUE` si se deshabilita la mezcla alfa de truecolor \(color de 32 bits\).|  
  
## Comentarios  
 El mapa de bits completo de las imágenes de la barra de herramientas administradas por `CMFCToolbarImages` consta de una o más pequeñas imágenes de la barra de herramientas \(botones\) de un tamaño fijo.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar un objeto de `CMFCToolBarImages` mediante varios métodos en la clase de `CMFCToolBarImages` .  El ejemplo muestra cómo establecer el tamaño de la imagen de la barra de herramientas, carga una imagen, y establece el color transparente en la imagen.  Este fragmento de código es parte de [Ejemplo de demostración de Visual Studio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#32](../../mfc/codesnippet/CPP/cmfctoolbarimages-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#33](../../mfc/codesnippet/CPP/cmfctoolbarimages-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md)  
  
## Requisitos  
 **encabezado:** afxtoolbarimages.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)