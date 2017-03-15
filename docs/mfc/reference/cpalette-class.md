---
title: CPalette (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPalette
- HPALETTE
dev_langs:
- C++
helpviewer_keywords:
- CPalette class
- HPALETTE
- color palettes, MFC
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
caps.latest.revision: 23
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
ms.openlocfilehash: 6ccd389eaf765993c59311cc1041893f2cf9fbfa
ms.lasthandoff: 02/24/2017

---
# <a name="cpalette-class"></a>CPalette (clase)
Encapsula una paleta de colores de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPalette : public CGdiObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPalette::CPalette](#cpalette)|Construye un `CPalette` objeto con ninguna paleta Windows conectada. Debe inicializar el `CPalette` objeto con una de las funciones de miembro de inicialización antes de poder usarlo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPalette:: AnimatePalette](#animatepalette)|Reemplaza las entradas de la paleta lógica identificado por la `CPalette` objeto. La aplicación no tiene actualizar su área cliente, porque Windows asigna las entradas nuevas en la paleta del sistema inmediatamente.|  
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Crea una paleta de semitonos para el contexto de dispositivo y lo adjunta a la `CPalette` objeto.|  
|[CPalette::CreatePalette](#createpalette)|Crea una paleta de colores de Windows y lo adjunta a la `CPalette` objeto.|  
|[CPalette::FromHandle](#fromhandle)|Devuelve un puntero a un `CPalette` objeto cuando se especifica un identificador a un objeto de la paleta de Windows.|  
|[CPalette::GetEntryCount](#getentrycount)|Recupera el número de entradas de la paleta de una paleta lógica.|  
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Devuelve el índice de la entrada de la paleta lógica que mejor coincida con un valor de color.|  
|[CPalette::GetPaletteEntries](#getpaletteentries)|Recupera un intervalo de entradas de la paleta de una paleta lógica.|  
|[CPalette::ResizePalette](#resizepalette)|Cambia el tamaño de la paleta lógica especificada por el `CPalette` objeto el número especificado de entradas.|  
|[CPalette::SetPaletteEntries](#setpaletteentries)|Establece los indicadores y sus valores RGB de un intervalo de entradas de una paleta lógica.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPalette::operator HPALETTE](#operator_hpalette)|Devuelve el `HPALETTE` conectado a la `CPalette`.|  
  
## <a name="remarks"></a>Comentarios  
 Una paleta proporciona una interfaz entre una aplicación y un dispositivo de salida de color (por ejemplo, un dispositivo de pantalla). La interfaz permite que la aplicación aprovechar al máximo las capacidades de color del dispositivo de salida sin gravemente interferir con los colores que se muestran por otras aplicaciones. Windows usa la paleta lógica de la aplicación (una lista de colores necesarias) y la paleta del sistema (que define los colores disponibles) para determinar los colores utilizados.  
  
 Un `CPalette` objeto proporciona funciones miembro para manipular la paleta que hace referencia el objeto. Construir un `CPalette` de objetos y utilizar sus funciones miembro para crear la paleta real, un objeto de interfaz (GDI) de dispositivo de gráficos y manipular sus entradas y otras propiedades.  
  
 Para obtener más información sobre el uso de `CPalette`, consulte [objetos gráficos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPalette`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-nameanimatepalettea--cpaletteanimatepalette"></a><a name="animatepalette"></a>CPalette:: AnimatePalette  
 Reemplaza las entradas de la paleta lógica asociado a la `CPalette` objeto.  
  
```  
void AnimatePalette(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartIndex`  
 Especifica la primera entrada en la paleta a animar.  
  
 `nNumEntries`  
 Especifica el número de entradas en la paleta a animar.  
  
 `lpPaletteColors`  
 Apunta al primer miembro de una matriz de [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) estructuras para reemplazar las entradas de paleta identificadas por `nStartIndex` y `nNumEntries`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una aplicación llama `AnimatePalette`, no tiene que actualizar su área cliente, porque Windows asigna las entradas nuevas en la paleta del sistema inmediatamente.  
  
 El `AnimatePalette` función cambiará sólo las entradas con el **PC_RESERVED** marcador establecido en el correspondiente **palPaletteEntry** miembro de la [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) estructura que se adjunta a la `CPalette` objeto. Consulte **LOGPALETTE** en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información acerca de esta estructura.  
  
##  <a name="a-namecpalettea--cpalettecpalette"></a><a name="cpalette"></a>CPalette::CPalette  
 Construye un objeto `CPalette`.  
  
```  
CPalette();
```  
  
### <a name="remarks"></a>Comentarios  
 El objeto no tiene ninguna paleta adjuntada hasta que llame a `CreatePalette` para conectar una.  
  
##  <a name="a-namecreatehalftonepalettea--cpalettecreatehalftonepalette"></a><a name="createhalftonepalette"></a>CPalette::CreateHalftonePalette  
 Crea una paleta de semitonos para el contexto de dispositivo.  
  
```  
BOOL CreateHalftonePalette(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Identifica el contexto de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación debe crear una paleta de semitonos cuando el modo de ajuste de un contexto de dispositivo se establece en **SEMITONOS**. La paleta de semitonos lógica devuelta por la [CreateHalftonePalette](http://msdn.microsoft.com/library/windows/desktop/dd183503) función miembro, a continuación, se selecciona y realiza en el contexto de dispositivo antes de la [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) o [StretchDIBits](http://msdn.microsoft.com/library/windows/desktop/dd145121) se llama la función.  
  
 Consulte la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información acerca de `CreateHalftonePalette` y **StretchDIBits**.  
  
##  <a name="a-namecreatepalettea--cpalettecreatepalette"></a><a name="createpalette"></a>CPalette::CreatePalette  
 Inicializa un `CPalette` objeto creando una paleta de colores lógica de Windows y adjuntarlo a la `CPalette` objeto.  
  
```  
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpLogPalette`  
 Apunta a un [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) estructura que contiene información acerca de los colores de la paleta lógica.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Consulte la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información acerca de la **LOGPALETTE** estructura.  
  
##  <a name="a-namefromhandlea--cpalettefromhandle"></a><a name="fromhandle"></a>CPalette::FromHandle  
 Devuelve un puntero a un `CPalette` objeto cuando se especifica un identificador a un objeto de la paleta de Windows.  
  
```  
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```  
  
### <a name="parameters"></a>Parámetros  
 `hPalette`  
 Identificador de una paleta de colores de Windows GDI.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CPalette` objeto si se realiza correctamente; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CPalette` objeto no está asociado a la paleta de Windows, un archivo temporal `CPalette` objeto creado y conectado. Este temporal `CPalette` objeto es válido sólo hasta la próxima vez que la aplicación tenga tiempo de inactividad en el bucle de eventos, que hora gráfico temporal de todos los objetos se eliminan. En otras palabras, el objeto temporal es válido solo durante el procesamiento de mensajes de una ventana.  
  
##  <a name="a-namegetentrycounta--cpalettegetentrycount"></a><a name="getentrycount"></a>CPalette::GetEntryCount  
 Llame a esta función miembro para recuperar el número de entradas de una paleta lógica determinada.  
  
```  
int GetEntryCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de entradas de una paleta lógica.  
  
##  <a name="a-namegetnearestpaletteindexa--cpalettegetnearestpaletteindex"></a><a name="getnearestpaletteindex"></a>CPalette::GetNearestPaletteIndex  
 Devuelve el índice de la entrada de la paleta lógica que mejor coincida con el valor de color especificado.  
  
```  
UINT GetNearestPaletteIndex(COLORREF crColor) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 Especifica el color que se debe coincidir.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de una entrada en una paleta lógica. La entrada contiene el color que más se ajusta el color especificado.  
  
##  <a name="a-namegetpaletteentriesa--cpalettegetpaletteentries"></a><a name="getpaletteentries"></a>CPalette::GetPaletteEntries  
 Recupera un intervalo de entradas de la paleta de una paleta lógica.  
  
```  
UINT GetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartIndex`  
 Especifica la primera entrada de la paleta lógica va a recuperar.  
  
 `nNumEntries`  
 Especifica el número de entradas en la paleta lógica va a recuperar.  
  
 `lpPaletteColors`  
 Apunta a una matriz de [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) estructuras de datos para recibir las entradas de la paleta. La matriz debe contener al menos tantas estructuras de datos según lo especificado por `nNumEntries`.  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera el número de entradas de la paleta lógica; 0 si el error de la función.  
  
##  <a name="a-nameoperatorhpalettea--cpaletteoperator-hpalette"></a><a name="operator_hpalette"></a>CPalette::operator HPALETTE  
 Utilice este operador para obtener el identificador de Windows GDI adjunto de la `CPalette` objeto.  
  
```  
operator HPALETTE() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un identificador para el objeto de GDI de Windows representado por la `CPalette` objeto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Este operador es un operador de conversión, que admite el uso directo de una `HPALETTE` objeto.  
  
 Para obtener más información acerca del uso de objetos gráficos, vea el artículo [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameresizepalettea--cpaletteresizepalette"></a><a name="resizepalette"></a>CPalette::ResizePalette  
 Cambia el tamaño de la paleta lógico asociado a la `CPalette` objeto en el número de entradas especificado por `nNumEntries`.  
  
```  
BOOL ResizePalette(UINT nNumEntries);
```  
  
### <a name="parameters"></a>Parámetros  
 `nNumEntries`  
 Especifica el número de entradas en la paleta después de se ha cambiado de tamaño.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la paleta cambió de tamaño correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si una aplicación llama `ResizePalette` para reducir el tamaño de la paleta, se modifican las entradas restantes en la paleta cuyo tamaño ha cambiado. Si la aplicación llama a `ResizePalette` para ampliar la paleta, se establecen las entradas de paleta adicional en negro (los valores rojos, verde y azules son 0), y los indicadores para todas las entradas adicionales se establecen en 0.  
  
 Para obtener más información acerca de la API de Windows `ResizePalette`, consulte [ResizePalette](http://msdn.microsoft.com/library/windows/desktop/dd162928) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetpaletteentriesa--cpalettesetpaletteentries"></a><a name="setpaletteentries"></a>CPalette::SetPaletteEntries  
 Establece los indicadores y sus valores RGB de un intervalo de entradas de una paleta lógica.  
  
```  
UINT SetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartIndex`  
 Especifica la primera entrada en la paleta lógica a establecerse.  
  
 `nNumEntries`  
 Especifica el número de entradas en la paleta lógica a establecerse.  
  
 `lpPaletteColors`  
 Apunta a una matriz de [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) estructuras de datos para recibir las entradas de la paleta. La matriz debe contener al menos tantas estructuras de datos según lo especificado por `nNumEntries`.  
  
### <a name="return-value"></a>Valor devuelto  
 Establece el número de entradas en la paleta lógica; 0 si el error de la función.  
  
### <a name="remarks"></a>Comentarios  
 Si se selecciona la paleta lógica en un contexto de dispositivo cuando la aplicación llama `SetPaletteEntries`, los cambios no surtirán efecto hasta que la aplicación llame [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).  
  
 Para obtener más información sobre la estructura de Windows **PALETTEENTRY**, consulte [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Clase CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](#getpaletteentries)   
 [CPalette::SetPaletteEntries](#setpaletteentries)




