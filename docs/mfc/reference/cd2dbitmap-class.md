---
title: "CD2DBitmap (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DBitmap"
  - "CD2DBitmap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DBitmap (clase)"
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DBitmap (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1Bitmap.  
  
## Sintaxis  
  
```  
class CD2DBitmap : public CD2DResource;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::CD2DBitmap](../Topic/CD2DBitmap::CD2DBitmap.md)|Sobrecargado.  Construye un objeto CD2DBitmap de HBITMAP.|  
|[CD2DBitmap::~CD2DBitmap](../Topic/CD2DBitmap::~CD2DBitmap.md)|El destructor.  Se llama cuando se destruye un objeto de mapa de bits D2D.|  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::CD2DBitmap](../Topic/CD2DBitmap::CD2DBitmap.md)|Sobrecargado.  Construye un objeto CD2DBitmap.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::Attach](../Topic/CD2DBitmap::Attach.md)|Adjunta la interfaz de recurso existente al objeto|  
|[CD2DBitmap::CopyFromBitmap](../Topic/CD2DBitmap::CopyFromBitmap.md)|Copia la región especificada del mapa de bits especificado en el mapa de bits actual|  
|[CD2DBitmap::CopyFromMemory](../Topic/CD2DBitmap::CopyFromMemory.md)|Copia la región especificada de la memoria en el mapa de bits actual|  
|[CD2DBitmap::CopyFromRenderTarget](../Topic/CD2DBitmap::CopyFromRenderTarget.md)|Copia la región especificada del destino de representación especificado en el mapa de bits actual|  
|[CD2DBitmap::Create](../Topic/CD2DBitmap::Create.md)|Crea un CD2DBitmap.  \(Invalida [CD2DResource::Create](../Topic/CD2DResource::Create.md).\)|  
|[CD2DBitmap::Destroy](../Topic/CD2DBitmap::Destroy.md)|Destruye un objeto CD2DBitmap.  \(Invalida [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md).\)|  
|[CD2DBitmap::Detach](../Topic/CD2DBitmap::Detach.md)|Desasocia la interfaz de recurso del objeto|  
|[CD2DBitmap::Get](../Topic/CD2DBitmap::Get.md)|Devuelve la interfaz ID2D1Bitmap|  
|[CD2DBitmap::GetDPI](../Topic/CD2DBitmap::GetDPI.md)|Devuelve los puntos por pulgada \(PPP\) del mapa de bits|  
|[CD2DBitmap::GetPixelFormat](../Topic/CD2DBitmap::GetPixelFormat.md)|Recupera el formato de píxel y el modo alfa del mapa de bits|  
|[CD2DBitmap::GetPixelSize](../Topic/CD2DBitmap::GetPixelSize.md)|Devuelve el tamaño, en unidades dependientes del dispositivo \(píxeles\), del mapa de bits|  
|[CD2DBitmap::GetSize](../Topic/CD2DBitmap::GetSize.md)|Devuelve el tamaño, en píxeles independientes del dispositivo \(DIP\), del mapa de bits.|  
|[CD2DBitmap::IsValid](../Topic/CD2DBitmap::IsValid.md)|Comprueba la validez del recurso \(invalida [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\).|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::CommonInit](../Topic/CD2DBitmap::CommonInit.md)|Inicializa el objeto|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::operator ID2D1Bitmap\*](../Topic/CD2DBitmap::operator%20ID2D1Bitmap*.md)|Devuelve la interfaz ID2D1Bitmap|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmap::m\_bAutoDestroyHBMP](../Topic/CD2DBitmap::m_bAutoDestroyHBMP.md)|TRUE si m\_hBmpSrc se debe destruir; de lo contrario FALSE.|  
|[CD2DBitmap::m\_hBmpSrc](../Topic/CD2DBitmap::m_hBmpSrc.md)|Identificador origen del mapa de bits.|  
|[CD2DBitmap::m\_lpszType](../Topic/CD2DBitmap::m_lpszType.md)|Tipo de recurso.|  
|[CD2DBitmap::m\_pBitmap](../Topic/CD2DBitmap::m_pBitmap.md)|Almacena un puntero a un objeto ID2D1Bitmap.|  
|[CD2DBitmap::m\_sizeDest](../Topic/CD2DBitmap::m_sizeDest.md)|Tamaño de destino de mapa de bits.|  
|[CD2DBitmap::m\_strPath](../Topic/CD2DBitmap::m_strPath.md)|Ruta de acceso del archivo de mapa de bits.|  
|[CD2DBitmap::m\_uiResID](../Topic/CD2DBitmap::m_uiResID.md)|Id. de recursos de mapa de bits.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBitmap](../../mfc/reference/cd2dbitmap-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)