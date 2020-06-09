---
title: Clases de Automation OLE
ms.date: 11/04/2016
helpviewer_keywords:
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
ms.openlocfilehash: 04cb93b8ce3699b579342d33c0dae77176878379
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625295"
---
# <a name="ole-automation-classes"></a>Clases de Automation OLE

Estas clases son compatibles con los clientes de automatización (aplicaciones que controlan otras aplicaciones). Los servidores de automatización (aplicaciones que pueden controlar otras aplicaciones) se admiten a través de las [asignaciones de envío](reference/dispatch-maps.md).

[COleDispatchDriver](reference/coledispatchdriver-class.md)<br/>
Se usa para llamar a los servidores de automatización desde el cliente de Automation. Al agregar una clase, esta clase se utiliza para crear clases con seguridad de tipos para los servidores de automatización que proporcionan una biblioteca de tipos.

[COleDispatchException](reference/coledispatchexception-class.md)<br/>
Excepción que se produce a causa de un error durante la automatización OLE. Los servidores de automatización producen las excepciones de automatización y las detectan los clientes de automatización.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
