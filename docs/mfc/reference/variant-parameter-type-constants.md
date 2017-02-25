---
title: "Constantes de tipo de par&#225;metro Variant | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VTS_YPOS_HIMETRIC"
  - "VTS_PICTURE"
  - "VTS_FONT"
  - "VTS_XPOS_HIMETRIC"
  - "VTS_XPOS_PIXELS"
  - "VTS_XSIZE_HIMETRIC"
  - "VTS_YPOS_PIXELS"
  - "VTS_TRISTATE"
  - "VTS_HANDLE"
  - "VTS_YSIZE_HIMETRIC"
  - "VTS_COLOR"
  - "VTS_OPTEXCLUSIVE"
  - "VTS_YSIZE_PIXELS"
  - "VTS_XSIZE_PIXELS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Variant (constantes de datos)"
  - "Variant"
  - "Variant, constantes de tipo de parámetro"
  - "VTS_COLOR (constante)"
  - "VTS_FONT (constante)"
  - "VTS_HANDLE (constante)"
  - "VTS_OPTEXCLUSIVE (constante)"
  - "VTS_PICTURE (constante)"
  - "VTS_TRISTATE (constante)"
  - "VTS_XPOS_HIMETRIC (constante)"
  - "VTS_XPOS_PIXELS (constante)"
  - "VTS_XSIZE_HIMETRIC (constante)"
  - "VTS_XSIZE_PIXELS (constante)"
  - "VTS_YPOS_HIMETRIC (constante)"
  - "VTS_YPOS_PIXELS (constante)"
  - "VTS_YSIZE_HIMETRIC (constante)"
  - "VTS_YSIZE_PIXELS (constante)"
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# Constantes de tipo de par&#225;metro Variant
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema muestra las nuevas constantes que indican los tipos de parámetro variables diseñados para el uso con las clases de controles activex MFC \(Microsoft Foundation Class\).  
  
 A continuación se muestra una lista de constantes de clase:  
  
##  <a name="_mfc_variant_data_constants"></a> Constantes de datos variables  
  
-   Entero de 32 bits de**VTS\_COLOR**A utilizado para representar un valor de color RGB.  
  
-   Puntero de**VTS\_FONT**A la interfaz de **IFontDisp** de un objeto OLE de la fuente.  
  
-   **VTS\_HANDLE** un valor de identificador de Windows.  
  
-   Puntero de**VTS\_PICTURE**A la interfaz de `IPictureDisp` de un objeto OLE de la imagen.  
  
-   Valor de 16 bits de**VTS\_OPTEXCLUSIVE**A utilizado para un control diseñado para utilizarse en un grupo de controles, como botones de radio.  Este tipo indica a contenedor que si un control en un grupo tiene un valor de **VERDADERO** , todos los demás se deben **FALSE**.  
  
-   Entero de 16 bits de**VTS\_TRISTATE**A utilizado para las propiedades que pueden tener uno de los tres valores posibles \(seleccionados, borrado, no disponible, por ejemplo, una casilla.  
  
-   Entero sin signo de 32 bits de**VTS\_XPOS\_HIMETRIC**A utiliza para representar una posición a lo largo del eje X en unidades de **HIMETRIC** .  
  
-   Entero sin signo de 32 bits de**VTS\_YPOS\_HIMETRIC**A utiliza para representar una posición a lo largo del eje Y en unidades de **HIMETRIC** .  
  
-   Entero sin signo de 32 bits de**VTS\_XPOS\_PIXELS**A utiliza para representar una posición a lo largo del eje X en píxeles.  
  
-   Entero sin signo de 32 bits de**VTS\_YPOS\_PIXELS**A utiliza para representar una posición a lo largo del eje Y en píxeles.  
  
-   Entero sin signo de 32 bits de**VTS\_XSIZE\_PIXELS**A utilizado para representar el ancho de un objeto de pantalla en píxeles.  
  
-   Entero sin signo de 32 bits de**VTS\_YSIZE\_PIXELS**A utilizado para representar el alto de un objeto de pantalla en píxeles.  
  
-   Entero sin signo de 32 bits de**VTS\_XSIZE\_HIMETRIC**A utilizado para representar el ancho de un objeto de la pantalla en unidades de **HIMETRIC** .  
  
-   Entero sin signo de 32 bits de**VTS\_YSIZE\_HIMETRIC**A utilizado para representar el alto de un objeto de la pantalla en unidades de **HIMETRIC** .  
  
    > [!NOTE]
    >  Las constantes variables adicionales se han definido para todos los tipos variables, a excepción de **VTS\_FONT** y de **VTS\_PICTURE**, que proporcionan un puntero a la constante de datos variant.  Estas constantes siguen la convención de **VTS\_P**`constantname` .  Por ejemplo, **VTS\_PCOLOR** es un puntero a una constante de **VTS\_COLOR** .  
  
## Requisitos  
 **Encabezado:** afxdisp.h  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)