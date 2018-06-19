---
title: CPalette (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
dev_langs:
- C++
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36cc13fa77becf5bdeb3960f6ac9db18d5d63dbb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377281"
---
# <a name="cpalette-class"></a>CPalette (clase)
Encapsula una paleta de colores de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPalette : public CGdiObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPalette::CPalette](#cpalette)|Construye un `CPalette` objeto con ninguna paleta Windows adjuntada. Debe inicializar el `CPalette` objeto con una de las funciones de miembro de inicialización antes de poder utilizarlo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPalette:: AnimatePalette](#animatepalette)|Reemplaza las entradas de la paleta lógica identificado por la `CPalette` objeto. La aplicación no tiene que actualizar su área de cliente, porque Windows asigna las nuevas entradas en la paleta del sistema inmediatamente.|  
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Crea una paleta de semitonos para el contexto de dispositivo y lo adjunta a la `CPalette` objeto.|  
|[CPalette::CreatePalette](#createpalette)|Crea una paleta de colores de Windows y lo adjunta a la `CPalette` objeto.|  
|[CPalette::FromHandle](#fromhandle)|Devuelve un puntero a un `CPalette` objeto cuando se especifica un identificador a un objeto de la paleta de Windows.|  
|[CPalette::GetEntryCount](#getentrycount)|Recupera el número de entradas de la paleta de una paleta lógica.|  
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Devuelve el índice de la entrada de la paleta lógica que mejor se ajuste a un valor de color.|  
|[CPalette::GetPaletteEntries](#getpaletteentries)|Recupera un intervalo de entradas de la paleta de una paleta lógica.|  
|[CPalette::ResizePalette](#resizepalette)|Cambia el tamaño de la paleta lógica especificada por el `CPalette` objeto para el número de entradas especificado.|  
|[CPalette::SetPaletteEntries](#setpaletteentries)|Establece los valores de color RGB y marcas en un intervalo de entradas de una paleta lógica.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPalette::operator HPALETTE](#operator_hpalette)|Devuelve el `HPALETTE` conectado a la `CPalette`.|  
  
## <a name="remarks"></a>Comentarios  
 Una paleta proporciona una interfaz entre una aplicación y un dispositivo de salida de color (por ejemplo, un dispositivo de pantalla). La interfaz permite que la aplicación aprovechar al máximo las capacidades relativas al color del dispositivo de salida sin graves interferir con los colores mostrados por otras aplicaciones. Windows usa la paleta lógica de la aplicación (una lista de colores sea necesarios) y la paleta del sistema (que define los colores disponibles) para determinar los colores utilizados.  
  
 Un `CPalette` objeto proporciona funciones miembro para manipular la paleta que hace referencia el objeto. Construir un `CPalette` de objetos y utilizar sus funciones miembro que se va a crear la paleta real, un objeto de interfaz (GDI) de dispositivo de gráficos como manipular sus entradas y otras propiedades.  
  
 Para obtener más información sobre el uso de `CPalette`, consulte [objetos gráficos](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPalette`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="animatepalette"></a>  CPalette:: AnimatePalette  
 Reemplaza las entradas de la paleta lógica que se adjunta a la `CPalette` objeto.  
  
```  
void AnimatePalette(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartIndex`  
 Especifica la primera entrada de la paleta que se va a animar.  
  
 `nNumEntries`  
 Especifica el número de entradas de la paleta que se va a animar.  
  
 `lpPaletteColors`  
 Apunta al primer miembro de una matriz de [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) estructuras para reemplazar las entradas de la paleta identificadas por `nStartIndex` y `nNumEntries`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una aplicación llama `AnimatePalette`, no tiene que actualizar su área de cliente, porque Windows asigna las nuevas entradas en la paleta del sistema inmediatamente.  
  
 El `AnimatePalette` función solamente cambiarán de entradas con el **PC_RESERVED** marcador establecido en el correspondiente **palPaletteEntry** miembro de la [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) estructura que está conectada a la `CPalette` objeto. Vea **LOGPALETTE** en el SDK de Windows para obtener más información acerca de esta estructura.  
  
##  <a name="cpalette"></a>  CPalette::CPalette  
 Construye un objeto `CPalette`.  
  
```  
CPalette();
```  
  
### <a name="remarks"></a>Comentarios  
 El objeto no tiene ninguna paleta adjuntada hasta que llame a `CreatePalette` para conectar una.  
  
##  <a name="createhalftonepalette"></a>  CPalette::CreateHalftonePalette  
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
 Una aplicación debe crear una paleta de semitonos cuando el modo de ajuste de un contexto de dispositivo se establece en **medios TONOS**. La paleta de semitonos lógica devuelta por la [CreateHalftonePalette](http://msdn.microsoft.com/library/windows/desktop/dd183503) función miembro debe, a continuación, selecciona y realiza en el contexto de dispositivo antes de la [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) o [ StretchDIBits](http://msdn.microsoft.com/library/windows/desktop/dd145121) función se invoca.  
  
 Consulte el SDK de Windows para obtener más información acerca de `CreateHalftonePalette` y **StretchDIBits**.  
  
##  <a name="createpalette"></a>  CPalette::CreatePalette  
 Inicializa un `CPalette` objeto mediante la creación de una paleta de colores lógico de Windows y adjuntarlo a la `CPalette` objeto.  
  
```  
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpLogPalette`  
 Apunta a un [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) estructura que contiene información acerca de los colores de la paleta lógica.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Consulte el SDK de Windows para obtener más información la **LOGPALETTE** estructura.  
  
##  <a name="fromhandle"></a>  CPalette::FromHandle  
 Devuelve un puntero a un `CPalette` objeto cuando se especifica un identificador a un objeto de la paleta de Windows.  
  
```  
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```  
  
### <a name="parameters"></a>Parámetros  
 `hPalette`  
 Identificador de una paleta de colores de GDI de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CPalette` objeto si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Si un `CPalette` objeto ya no está asociado a la paleta de Windows, un archivo temporal `CPalette` se crea y asocia el objeto. Este temporal `CPalette` objeto es válido solo hasta la próxima vez que la aplicación tenga tiempo de inactividad en el bucle de eventos, que hora gráfico temporal todos los objetos se eliminan. En otras palabras, el objeto temporal es válido solo durante el procesamiento de mensajes de una ventana.  
  
##  <a name="getentrycount"></a>  CPalette::GetEntryCount  
 Llame a esta función miembro para recuperar el número de entradas de una paleta lógica determinada.  
  
```  
int GetEntryCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de entradas de una paleta lógica.  
  
##  <a name="getnearestpaletteindex"></a>  CPalette::GetNearestPaletteIndex  
 Devuelve el índice de la entrada de la paleta lógica que mejor se ajuste el valor de color especificado.  
  
```  
UINT GetNearestPaletteIndex(COLORREF crColor) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 Especifica el color que se debe coincidir.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de una entrada en una paleta lógica. La entrada contiene el color que más se ajusta el color especificado.  
  
##  <a name="getpaletteentries"></a>  CPalette::GetPaletteEntries  
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
 Especifica el número de entradas de la paleta lógica va a recuperar.  
  
 `lpPaletteColors`  
 Apunta a una matriz de [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) estructuras de datos para recibir las entradas de la paleta. La matriz debe contener al menos tantos estructuras de datos según lo especificado por `nNumEntries`.  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera el número de entradas de la paleta lógica; 0 si la función produce un error.  
  
##  <a name="operator_hpalette"></a>  CPalette::operator HPALETTE  
 Utilice este operador para obtener el identificador de GDI de Windows asociado de la `CPalette` objeto.  
  
```  
operator HPALETTE() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, un identificador para el objeto GDI de Windows representado por la `CPalette` objeto; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Éste es un operador de conversión, que admite el uso directo de un `HPALETTE` objeto.  
  
 Para obtener más información sobre el uso de objetos gráficos, vea el artículo [gráfico de objetos](http://msdn.microsoft.com/library/windows/desktop/dd144962) en el SDK de Windows.  
  
##  <a name="resizepalette"></a>  CPalette::ResizePalette  
 Cambia el tamaño de la paleta lógica que se adjunta a la `CPalette` objeto para el número de entradas especificado por `nNumEntries`.  
  
```  
BOOL ResizePalette(UINT nNumEntries);
```  
  
### <a name="parameters"></a>Parámetros  
 `nNumEntries`  
 Especifica el número de entradas de la paleta después de se ha cambiado de tamaño.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la paleta correctamente cambió de tamaño; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si una aplicación llama `ResizePalette` para reducir el tamaño de la paleta, se modifican las entradas restantes de la paleta cuyo tamaño ha cambiado. Si la aplicación llama a `ResizePalette` para ampliar la paleta, las entradas de la paleta adicionales se establecen en negro (los valores de rojos, verde y azules son 0) y los indicadores para todas las entradas adicionales se establecen en 0.  
  
 Para obtener más información sobre la API de Windows `ResizePalette`, consulte [ResizePalette](http://msdn.microsoft.com/library/windows/desktop/dd162928) en el SDK de Windows.  
  
##  <a name="setpaletteentries"></a>  CPalette::SetPaletteEntries  
 Establece los valores de color RGB y marcas en un intervalo de entradas de una paleta lógica.  
  
```  
UINT SetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartIndex`  
 Especifica la primera entrada de la paleta lógica se establezca.  
  
 `nNumEntries`  
 Especifica el número de entradas en la paleta lógica que puede establecer.  
  
 `lpPaletteColors`  
 Apunta a una matriz de [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) estructuras de datos para recibir las entradas de la paleta. La matriz debe contener al menos tantos estructuras de datos según lo especificado por `nNumEntries`.  
  
### <a name="return-value"></a>Valor devuelto  
 Establece el número de entradas de la paleta lógica; 0 si la función produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Si se selecciona la paleta lógica en un contexto de dispositivo cuando la aplicación llama `SetPaletteEntries`, los cambios no surtirán efecto hasta que la aplicación llama [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).  
  
 Para obtener más información sobre la estructura de Windows **PALETTEENTRY**, consulte [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Clase CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](#getpaletteentries)   
 [CPalette::SetPaletteEntries](#setpaletteentries)



