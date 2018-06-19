---
title: Salida de clases (contexto de dispositivo) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.output
dev_langs:
- C++
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85571e2173d9dc4e900d63e982a91571fafc103e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350489"
---
# <a name="output-device-context-classes"></a>Clases de resultados (Contexto de dispositivo)
Estas clases encapsulan los diferentes tipos de contextos de dispositivo disponibles en Windows.  
  
 La mayoría de las clases siguientes encapsula un identificador para un contexto de dispositivo de Windows. Un contexto de dispositivo es un objeto de Windows que contiene información sobre los atributos de dibujo de un dispositivo, como una pantalla o una impresora. Todas las llamadas de dibujo se realizan a través de un objeto de contexto de dispositivo. Las clases más derivadas de `CDC` encapsulan la funcionalidad especializada del contexto de dispositivo, incluida la compatibilidad con metarchivos de Windows.  
  
 [CDC](../mfc/reference/cdc-class.md)  
 La clase base para contextos de dispositivo. Usar directamente para tener acceso a la pantalla completa y para tener acceso a los contextos de nondisplay como las impresoras.  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)  
 Un contexto de presentación que se usan en `OnPaint` las funciones miembro de windows. Llama automáticamente a `BeginPaint` durante la construcción y `EndPaint` en la destrucción.  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)  
 Un contexto de presentación de las áreas de cliente de windows. Se utiliza, por ejemplo, para dibujar en una respuesta inmediata a los eventos del mouse.  
  
 [Objetos CWindowDC](../mfc/reference/cwindowdc-class.md)  
 Un contexto de presentación de windows completos, incluidas las áreas cliente y cliente.  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)  
 Un contexto de dispositivo para metarchivos de Windows. Un metarchivo de Windows contiene una secuencia de comandos de dispositivo gráfico (GDI) de la interfaz que se pueden reproducir para crear una imagen. Las llamadas realizadas a las funciones miembro de un `CMetaFileDC` se registran en un metarchivo.  
  
## <a name="related-classes"></a>Clases relacionadas  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 Contiene pares de coordenadas (x, y).  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 Contiene valores emparejados, posiciones relativas o distancia.  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 Contiene coordenadas de áreas rectangulares.  
  
 [CRgn](../mfc/reference/crgn-class.md)  
 Encapsula una región GDI para manipular un área elíptico, poligonal o irregular dentro de una ventana. Usar junto con las funciones de miembro de recorte en clase `CDC`.  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 Muestra y administra la interfaz de usuario para cambiar el tamaño y mover objetos rectangulares.  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 Proporciona un cuadro de diálogo para seleccionar un color.  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 Proporciona un cuadro de diálogo para seleccionar una fuente.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Proporciona un cuadro de diálogo estándar para imprimir un archivo.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

