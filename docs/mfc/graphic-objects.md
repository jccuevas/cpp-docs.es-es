---
title: "Objetos gr&#225;ficos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "HRGN"
  - "HFONT"
  - "HBITMAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de bits [C++], crear en contextos de dispositivo"
  - "pinceles, crear en contexto de dispositivo"
  - "CBitmap (clase), tipo de controlador HBITMAP"
  - "CBrush (clase), tipo de controlador HBRUSH"
  - "CFont (clase), tipo de controlador HFONT"
  - "CPalette (clase), tipo de controlador HPALETTE"
  - "CPen (clase), tipo de controlador HPEN"
  - "CRgn (clase), tipo de controlador HRGN"
  - "contextos de dispositivo, objetos gráficos"
  - "dibujar, en contextos de dispositivo"
  - "fuentes [C++], crear en contexto de dispositivo"
  - "GDI [C++], clases de objeto gráfico"
  - "objetos GDI [C++]"
  - "objetos GDI [C++], clases de objeto gráfico"
  - "objetos gráficos"
  - "objetos gráficos, crear en contexto de dispositivo"
  - "HBITMAP y la clase CBitmap"
  - "HBRUSH y la clase CBrush"
  - "HFONT y la clase CFont"
  - "HPALETTE y la clase CPalette"
  - "HPEN"
  - "HRGN"
  - "imágenes [C++], objetos gráficos"
  - "memoria [C++], contextos de presentación"
  - "MFC, objetos gráficos"
  - "objetos [C++], gráfico"
  - "objetos [C++], objetos gráficos"
  - "dibujar y contexto de dispositivo"
  - "objetos de paleta"
  - "paletas, crear en contexto de dispositivo"
  - "objetos de lápiz"
  - "lápices, crear en contexto de dispositivo"
  - "objetos de región"
  - "regiones, crear en contexto de dispositivo"
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Objetos gr&#225;ficos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Windows proporciona diversas herramientas de dibujo que se usan en contextos de dispositivo.  Incluye lápices para trazar líneas, pinceles para rellenar interiores y fuentes para dibujar texto.  MFC proporciona clases de objetos gráficos que equivalen a las herramientas de dibujo de Windows.  En la siguiente tabla se recogen las clases disponibles y los tipos de identificador de Interfaz de dispositivo gráfico \(GDI\) de Windows equivalentes.  
  
> [!NOTE]
>  GDI\+ se incluye con Windows XP y está disponible como componente redistribuible para Windows NT 4.0 SP6, Windows 2000, Windows 98 y Windows Millennium Edition.  Para descargar el último componente redistribuible, vea [http:\/\/www.microsoft.com\/msdownload\/platformsdk\/sdkupdate\/psdkredist.htm](http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdkredist.htm).  Para obtener más información, vea la documentación del SDK de GDI\+ en MSDN: [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/gdicpp\/GDIPlus\/GDIPlus.asp](http://msdn.microsoft.com/library/default.asp?url=/library/gdicpp/GDIPlus/GDIPlus.asp).  
  
 En este artículo se explica el uso de estas clases de objetos gráficos:  
  
### Clases de objetos GDI de Windows  
  
|Clase|Tipo de identificador de Windows|  
|-----------|--------------------------------------|  
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|  
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|  
|[CFont](../mfc/reference/cfont-class.md)|**HFONT**|  
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|  
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|  
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|  
  
> [!NOTE]
>  La clase [CImage](../atl-mfc-shared/reference/cimage-class.md) proporciona una mejor compatibilidad con los mapas de bits.  
  
 Cada clase de objeto gráfico en la biblioteca de clases tiene un constructor que permite crear objetos gráficos de esa clase. Este constructor se tiene que inicializar con la función de creación adecuada, como, por ejemplo, `CreatePen`.  
  
 Cada clase de objeto gráfico en la biblioteca de clases tiene un operador de conversión que convierte un objeto MFC en el identificador de Windows asociado.  El identificador resultante es válido hasta que el objeto asociado lo desconecta.  Use la función miembro **Detach** del objeto para desconectar el identificador.  
  
 El siguiente código convierte un objeto `CPen` en un identificador de Windows:  
  
 [!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/CPP/graphic-objects_1.cpp)]  
  
#### Para crear un objeto gráfico en un contexto de dispositivo  
  
1.  Defina un objeto gráfico en el marco de pila.  Inicialice el objeto con la función de creación específica del tipo, como `CreatePen`.  Como alternativa, inicialice el objeto en el constructor.  Vea la explicación en el tema de [creación en una fase y en dos fases](../mfc/one-stage-and-two-stage-construction-of-objects.md), donde encontrará un código de ejemplo.  
  
2.  [Seleccione el objeto en el contexto de dispositivo actual](../mfc/selecting-a-graphic-object-into-a-device-context.md), procurando guardar el objeto gráfico anterior que estaba seleccionado.  
  
3.  Cuando termine con el objeto gráfico actual, seleccione el objeto gráfico anterior en el contexto de dispositivo para restaurar su estado.  
  
4.  Deje que el objeto gráfico asignado por el marco se elimine automáticamente cuando salga del ámbito.  
  
> [!NOTE]
>  Si va a usar un objeto gráfico repetidamente, puede asignarlo una vez y seleccionarlo en un contexto de dispositivo cada vez que lo necesite.  Asegúrese de eliminar este objeto cuando ya no lo necesite.  
  
### ¿Qué más desea saber?  
  
-   [Creación de objetos en una fase y en dos fases](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [Ejemplo de creación de un lápiz en una y dos fases](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [Seleccionar un objeto gráfico en un contexto de dispositivo](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [Contextos de dispositivo](../mfc/device-contexts.md)  
  
-   [Limitaciones de CImage con sistemas operativos anteriores](../mfc/cimage-limitations-with-earlier-operating-systems.md)  
  
## Vea también  
 [Window \(Objetos\)](../mfc/window-objects.md)