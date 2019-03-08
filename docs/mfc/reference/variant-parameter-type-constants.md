---
title: Constantes de tipo de parámetro Variant
ms.date: 11/04/2016
f1_keywords:
- VTS_YPOS_HIMETRIC
- VTS_PICTURE
- VTS_FONT
- VTS_XPOS_HIMETRIC
- VTS_XPOS_PIXELS
- VTS_XSIZE_HIMETRIC
- VTS_YPOS_PIXELS
- VTS_TRISTATE
- VTS_HANDLE
- VTS_YSIZE_HIMETRIC
- VTS_COLOR
- VTS_OPTEXCLUSIVE
- VTS_YSIZE_PIXELS
- VTS_XSIZE_PIXELS
helpviewer_keywords:
- VTS_XPOS_HIMETRIC constant [MFC]
- VTS_FONT constant [MFC]
- VTS_XPOS_PIXELS constant [MFC]
- VTS_COLOR constant [MFC]
- Variants [MFC]
- VTS_YPOS_PIXELS constant [MFC]
- VTS_YSIZE_HIMETRIC constant [MFC]
- VTS_YPOS_HIMETRIC constant [MFC]
- Variants, parameter type constants
- Variant data constants [MFC]
- VTS_PICTURE constant [MFC]
- VTS_TRISTATE constant [MFC]
- VTS_XSIZE_HIMETRIC constant [MFC]
- VTS_HANDLE constant [MFC]
- VTS_XSIZE_PIXELS constant [MFC]
- VTS_OPTEXCLUSIVE constant [MFC]
- VTS_YSIZE_PIXELS constant [MFC]
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
ms.openlocfilehash: b15a303f69ce13cf3ba3b6c1c0739acdb8a33c7c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261640"
---
# <a name="variant-parameter-type-constants"></a>Constantes de tipo de parámetro Variant

En este tema se enumera nuevas constantes que indican los tipos de parámetro variant diseñados para su uso con las clases de control OLE de la biblioteca Microsoft Foundation Class.

La siguiente es una lista de constantes de clase:

##  <a name="_mfc_variant_data_constants"></a> Constantes de datos Variant

- Entero de 32 bits VTS_COLOR utilizado para representar un valor de color RGB.

- Puntero de un VTS_FONT a la `IFontDisp` interfaz de un objeto de fuente OLE.

- Valor de identificador VTS_HANDLE A Windows.

- Puntero de un VTS_PICTURE a la `IPictureDisp` interfaz de un objeto de imagen OLE.

- Valor de 16 bits VTS_OPTEXCLUSIVE usado para un control que está pensado para usarse en un grupo de controles, como botones de radio. Este tipo indica al contenedor que si un control en un grupo tiene un valor TRUE, todas las demás deben ser FALSE.

- Utilizado para las propiedades que pueden tener uno de los tres valores posibles (activados, desactivados, no está disponible), por ejemplo, una casilla de verificación de entero con signo de 16 bits VTS_TRISTATE.

- VTS_XPOS_HIMETRIC 32 bits sin signo entero utilizado para representar una posición a lo largo del eje x en unidades HIMETRIC.

- VTS_YPOS_HIMETRIC 32 bits sin signo entero utilizado para representar una posición a lo largo del eje y en unidades HIMETRIC.

- VTS_XPOS_PIXELS 32 bits sin signo entero utilizado para representar una posición a lo largo del eje x en píxeles.

- VTS_YPOS_PIXELS 32 bits sin signo entero utilizado para representar una posición a lo largo del eje y, en píxeles.

- VTS_XSIZE_PIXELS 32 bits sin signo entero utilizado para representar el ancho de un objeto de la pantalla en píxeles.

- VTS_YSIZE_PIXELS 32 bits sin signo entero utilizado para representar el alto de un objeto de la pantalla en píxeles.

- VTS_XSIZE_HIMETRIC 32 bits sin signo entero utilizado para representar el ancho de un objeto de la pantalla en unidades HIMETRIC.

- VTS_YSIZE_HIMETRIC 32 bits sin signo entero utilizado para representar el alto de un objeto de la pantalla en unidades HIMETRIC.

    > [!NOTE]
    >  Constantes de tipo variant adicionales se han definido para todos los tipos variantes, a excepción de VTS_FONT y VTS_PICTURE, que proporcionan un puntero a la constante de datos variant. Estas constantes se denominan mediante el VTS_P`constantname` convención. Por ejemplo, VTS_PCOLOR es un puntero a un VTS_COLOR (constante).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
