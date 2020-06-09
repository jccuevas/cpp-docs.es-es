---
title: Clases de resultados (Contexto de dispositivo)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.output
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
ms.openlocfilehash: b15f5034604f9d6b67574288140b79b144692478
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615358"
---
# <a name="output-device-context-classes"></a>Clases de resultados (Contexto de dispositivo)

Estas clases encapsulan los distintos tipos de contextos de dispositivo disponibles en Windows.

La mayoría de las clases siguientes encapsulan un identificador a un contexto de dispositivo de Windows. Un contexto de dispositivo es un objeto de Windows que contiene información sobre los atributos de dibujo de un dispositivo, como una pantalla o una impresora. Todas las llamadas de dibujo se realizan a través de un objeto de contexto de dispositivo. Otras clases derivadas de `CDC` encapsular la funcionalidad especializada de contexto de dispositivo, incluida la compatibilidad con los metaarchivos de Windows.

[CDC](reference/cdc-class.md)<br/>
La clase base para los contextos de dispositivo. Se usa directamente para obtener acceso a toda la presentación y para obtener acceso a los contextos no mostrados, como las impresoras.

[CPaintDC](reference/cpaintdc-class.md)<br/>
Un contexto de presentación utilizado en `OnPaint` funciones miembro de Windows. Llama automáticamente a `BeginPaint` en la construcción y `EndPaint` en la destrucción.

[CClientDC](reference/cclientdc-class.md)<br/>
Un contexto de presentación para las áreas de cliente de Windows. Se utiliza, por ejemplo, para dibujar en una respuesta inmediata a los eventos del mouse.

[CWindowDC](reference/cwindowdc-class.md)<br/>
Un contexto de presentación para todas las ventanas, incluidas las áreas cliente y no cliente.

[CMetaFileDC](reference/cmetafiledc-class.md)<br/>
Un contexto de dispositivo para los metaarchivos de Windows. Un metarchivo de Windows contiene una secuencia de comandos de la interfaz de dispositivo gráfico (GDI) que se pueden reproducir para crear una imagen. Las llamadas realizadas a las funciones miembro de un `CMetaFileDC` se registran en un metarchivo.

## <a name="related-classes"></a>Clases relacionadas

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Contiene pares de coordenadas (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Contiene la distancia, las posiciones relativas o los valores emparejados.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Contiene las coordenadas de las áreas rectangulares.

[CRgn](reference/crgn-class.md)<br/>
Encapsula una región GDI para manipular una zona elíptica, poligonal o irregular dentro de una ventana. Se usa junto con las funciones miembro de recorte de la clase `CDC` .

[CRectTracker](reference/crecttracker-class.md)<br/>
Muestra y controla la interfaz de usuario para cambiar el tamaño y mover objetos rectangulares.

[CColorDialog](reference/ccolordialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para seleccionar un color.

[CFontDialog](reference/cfontdialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para seleccionar una fuente.

[CPrintDialog](reference/cprintdialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para imprimir un archivo.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
