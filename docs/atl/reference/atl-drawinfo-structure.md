---
title: Estructura ATL_DRAWINFO | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
dev_langs:
- C++
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c8ba7be259a10ee1bf47bbdc401a2389adac2be
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255969"
---
# <a name="atldrawinfo-structure"></a>Estructura ATL_DRAWINFO
Contiene información utilizada para la representación en varios destinos, como una impresora, un metarchivo o un control ActiveX.  
  
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
 Especifica cómo el destino se va a representar. Representaciones pueden incluir contenido, un icono, una vista en miniatura o un documento impreso. Para obtener una lista de valores posibles, consulte [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) y [DVASPECT2](http://msdn.microsoft.com/library/windows/desktop/ms688644).  
  
 **lIndex**  
 Parte del destino que es de interés para la operación de dibujo. Su interpretación varía según el valor de la **dwDrawAspect** miembro.  
  
 **ptd**  
 Puntero a un [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) estructura que permite optimizaciones de dibujo dependen del aspecto especificado. Tenga en cuenta que más reciente de los objetos y contenedores que admiten las interfaces de dibujo optimizadas admiten a este miembro también. Especifican los objetos antiguos y contenedores que no son compatibles con las interfaces de dibujo optimizadas siempre **NULL** para este miembro.  
  
 **hicTargetDev**  
 Información de contexto para el dispositivo de destino que señala **ptd** desde el que el objeto puede extraer las métricas del dispositivo y probar las capacidades del dispositivo. Si **ptd** es **NULL**, el objeto debe pasar por alto el valor de la **hicTargetDev** miembro.  
  
 **hdcDraw**  
 El contexto de dispositivo en el que se va a dibujar. Para un objeto sin ventana, el **hdcDraw** miembro está en el `MM_TEXT` modo de asignación con sus coordenadas lógicas coincidencia de las coordenadas de cliente de la ventana contenedora. Además, el contexto de dispositivo debe estar en el mismo estado que normalmente se pasa por un `WM_PAINT` mensaje.  
  
 **prcBounds**  
 Puntero a un [RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907) estructura que especifica el rectángulo en **hdcDraw** y en que se debe dibujar el objeto. Este miembro controla la posición y el ajuste del objeto. Este miembro debe ser **NULL** para dibujar un objeto de active en contexto sin ventanas. En todos los demás escenarios, **NULL** no es un valor válido y debe tener como resultado un `E_INVALIDARG` código de error. Si pasa el contenedor no**NULL** valor a un objeto sin ventana, el objeto debe representar el aspecto solicitado en el contexto de dispositivo especificado y el rectángulo. Un contenedor puede solicitar esto a un objeto sin ventanas para representar una vista en segundo lugar, no activo del objeto o para imprimir el objeto.  
  
 **prcWBounds**  
 Si **hdcDraw** es un contexto de dispositivo de metarchivo (vea [GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) en el SDK de Windows), se trata de un puntero a un **RECTL** estructura que especifica el rectángulo delimitador en el Metarchivo subyacente. La estructura de rectángulo contiene la extensión de la ventana y el origen de la ventana. Estos valores son útiles para dibujar metarchivos. El rectángulo indicado por **prcBounds** está anidada dentro de este **prcWBounds** rectángulo; están en el mismo espacio de coordenadas.  
  
 **bOptimize**  
 Es distinto de cero si el dibujo del control es ser optimizado, 0 en caso contrario. Si se optimiza el dibujo, automáticamente se restaura el estado del contexto del dispositivo cuando haya terminado de representación.  
  
 **bZoomed**  
 Es distinto de cero si el destino tiene un factor de zoom, de lo contrario, 0. El factor de zoom se almacena en **ZoomNum**.  
  
 **bRectInHimetric**  
 Distinto de cero si las dimensiones de **prcBounds** en **HIMETRIC**, de lo contrario, 0.  
  
 **ZoomNum**  
 El ancho y alto del rectángulo en el que se representa el objeto. El factor de zoom en el eje x (la proporción del tamaño del objeto natural a su tamaño actual) del destino es el valor de **ZoomNum.cx** dividido por el valor de **ZoomDen.cx**. El factor de zoom a lo largo del eje y se consigue de forma similar.  
  
 **ZoomDen**  
 El ancho real y el alto del destino.  
  
## <a name="remarks"></a>Comentarios  
 Uso típico de esta estructura sería la recuperación de información durante la representación del objeto de destino. Por ejemplo, podría recuperar valores de `ATL_DRAWINFO` dentro de la sobrecarga de [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).  
  
 Esta estructura almacena información pertinente que se usa para representar la apariencia de un objeto para el dispositivo de destino. La información proporcionada se puede utilizar en dibujo en la pantalla, una impresora o incluso un metarchivo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
## <a name="see-also"></a>Vea también  
  [Clases y structs](../../atl/reference/atl-classes.md) [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)





