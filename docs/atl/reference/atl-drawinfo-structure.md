---
title: "ATL_DRAWINFO Structure | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::ATL_DRAWINFO"
  - "ATL_DRAWINFO"
  - "ATL.ATL_DRAWINFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL_DRAWINFO structure"
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL_DRAWINFO Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contiene la información utilizada para generar a varios destinos, como una impresora, un metarchivo, o un control ActiveX.  
  
## Sintaxis  
  
```  
  
      struct ATL_DRAWINFO{  
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
  
## Members  
 `cbSize`  
 El tamaño de la estructura, en bytes.  
  
 **dwDrawAspect**  
 Especifica cómo el destino se debe representar.  Las representaciones pueden incluir contenido, el icono, una miniatura, o un documento impreso.  Para obtener una lista de valores posibles, vea [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) y [DVASPE CT2](http://msdn.microsoft.com/library/windows/desktop/ms688644).  
  
 **lindex**  
 Parte de destino que de interés para la operación de dibujo.  Su interpretación varía dependiendo del valor del miembro de **dwDrawAspect** .  
  
 **ptd**  
 Puntero a una estructura de [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) que habilita las optimizaciones del gráfico según el aspecto especificado.  Observe que los objetos y contenedores más recientes que las interfaces de dibujo optimizadas compatibilidad admiten este miembro también.  Objetos y contenedores más antiguos que no admiten interfaces de dibujo optimizadas especifican siempre **NULL** para este miembro.  
  
 **hicTargetDev**  
 El contexto de la información del dispositivo de destino al que **ptd** de las que el objeto puede extraer métricas de dispositivo y prueba la funcionalidad del dispositivo.  Si **ptd** es **NULL**, el objeto debe omitir el valor del miembro de **hicTargetDev** .  
  
 **hdcDraw**  
 El contexto de dispositivo en el que se va a dibujar.  Para un objeto sin ventana, el miembro de **hdcDraw** está en `MM_TEXT` que asigna el modo con sus coordenadas lógicas que coincide con las coordenadas de cliente de la ventana que contiene.  Además, el contexto de dispositivo debe estar en el mismo estado que la última normalmente por un mensaje de `WM_PAINT` .  
  
 **prcBounds**  
 Puntero a una estructura de [RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907) que especifica el rectángulo en **hdcDraw** y en qué debe ser dibujado el objeto.  Este miembro controla la posición y ajustar del objeto.  Este miembro debe ser **NULL** para dibujar un objeto activo en contexto sin ventana.  En cada otra situación, **NULL** no es un valor válido y debe producir un código de error de `E_INVALIDARG` .  Si el contenedor pasa un valor no nulo en un objeto sin ventana, el objeto debe generar el aspecto solicitado en el contexto y el rectángulo especificado del dispositivo.  Un contenedor puede solicitar esto de un objeto sin ventana para generar una segunda, inactivo vista de objeto o imprimir el objeto.  
  
 **prcWBounds**  
 Si **hdcDraw** es un contexto de dispositivo metafile \(vea [GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]\), esto es un puntero a una estructura de **RECTL** que especifica el rectángulo delimitador del metarchivo subyacente.  La estructura del rectángulo contiene la extensión y el origen de ventana.  Estos valores son útiles para dibujar metarchivos.  El rectángulo indicado por **prcBounds** está anidada dentro de este rectángulo de **prcWBounds** ; están en el mismo espacio.  
  
 **bOptimize**  
 Distinto de cero si el gráfico de control a optimizar, si no 0.  Si se optimiza el gráfico, se restablece el estado del contexto de dispositivo automáticamente cuando es la generación finalizado.  
  
 **bZoomed**  
 Distinto de cero si el destino tiene un factor de zoom, si no 0.  El factor de zoom se almacena en **ZoomNum**.  
  
 **bRectInHimetric**  
 Distinto de cero si las dimensiones de **prcBounds** están en **HIMETRIC**, si no 0.  
  
 **ZoomNum**  
 El ancho y el alto del rectángulo en el que se representa el objeto.  El factor de zoom a lo largo del eje X \(la proporción de tamaño natural del objeto a su extensión actual\) de destino es el valor de **ZoomNum.cx** de por el valor de **ZoomDen.cx**.  El factor de zoom a lo largo del eje Y se alcanza de manera similar.  
  
 **ZoomDen**  
 El ancho y el alto reales de destino.  
  
## Comentarios  
 El uso típico de esta estructura sería la recuperación de información durante la representación del objeto de destino.  Por ejemplo, podría recuperar valores de `ATL_DRAWINFO` dentro de la sobrecarga de [CComControlBase:: OnDrawAdvanced](../Topic/CComControlBase::OnDrawAdvanced.md).  
  
 Esta estructura almacena la información pertinente utilizada para generar el aspecto de un objeto para el dispositivo de destino.  La información proporcionada se puede utilizar en el gráfico en la pantalla, a una impresora, o incluso un metarchivo.  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)   
 [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../Topic/CComControlBase::OnDrawAdvanced.md)