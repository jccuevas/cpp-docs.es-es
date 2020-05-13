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
ms.openlocfilehash: f73c72830216679f8a91d0037d48c1e1b8e400c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372865"
---
# <a name="variant-parameter-type-constants"></a>Constantes de tipo de parámetro Variant

En este tema se enumeran las nuevas constantes que indican tipos de parámetros de variante diseñados para su uso con las clases de control OLE de la biblioteca Microsoft Foundation Class.

La siguiente es una lista de constantes de clase:

## <a name="variant-data-constants"></a><a name="_mfc_variant_data_constants"></a>Constantes de datos de variantes

- VTS_COLOR Un entero de 32 bits utilizado para representar un valor de color RGB.

- VTS_FONT un puntero `IFontDisp` a la interfaz de un objeto de fuente OLE.

- VTS_HANDLE Un valor de identificador de Windows.

- VTS_PICTURE un puntero `IPictureDisp` a la interfaz de un objeto de imagen OLE.

- VTS_OPTEXCLUSIVE Un valor de 16 bits utilizado para un control que está diseñado para usarse en un grupo de controles, como botones de opción. Este tipo indica al contenedor que si un control de un grupo tiene un valor TRUE, todos los demás deben ser FALSE.

- VTS_TRISTATE Un entero con signo de 16 bits utilizado para propiedades que pueden tener uno de los tres valores posibles (seleccionados, desactivados, no disponibles), por ejemplo, una casilla de verificación.

- VTS_XPOS_HIMETRIC Un entero sin signo de 32 bits utilizado para representar una posición a lo largo del eje X en unidades HIMETRIC.

- VTS_YPOS_HIMETRIC Un entero sin signo de 32 bits utilizado para representar una posición a lo largo del eje Y en unidades HIMETRIC.

- VTS_XPOS_PIXELS Un entero sin signo de 32 bits utilizado para representar una posición a lo largo del eje X en píxeles.

- VTS_YPOS_PIXELS Un entero sin signo de 32 bits utilizado para representar una posición a lo largo del eje Y en píxeles.

- VTS_XSIZE_PIXELS Un entero sin signo de 32 bits utilizado para representar el ancho de un objeto de pantalla en píxeles.

- VTS_YSIZE_PIXELS Un entero sin signo de 32 bits utilizado para representar el alto de un objeto de pantalla en píxeles.

- VTS_XSIZE_HIMETRIC Un entero sin signo de 32 bits utilizado para representar el ancho de un objeto de pantalla en unidades HIMETRIC.

- VTS_YSIZE_HIMETRIC Un entero sin signo de 32 bits utilizado para representar la altura de un objeto de pantalla en unidades HIMETRIC.

    > [!NOTE]
    >  Se han definido constantes de variante adicionales para todos los tipos de variante, con la excepción de VTS_FONT y VTS_PICTURE, que proporcionan un puntero a la constante de datos de variante. Estas constantes se denominan mediante la convención VTS_P.`constantname` Por ejemplo, VTS_PCOLOR es un puntero a una constante VTS_COLOR.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
