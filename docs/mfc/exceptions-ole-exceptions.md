---
title: 'Excepciones: Excepciones OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: 1606a0f5a86996345e12024cf6416afdf6bdc82b
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246704"
---
# <a name="exceptions-ole-exceptions"></a>Excepciones: Excepciones OLE

Las técnicas y las funciones para controlar las excepciones en OLE son las mismas que para controlar otras excepciones. Para más información sobre el control de excepciones, consulte el artículo [procedimientos recomendados modernos C++ para excepciones y control de errores](../cpp/errors-and-exception-handling-modern-cpp.md).

Todos los objetos de excepción se derivan de la clase base abstracta `CException`. MFC proporciona dos clases para controlar las excepciones OLE:

- [COleException](../mfc/reference/coleexception-class.md) Para controlar las excepciones OLE generales.

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) Para generar y administrar excepciones de envío OLE (automatización).

La diferencia entre estas dos clases es la cantidad de información que proporcionan y dónde se usan. `COleException` tiene un miembro de datos público que contiene el código de estado OLE para la excepción. `COleDispatchException` proporciona más información, incluidas las siguientes:

- Un código de error específico de la aplicación

- Una descripción del error, como "disco lleno"

- Un contexto de ayuda que la aplicación puede usar para proporcionar información adicional para el usuario.

- Nombre del archivo de ayuda de la aplicación.

- El nombre de la aplicación que generó la excepción

`COleDispatchException` proporciona más información para que se pueda usar con productos como Microsoft Visual Basic. La descripción del error verbal puede usarse en un cuadro de mensaje o en otra notificación. la información de ayuda se puede usar para ayudar al usuario a responder a las condiciones que produjeron la excepción.

Dos funciones globales corresponden a las dos clases de excepción OLE: [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception) y [AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Úselos para producir excepciones OLE generales y excepciones de envío OLE, respectivamente.

## <a name="see-also"></a>Vea también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
