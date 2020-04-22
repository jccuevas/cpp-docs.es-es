---
title: Estructura ATL_DRAWINFO
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: fb50f49d387e8620f3d5bbb41263738adbd8b437
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748803"
---
# <a name="atl_drawinfo-structure"></a>Estructura ATL_DRAWINFO

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

`cbSize`<br/>
El tamaño de la estructura, en bytes.

`dwDrawAspect`<br/>
Especifica cómo se va a representar el destino. Las representaciones pueden incluir contenido, un icono, una miniatura o un documento impreso. Para obtener una lista de los valores posibles, consulte [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) y [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2).

`lindex`<br/>
Parte del destino que es de interés para la operación de dibujo. Su interpretación varía dependiendo `dwDrawAspect` del valor en el miembro.

`ptd`<br/>
Puntero a una estructura [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) que permite optimizaciones de dibujo en función del aspecto especificado. Tenga en cuenta que los objetos y contenedores más recientes que admiten interfaces de dibujo optimizadas también admiten este miembro. Los objetos y contenedores más antiguos que no admiten interfaces de dibujo optimizadas siempre especifican NULL para este miembro.

`hicTargetDev`<br/>
Contexto de información para el `ptd` dispositivo de destino al que apunta desde el que el objeto puede extraer métricas de dispositivo y probar las capacidades del dispositivo. Si `ptd` es NULL, el objeto debe `hicTargetDev` omitir el valor del miembro.

`hdcDraw`<br/>
El contexto del dispositivo en el que se desea dibujar. Para un objeto sin ventana, el `hdcDraw` miembro está en el `MM_TEXT` modo de asignación con sus coordenadas lógicas que coinciden con las coordenadas de cliente de la ventana contenedora. Además, el contexto del dispositivo debe estar en `WM_PAINT` el mismo estado que el que normalmente pasa un mensaje.

`prcBounds`<br/>
Puntero a una estructura [RECTL](/windows/win32/api/windef/ns-windef-rectl) `hdcDraw` que especifica el rectángulo y en el que se debe dibujar el objeto. Este miembro controla el posicionamiento y el estiramiento del objeto. Este miembro debe ser NULL para dibujar un objeto activo en el lugar sin ventanas. En cualquier otra situación, NULL no es `E_INVALIDARG` un valor legal y debe dar lugar a un código de error. Si el contenedor pasa un valor no NULL a un objeto sin ventana, el objeto debe representar el aspecto solicitado en el rectángulo y el contexto del dispositivo especificados. Un contenedor puede solicitar esto desde un objeto sin ventana para representar una segunda vista no activa del objeto o para imprimir el objeto.

`prcWBounds`<br/>
Si `hdcDraw` es un contexto de dispositivo de metarchivo (consulte [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) en el Windows SDK), este es un puntero a una `RECTL` estructura que especifica el rectángulo delimitador en el metarchivo subyacente. La estructura del rectángulo contiene la extensión de la ventana y el origen de la ventana. Estos valores son útiles para dibujar metarchivos. El rectángulo indicado `prcBounds` por está `prcWBounds` anidado dentro de este rectángulo; están en el mismo espacio de coordenadas.

`bOptimize`<br/>
Distinto de cero si se va a optimizar el dibujo del control, de lo contrario 0. Si el dibujo está optimizado, el estado del contexto del dispositivo se restaura automáticamente cuando haya terminado de renderizar.

`bZoomed`<br/>
Distinto de cero si el destino tiene un factor de zoom, de lo contrario 0. El factor de `ZoomNum`zoom se almacena en .

`bRectInHimetric`<br/>
Distinto de cero `prcBounds` si las dimensiones de están en HIMETRIC, de lo contrario 0.

`ZoomNum`<br/>
Ancho y alto del rectángulo en el que se representa el objeto. El factor de zoom a lo largo del eje X (la proporción del tamaño natural `ZoomNum.cx` del objeto `ZoomDen.cx`hasta su extensión actual) del destino es el valor de dividido por el valor de . El factor de zoom a lo largo del eje Y se logra de una manera similar.

`ZoomDen`<br/>
La anchura y la altura reales del objetivo.

## <a name="remarks"></a>Observaciones

El uso típico de esta estructura sería la recuperación de información durante la representación del objeto de destino. Por ejemplo, podría recuperar valores de ATL_DRAWINFO dentro de la sobrecarga de [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Esta estructura almacena la información pertinente utilizada para representar la apariencia de un objeto para el dispositivo de destino. La información proporcionada se puede utilizar para dibujar en la pantalla, una impresora o incluso un metarchivo.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="see-also"></a>Vea también

[Clases y estructuras](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
