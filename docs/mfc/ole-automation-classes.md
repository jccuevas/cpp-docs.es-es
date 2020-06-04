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
ms.openlocfilehash: 644a4930eb55636ba6e87b949ed610b725334661
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447683"
---
# <a name="ole-automation-classes"></a>Clases de Automation OLE

Estas clases son compatibles con los clientes de automatización (aplicaciones que controlan otras aplicaciones). Los servidores de automatización (aplicaciones que pueden controlar otras aplicaciones) se admiten a través de las [asignaciones de envío](../mfc/reference/dispatch-maps.md).

[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)<br/>
Se usa para llamar a los servidores de automatización desde el cliente de Automation. Al agregar una clase, esta clase se utiliza para crear clases con seguridad de tipos para los servidores de automatización que proporcionan una biblioteca de tipos.

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Excepción que se produce a causa de un error durante la automatización OLE. Los servidores de automatización producen las excepciones de automatización y las detectan los clientes de automatización.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)
