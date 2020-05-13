---
title: Estructura de ATL_DRAWINFO
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: 00d93b3dd8b060a21b6ff4083bb9880d8d836a19
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168623"
---
# <a name="atl_drawinfo-structure"></a>Estructura de ATL_DRAWINFO

Contiene información que se usa para representar varios destinos, como una impresora, un metarchivo o un control ActiveX.

## <a name="syntax"></a>Sintaxis

```cpp
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

## <a name="members"></a>Members

`cbSize`<br/>
Tamaño de la estructura, en bytes.

`dwDrawAspect`<br/>
Especifica cómo se va a representar el destino. Las representaciones pueden incluir contenido, un icono, una miniatura o un documento impreso. Para obtener una lista de los valores posibles, vea [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) y [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2).

`lindex`<br/>
Parte del destino que es de interés para la operación de dibujo. Su interpretación varía en función del valor del `dwDrawAspect` miembro.

`ptd`<br/>
Puntero a una estructura [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) que habilita las optimizaciones de dibujo según el aspecto especificado. Tenga en cuenta que los objetos y contenedores más recientes que admiten interfaces de dibujo optimizadas también admiten este miembro. Los objetos y contenedores antiguos que no admiten interfaces de dibujo optimizadas siempre especifican NULL para este miembro.

`hicTargetDev`<br/>
Contexto de información para el dispositivo `ptd` de destino al que apunta desde el que el objeto puede extraer las métricas del dispositivo y probar las funciones del dispositivo. Si `ptd` es null, el objeto debe omitir el valor del `hicTargetDev` miembro.

`hdcDraw`<br/>
Contexto de dispositivo en el que se va a dibujar. Para un objeto sin ventana, el `hdcDraw` miembro está en el `MM_TEXT` modo de asignación con sus coordenadas lógicas que coinciden con las coordenadas de cliente de la ventana contenedora. Además, el contexto de dispositivo debe estar en el mismo estado que el que pasa normalmente un `WM_PAINT` mensaje.

`prcBounds`<br/>
Puntero a una estructura [RecTL](/windows/win32/api/windef/ns-windef-rectl) que especifica el rectángulo en `hdcDraw` y en el que se debe dibujar el objeto. Este miembro controla la posición y la ampliación del objeto. Este miembro debe ser NULL para dibujar un objeto activo en contexto sin ventanas. En cualquier otra situación, NULL no es un valor válido y debe generar un `E_INVALIDARG` código de error. Si el contenedor pasa un valor distinto de NULL a un objeto sin ventana, el objeto debe representar el aspecto solicitado en el contexto de dispositivo y el rectángulo especificados. Un contenedor puede solicitar esto desde un objeto sin ventana para representar una segunda vista no activa del objeto o para imprimir el objeto.

`prcWBounds`<br/>
Si `hdcDraw` es un contexto de dispositivo de metarchivo (vea [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) en el Windows SDK), se trata de un `RECTL` puntero a una estructura que especifica el rectángulo delimitador en el metarchivo subyacente. La estructura de rectángulo contiene la extensión de ventana y el origen de la ventana. Estos valores son útiles para dibujar metaarchivos. El rectángulo indicado por `prcBounds` está anidado dentro de `prcWBounds` este rectángulo; están en el mismo espacio de coordenadas.

`bOptimize`<br/>
Es distinto de cero si se va a optimizar el dibujo del control; de lo contrario, es 0. Si el dibujo está optimizado, el estado del contexto del dispositivo se restaurará automáticamente cuando termine la representación.

`bZoomed`<br/>
Es distinto de cero si el destino tiene un factor de zoom; en caso contrario, es 0. El factor de zoom se almacena `ZoomNum`en.

`bRectInHimetric`<br/>
Es distinto de cero si las `prcBounds` dimensiones de están en HIMETRIC; de lo contrario, es 0.

`ZoomNum`<br/>
Ancho y alto del rectángulo en el que se representa el objeto. El factor de zoom a lo largo del eje x (la proporción del tamaño natural del objeto con respecto a su extensión actual) del destino es el `ZoomNum.cx` valor de dividido por el `ZoomDen.cx`valor de. El factor de zoom a lo largo del eje y se logra de manera similar.

`ZoomDen`<br/>
Ancho y alto reales del destino.

## <a name="remarks"></a>Observaciones

El uso típico de esta estructura sería la recuperación de información durante la representación del objeto de destino. Por ejemplo, puede recuperar valores de ATL_DRAWINFO dentro de la sobrecarga de [CComControlBase:: OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Esta estructura almacena la información pertinente utilizada para representar el aspecto de un objeto para el dispositivo de destino. La información proporcionada se puede usar para dibujar en la pantalla, una impresora o incluso un metarchivo.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

## <a name="see-also"></a>Consulte también

[Clases y estructuras](../../atl/reference/atl-classes.md)<br/>
[IViewObject::D RAW](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
