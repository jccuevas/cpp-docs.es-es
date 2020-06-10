---
title: Clases relacionadas con OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: 6f6db6ce133b440a5ed86e7c1642396888744540
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621034"
---
# <a name="ole-related-classes"></a>Clases relacionadas con OLE

Estas clases proporcionan una serie de servicios diferentes, que van desde excepciones hasta archivos de entrada y salida.

[COleObjectFactory](reference/coleobjectfactory-class.md)<br/>
Se usa para crear elementos cuando se solicita desde otros contenedores. Esta clase actúa como la clase base para tipos de generadores más específicos, incluido `COleTemplateServer` .

[COleMessageFilter](reference/colemessagefilter-class.md)<br/>
Se usa para administrar la simultaneidad con llamadas a procedimiento remoto ligero OLE (LRPC).

[COleStreamFile](reference/colestreamfile-class.md)<br/>
Utiliza la `IStream` interfaz com para proporcionar `CFile` acceso a los archivos compuestos. Esta clase (derivada de `CFile` ) permite que la serialización de MFC use el almacenamiento estructurado OLE.

[CRectTracker](reference/crecttracker-class.md)<br/>
Se usa para permitir el movimiento, el cambio de tamaño y la reorientación de los elementos en contexto.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
