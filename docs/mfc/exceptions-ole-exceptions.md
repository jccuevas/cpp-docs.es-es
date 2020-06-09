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
ms.openlocfilehash: 7bd0b0cb2c9eb6fe49356ae8fd4602676d54fa66
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622783"
---
# <a name="exceptions-ole-exceptions"></a>Excepciones: Excepciones OLE

Las técnicas y las funciones para controlar las excepciones en OLE son las mismas que para controlar otras excepciones. Para obtener más información sobre el control de excepciones, vea el artículo [procedimientos recomendados de C++ moderno para excepciones y control de errores](../cpp/errors-and-exception-handling-modern-cpp.md).

Todos los objetos de excepción se derivan de la clase base abstracta `CException` . MFC proporciona dos clases para controlar las excepciones OLE:

- [COleException](reference/coleexception-class.md) Para controlar las excepciones OLE generales.

- [COleDispatchException](reference/coledispatchexception-class.md) Para generar y administrar excepciones de envío OLE (automatización).

La diferencia entre estas dos clases es la cantidad de información que proporcionan y dónde se usan. `COleException`tiene un miembro de datos público que contiene el código de estado OLE para la excepción. `COleDispatchException`proporciona más información, incluidas las siguientes:

- Un código de error específico de la aplicación

- Una descripción del error, como "disco lleno"

- Un contexto de ayuda que la aplicación puede usar para proporcionar información adicional para el usuario.

- Nombre del archivo de ayuda de la aplicación.

- El nombre de la aplicación que generó la excepción

`COleDispatchException`proporciona más información para que se pueda usar con productos como Microsoft Visual Basic. La descripción del error verbal puede usarse en un cuadro de mensaje o en otra notificación. la información de ayuda se puede usar para ayudar al usuario a responder a las condiciones que produjeron la excepción.

Dos funciones globales corresponden a las dos clases de excepción OLE: [AfxThrowOleException](reference/exception-processing.md#afxthrowoleexception) y [AfxThrowOleDispatchException](reference/exception-processing.md#afxthrowoledispatchexception). Úselos para producir excepciones OLE generales y excepciones de envío OLE, respectivamente.

## <a name="see-also"></a>Consulte también

[Control de excepciones](exception-handling-in-mfc.md)
