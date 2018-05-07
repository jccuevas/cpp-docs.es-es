---
title: Constantes de tipo de parámetro Variant | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13820ff4fb07c3743f36ba3ebe33ee56a3a79c7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="variant-parameter-type-constants"></a>Constantes de tipo de parámetro Variant
Este tema enumeran las constantes nuevas que indican los tipos de parámetro variant diseñados para su uso con las clases de control OLE de la biblioteca Microsoft Foundation Class.  
  
 La siguiente es una lista de constantes de clase:  
  
##  <a name="_mfc_variant_data_constants"></a> Constantes de datos Variant  
  
-   **VTS_COLOR** entero de 32 bits que se utiliza para representar un valor de color RGB.  
  
-   **VTS_FONT** un puntero a la **IFontDisp** interfaz de un objeto de fuente OLE.  
  
-   **VTS_HANDLE** identificador de Windows de un valor.  
  
-   **VTS_PICTURE** un puntero a la `IPictureDisp` interfaz de un objeto de imagen OLE.  
  
-   **VTS_OPTEXCLUSIVE** valor A 16 bits que se utiliza para un control que está pensado para usarse en un grupo de controles, como botones de radio. Este tipo se indica al contenedor si un control en un grupo tiene un **TRUE** valor, todas las demás deben ser **FALSE**.  
  
-   **VTS_TRISTATE** entero A 16 bits con signo que usa para las propiedades que pueden tener uno de tres valores posibles (activados, desactivados y no disponibles), por ejemplo, una casilla de verificación.  
  
-   **VTS_XPOS_HIMETRIC** entero sin signo de 32 bits utilizado para representar una posición a lo largo del eje x en **HIMETRIC** unidades.  
  
-   **VTS_YPOS_HIMETRIC** entero sin signo de 32 bits utilizado para representar una posición a lo largo del eje y en **HIMETRIC** unidades.  
  
-   **VTS_XPOS_PIXELS** entero sin signo de 32 bits utilizado para representar una posición en el eje x, en píxeles.  
  
-   **VTS_YPOS_PIXELS** entero sin signo de 32 bits utilizado para representar una posición a lo largo del eje y, en píxeles.  
  
-   **VTS_XSIZE_PIXELS** entero sin signo de 32 bits utilizado para representar el ancho de un objeto de la pantalla en píxeles.  
  
-   **VTS_YSIZE_PIXELS** entero sin signo de 32 bits utilizado para representar el alto de un objeto de la pantalla en píxeles.  
  
-   **VTS_XSIZE_HIMETRIC** entero sin signo de 32 bits utilizado para representar el ancho de un objeto de la pantalla en **HIMETRIC** unidades.  
  
-   **VTS_YSIZE_HIMETRIC** entero sin signo de 32 bits utilizado para representar el alto de un objeto de la pantalla en **HIMETRIC** unidades.  
  
    > [!NOTE]
    >  Constantes de tipo variantes adicionales se han definido para todos los tipos variantes, con la excepción de **VTS_FONT** y **VTS_PICTURE**, que proporciona un puntero a la oficina central de datos variant nstant. Estas constantes se denominan utilizando la **VTS_P** `constantname` convención. Por ejemplo, **VTS_PCOLOR** es un puntero a un **VTS_COLOR** constante.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
