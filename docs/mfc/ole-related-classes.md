---
title: Clases relacionadas con OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: dfcc07b3fbd0c5badce8e397f4d52bc7d8d3028c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447605"
---
# <a name="ole-related-classes"></a>Clases relacionadas con OLE

Estas clases proporcionan una serie de servicios diferentes, que van desde excepciones hasta archivos de entrada y salida.

[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)<br/>
Se usa para crear elementos cuando se solicita desde otros contenedores. Esta clase actúa como la clase base para tipos de generadores más específicos, incluido `COleTemplateServer`.

[COleMessageFilter](../mfc/reference/colemessagefilter-class.md)<br/>
Se usa para administrar la simultaneidad con llamadas a procedimiento remoto ligero OLE (LRPC).

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
Usa la interfaz de `IStream` COM para proporcionar `CFile` acceso a los archivos compuestos. Esta clase (derivada de `CFile`) permite a la serialización de MFC utilizar el almacenamiento estructurado OLE.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Se usa para permitir el movimiento, el cambio de tamaño y la reorientación de los elementos en contexto.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)
