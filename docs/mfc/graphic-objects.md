---
title: Objetos gráficos
ms.date: 11/04/2016
f1_keywords:
- HRGN
- HFONT
- HBITMAP
helpviewer_keywords:
- CRgn class [MFC], HRGN handle type
- HPEN [MFC]
- objects [MFC], graphic
- palettes [MFC], creating in device context
- pens [MFC], creating in device context
- bitmaps [MFC], creating in device contexts
- palette objects [MFC]
- memory [MFC], display contexts
- MFC, graphic objects
- regions [MFC], creating in device context
- CPen class [MFC], HPEN handle type
- GDI objects [MFC]
- HRGN [MFC]
- graphic objects [MFC]
- GDI objects [MFC], graphic-object classes
- CFont class [MFC], HFONT handle type
- HFONT and class CFont [MFC]
- HBITMAP and class CBitmap [MFC]
- fonts [MFC], creating in device context
- images [MFC], graphic objects [MFC]
- CBitmap class [MFC], HBITMAP handle type
- HPALETTE and class CPalette [MFC]
- CBrush class [MFC], HBRUSH handle type
- objects [MFC], graphic objects
- drawing [MFC], in device contexts
- device contexts [MFC], graphic objects [MFC]
- brushes [MFC], creating in device context
- region objects [MFC]
- pen objects [MFC]
- GDI [MFC], graphic-object classes
- graphic objects [MFC], creating in device context
- HBRUSH and class CBrush [MFC]
- painting and device context [MFC]
- CPalette class [MFC], HPALETTE handle type
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
ms.openlocfilehash: a7d038a971fd1d280c100024f8af9a1ec74d8627
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618652"
---
# <a name="graphic-objects"></a>Objetos gráficos

Windows proporciona diversas herramientas de dibujo que se usan en contextos de dispositivo. Incluye lápices para trazar líneas, pinceles para rellenar interiores y fuentes para dibujar texto. MFC proporciona clases de objetos gráficos que equivalen a las herramientas de dibujo de Windows. En la siguiente tabla se recogen las clases disponibles y los tipos de identificador de Interfaz de dispositivo gráfico (GDI) de Windows equivalentes.

> [!NOTE]
> Para obtener más información, vea la [documentación del SDK de GDI+](/windows/win32/gdiplus/-gdiplus-gdi-start).

En este artículo se explica el uso de estas clases de objetos gráficos:

### <a name="classes-for-windows-gdi-objects"></a>Clases de objetos GDI de Windows

|Class|Tipo de identificador de Windows|
|-----------|-------------------------|
|[CPen](reference/cpen-class.md)|`HPEN`|
|[CBrush](reference/cbrush-class.md)|`HBRUSH`|
|[CFont](reference/cfont-class.md)|**HFONT**|
|[CBitmap](reference/cbitmap-class.md)|`HBITMAP`|
|[CPalette](reference/cpalette-class.md)|`HPALETTE`|
|[CRgn](reference/crgn-class.md)|**HRGN**|

> [!NOTE]
> La clase [CImage](../atl-mfc-shared/reference/cimage-class.md) proporciona compatibilidad mejorada con mapas de bits.

Cada clase de objeto gráfico en la biblioteca de clases tiene un constructor que permite crear objetos gráficos de esa clase. Este constructor se tiene que inicializar con la función de creación adecuada, como, por ejemplo, `CreatePen`.

Cada clase de objeto gráfico en la biblioteca de clases tiene un operador de conversión que convierte un objeto MFC en el identificador de Windows asociado. El identificador resultante es válido hasta que el objeto asociado lo desconecta. Utilice la `Detach` función miembro del objeto para desasociar el identificador.

El siguiente código convierte un objeto `CPen` en un identificador de Windows:

[!code-cpp[NVC_MFCDocViewSDI#5](codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>Para crear un objeto gráfico en un contexto de dispositivo

1. Defina un objeto gráfico en el marco de pila. Inicialice el objeto con la función de creación específica del tipo, como `CreatePen`. Como alternativa, inicialice el objeto en el constructor. Vea la explicación de la [creación en una fase y en dos fases](one-stage-and-two-stage-construction-of-objects.md), que proporciona código de ejemplo.

1. [Seleccione el objeto en el contexto del dispositivo actual](selecting-a-graphic-object-into-a-device-context.md)y guarde el objeto gráfico anterior que se seleccionó anteriormente.

1. Cuando termine con el objeto gráfico actual, seleccione el objeto gráfico anterior en el contexto de dispositivo para restaurar su estado.

1. Deje que el objeto gráfico asignado por el marco se elimine automáticamente cuando salga del ámbito.

> [!NOTE]
> Si va a usar un objeto gráfico repetidamente, puede asignarlo una vez y seleccionarlo en un contexto de dispositivo cada vez que lo necesite. Asegúrese de eliminar este objeto cuando ya no lo necesite.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Creación de objetos en una fase y en dos fases](one-stage-and-two-stage-construction-of-objects.md)

- [Ejemplo de creación de un lápiz en una y dos fases](one-stage-and-two-stage-construction-of-objects.md)

- [Selección de un objeto gráfico en un contexto de dispositivo](selecting-a-graphic-object-into-a-device-context.md)

- [Contextos de dispositivo](device-contexts.md)

## <a name="see-also"></a>Consulte también

[Window (Objetos)](window-objects.md)
