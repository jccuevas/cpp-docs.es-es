---
title: Funciones de mapa de bits grises o interpoladas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
dev_langs: C++
helpviewer_keywords: gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 372fd343bbca8bfac4ec31a34b3920cf29d35957
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="gray-and-dithered-bitmap-functions"></a>funciones de mapa de bits grises o interpoladas
**Funciones de mapa de bits grises**  
  
 MFC proporciona dos funciones para dar a un mapa de bits la apariencia de un control deshabilitado.  
  
 ![Comparación de versiones de icono grises y originales](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
|||  
|-|-|  
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|Dibuja una versión gris de un mapa de bits.|  
|[AfxGetGrayBitmap](#afxgetgraybitmap)|Copia una versión gris de un mapa de bits.|  
  
 **Funciones de mapa de bits interpoladas**  
  
 MFC también proporciona dos funciones para reemplazar el fondo de un mapa de bits por un patrón interpolado.  
  
 ![Comparación de versiones de icono interpoladas y originales](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
|||  
|-|-|  
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|Dibuja un mapa de bits con un fondo interpolado.|  
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|Copia un mapa de bits con un fondo interpolado.|  
  
##  <a name="afxdrawgraybitmap"></a>  AfxDrawGrayBitmap  
 Dibuja una versión gris de un mapa de bits.  
  
```   
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Apunta al controlador de dominio de destino.  
  
 *x*  
 Coordenada X de destino.  
  
 *y*  
 Coordenada Y de destino.  
  
 `rSrc`  
 Mapa de bits de origen.  
  
 `crBackground`  
 Nuevo color de fondo (normalmente gris, como COLOR_MENU).  
  
### <a name="remarks"></a>Comentarios  
 Un mapa de bits dibujado con `AfxDrawGrayBitmap` tendrá el aspecto de un control desactivado.  
  
 ![Comparación de versiones de icono grises y originales](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  

##  <a name="afxgetgraybitmap"></a>  AfxGetGrayBitmap  
 Copia una versión gris de un mapa de bits.  
  
```   
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>Parámetros  
 `rSrc`  
 Mapa de bits de origen.  
  
 `pDest`  
 Mapa de bits de destino.  
  
 `crBackground`  
 Nuevo color de fondo (normalmente gris, como COLOR_MENU).  
  
### <a name="remarks"></a>Comentarios  
 Un mapa de bits copiado con `AfxGetGrayBitmap` tendrá el aspecto de un control desactivado.  
  
 ![Comparación de versiones de icono grises y originales](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="afxdrawditheredbitmap"></a>  AfxDrawDitheredBitmap  
 Dibuja un mapa de bits, reemplazando su fondo con un patrón interpolado (Comprobador).  
  
```   
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Apunta al controlador de dominio de destino.  
  
 *x*  
 Coordenada X de destino.  
  
 *y*  
 Coordenada Y de destino.  
  
 `rSrc`  
 Mapa de bits de origen.  
  
 `cr1`  
 Uno de los colores de interpolación de dos, por lo general en blanco.  
  
 `cr2`  
 Lo otro interpolación color gris claro normalmente (COLOR_MENU).  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits de origen se dibuja en el controlador de dominio de destino con dos colores ( `cr1` y `cr2`) trama a cuadros Reemplazar el fondo del mapa de bits. El fondo del mapa de bits de origen se define como sus píxeles blancos y todos los píxeles que coinciden con el color del píxel de la esquina superior izquierda del mapa de bits.  
  
 ![Comparación de versiones de icono interpoladas y originales](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  


##  <a name="afxgetditheredbitmap"></a>  AfxGetDitheredBitmap  
 Copia un mapa de bits, reemplazando su fondo con un patrón interpolado (Comprobador).  
  
```   
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>Parámetros  
 `rSrc`  
 Mapa de bits de origen.  
  
 `pDest`  
 Mapa de bits de destino.  
  
 `cr1`  
 Uno de los colores de interpolación de dos, por lo general en blanco.  
  
 `cr2`  
 Lo otro interpolación color gris claro normalmente (COLOR_MENU).  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits de origen se copia en el mapa de bits de destino con dos colores ( `cr1` y `cr2`) trama a cuadros Reemplazar el fondo de la fuente de mapa de bits. El fondo del mapa de bits de origen se define como sus píxeles blancos y todos los píxeles que coinciden con el color del píxel de la esquina superior izquierda del mapa de bits.  
  
 ![Comparación de versiones de icono interpoladas y originales](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
