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
ms.openlocfilehash: 1d76570e7bfd4ce587b3803235394ec5406d30b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410205"
---
# <a name="output-device-context-classes"></a>Clases de resultados (Contexto de dispositivo)

Estas clases encapsulan los diferentes tipos de contextos de dispositivo disponibles en Windows.

La mayoría de las clases siguientes encapsula un identificador de un contexto de dispositivo de Windows. Un contexto de dispositivo es un objeto de Windows que contiene información sobre los atributos de dibujo de un dispositivo, como una pantalla o una impresora. Todas las llamadas de dibujos se realizan a través de un objeto de contexto de dispositivo. Las clases más derivadas de `CDC` encapsulan la funcionalidad especializada del contexto de dispositivo, incluida la compatibilidad con metarchivos de Windows.

[CDC](../mfc/reference/cdc-class.md)<br/>
La clase base para los contextos de dispositivo. Utilizar directamente para tener acceso a la pantalla completa y obtener acceso a los contextos de nondisplay como las impresoras.

[CPaintDC](../mfc/reference/cpaintdc-class.md)<br/>
Utilizado en un contexto de presentación `OnPaint` funciones miembro de windows. Llama automáticamente a `BeginPaint` durante la construcción y `EndPaint` en la destrucción.

[CClientDC](../mfc/reference/cclientdc-class.md)<br/>
Un contexto de presentación de las áreas de cliente de windows. Se usa, por ejemplo, para dibujar en una respuesta inmediata a los eventos del mouse.

[CWindowDC](../mfc/reference/cwindowdc-class.md)<br/>
Un contexto de presentación de windows completos, incluidas las áreas cliente y el cliente.

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md)<br/>
Un contexto de dispositivo para metarchivos de Windows. Un metarchivo de Windows contiene una secuencia de comandos de interfaz (GDI) de dispositivo de gráficos que puede reproducirse para crear una imagen. Las llamadas realizadas a las funciones miembro de un `CMetaFileDC` se registran en un metarchivo.

## <a name="related-classes"></a>Clases relacionadas

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Contiene pares de coordenadas (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Contiene valores emparejados, posiciones relativas o distancia.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Contiene las coordenadas de áreas rectangulares.

[CRgn](../mfc/reference/crgn-class.md)<br/>
Encapsula una región GDI para manipular un área elíptico, poligonal o irregular dentro de una ventana. Usar junto con las funciones de miembro de recorte en la clase `CDC`.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Muestra y administra la interfaz de usuario para cambiar el tamaño y mover objetos rectangulares.

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para seleccionar un color.

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para seleccionar una fuente.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para imprimir un archivo.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
