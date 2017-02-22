---
title: "Clases de resultados (Contexto de dispositivo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.output"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contextos de dispositivo, clases"
  - "clases de salida"
  - "clases para dibujar"
  - "clases de impresión"
  - "clases de resultados en pantalla"
  - "clases de ventana de dibujo"
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de resultados (Contexto de dispositivo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases encapsulan los diferentes tipos de contextos de dispositivo disponibles en Windows.  
  
 La mayoría de las clases siguientes encapsulan un identificador a un contexto de dispositivo de Windows.  Un contexto de dispositivo es un objeto de Windows que contiene información sobre los atributos del gráfico de un dispositivo como una pantalla o una impresora.  Todas las llamadas del gráfico se hace a través de un objeto de dispositivo\- contexto.  Clases adicionales derivadas de `CDC` encapsulan la funcionalidad especializada de dispositivo\- contexto, con compatibilidad con metarchivos de Windows.  
  
 [CDC](../mfc/reference/cdc-class.md)  
 La clase base de los contextos de dispositivo.  Utilice directamente para tener acceso a la pantalla de conjunto y tener acceso a los contextos nondisplay como impresoras.  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)  
 Un contexto de presentación utilizado en funciones miembro de `OnPaint` de ventanas.  Llama automáticamente a `BeginPaint` en la construcción y `EndPaint` en destrucción.  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)  
 Un contexto de presentación para las áreas de cliente de las ventanas.  Utilizado, por ejemplo, para dibujar en una respuesta inmediata a eventos del mouse.  
  
 [CWindowDC](../mfc/reference/cwindowdc-class.md)  
 Un contexto de presentación para las ventanas completas, incluidas las áreas cliente y no cliente de.  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)  
 Un contexto para metarchivos de Windows.  Un metarchivo de Windows contiene un script de \(GDI\) de la interfaz de dispositivo gráfico que puedan volver a consultars para crear una imagen.  Las llamadas realizadas a las funciones miembro de `CMetaFileDC` se registran en un metarchivo.  
  
## Clases relacionadas  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 Contiene las coordenadas \(x, y\) los pares.  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 Contiene distancia, posiciones relativas, o valores emparejados.  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 Contiene coordenadas de áreas rectangulares.  
  
 [CRgn](../mfc/reference/crgn-class.md)  
 Encapsula una región de GDI para manipular un área elíptico, poligonal, o irregular dentro de una ventana.  Se utiliza junto con el miembro de recorte funciona en la clase `CDC`.  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 Muestra y administra la interfaz de usuario para cambiar el tamaño y mover objetos rectangulares.  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 Proporciona un cuadro de diálogo estándar para seleccionar color.  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 Proporciona un cuadro de diálogo estándar para seleccionar una fuente.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Proporciona un cuadro de diálogo estándar para imprimir un archivo.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)