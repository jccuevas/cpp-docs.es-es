---
title: Estructura ATL_DRAWINFO | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
dev_langs:
- C++
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
caps.latest.revision: 16
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: bc124de97acf85d6e706605afb55b0747a327ade
ms.lasthandoff: 02/24/2017

---
# <a name="atldrawinfo-structure"></a>ATL_DRAWINFO (estructura)
Contiene información utilizada para representar a varios destinos, como una impresora, un metarchivo o un control ActiveX.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct ATL_DRAWINFO {
    UINT cbSize;
    DWORD dwDrawAspect;
    LONG lindex;
    DVTARGETDEVICE* ptd;
    HDC hicTargetDev;
    HDC hdcDraw;
    LPCRECTL prcBounds;
    LPCRECTL prcWBounds;
    BOOL bOptimize;
    BOOL bZoomed;
    BOOL bRectInHimetric;
    SIZEL ZoomNum;
    SIZEL ZoomDen;
};
```  
  
## <a name="members"></a>Miembros  
 `cbSize`  
 El tamaño de la estructura, en bytes.  
  
 **dwDrawAspect**  
 Especifica cómo se representará el destino. Representaciones pueden incluir contenido, un icono, una vista en miniatura o un documento impreso. Para obtener una lista de valores posibles, consulte [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) y [DVASPECT2](http://msdn.microsoft.com/library/windows/desktop/ms688644).  
  
 **lIndex**  
 Parte del destino que es de interés para la operación de dibujo. Su interpretación varía según el valor de la **dwDrawAspect** miembro.  
  
 **ptd**  
 Puntero a un [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) estructura que permite optimizaciones de dibujos dependen del aspecto especificado. Tenga en cuenta que más recientes de los objetos y contenedores que admitan las interfaces de dibujos optimizadas admiten a también este miembro. Especifican los objetos antiguos y contenedores que no admitan las interfaces de dibujos optimizadas siempre **NULL** para este miembro.  
  
 **hicTargetDev**  
 Información de contexto para el dispositivo de destino que señala **ptd** desde el que el objeto puede extraer las métricas del dispositivo y probar las capacidades del dispositivo. Si **ptd** es **NULL**, el objeto debe pasar por alto el valor de la **hicTargetDev** miembro.  
  
 **hdcDraw**  
 El contexto de dispositivo en el que se va a dibujar. Para un objeto sin ventanas, el **hdcDraw** miembro está en el `MM_TEXT` modo de asignación con sus coordenadas lógicas que coinciden con las coordenadas de cliente de la ventana contenedora. Además, debe ser el contexto de dispositivo en el mismo estado que normalmente se pasa por un `WM_PAINT` mensaje.  
  
 **prcBounds**  
 Puntero a un [RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907) estructura que especifica el rectángulo en **hdcDraw** y en el que debe dibujarse el objeto. Este miembro controla la posición y el ajuste del objeto. Este miembro debe ser **NULL** para dibujar un objeto de active en contexto sin ventanas. En cada situación, **NULL** no es un valor válido y debe tener como resultado un `E_INVALIDARG` código de error. Si pasa el contenedor no**NULL** valor a un objeto sin ventanas, el objeto debe presentar el aspecto solicitado en el contexto de dispositivo especificado y el rectángulo. Un contenedor puede solicitarla un objeto sin ventanas para representar una vista en segundo lugar, no activo del objeto o para imprimir el objeto.  
  
 **prcWBounds**  
 Si **hdcDraw** es un contexto de dispositivo de metarchivo (consulte [GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]), se trata de un puntero a un **RECTL** estructura que especifica el rectángulo delimitador en el metarchivo subyacente. La estructura de rectángulo contiene la extensión de la ventana y el origen de la ventana. Estos valores son útiles para dibujar metarchivos. El rectángulo indicado por **prcBounds** está anidada dentro de esta **prcWBounds** rectángulo; están en el mismo espacio de coordenadas.  
  
 **bOptimize**  
 Es distinto de cero si el dibujo del control es ser optimizado 0 en caso contrario. Si se optimiza el dibujo, el estado del contexto de dispositivo se restaura automáticamente cuando haya terminado de representación.  
  
 **bZoomed**  
 Distinto de cero si el destino tiene un factor de zoom, de lo contrario, 0. El factor de zoom se almacena en **ZoomNum**.  
  
 **bRectInHimetric**  
 Distinto de cero si las dimensiones de **prcBounds** en **HIMETRIC**, de lo contrario, 0.  
  
 **ZoomNum**  
 El ancho y alto del rectángulo en el que se procesa el objeto. El factor de zoom en el eje x (la proporción de tamaño natural del objeto a su tamaño actual) del destino es el valor de **ZoomNum.cx** dividido por el valor de **ZoomDen.cx**. El factor de zoom en el eje y se consigue de manera similar.  
  
 **ZoomDen**  
 El ancho real y el alto del destino.  
  
## <a name="remarks"></a>Comentarios  
 Uso típico de esta estructura sería la recuperación de información durante la representación del objeto de destino. Por ejemplo, puede recuperar los valores de `ATL_DRAWINFO` dentro de la sobrecarga de [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).  
  
 Esta estructura almacena información pertinente que se usa para representar la apariencia de un objeto para el dispositivo de destino. Puede utilizarse la información proporcionada en el dibujo en la pantalla, una impresora o incluso un metarchivo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)   
 [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)






