---
title: Clases de plantillas de documentos
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: dffde80093f98fc1c81a6c20dfaf92b82e3b4c78
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618984"
---
# <a name="document-template-classes"></a>Clases de plantillas de documentos

Los objetos de plantilla de documento coordinan la creación de objetos de documentos, vistas y ventanas de marco cuando se crea un nuevo documento o vista.

[CDocTemplate](reference/cdoctemplate-class.md)<br/>
La clase base para las plantillas de documento. Nunca usará esta clase directamente; en su lugar, se usa una de las otras clases de plantilla de documento derivadas de esta clase.

[CMultiDocTemplate](reference/cmultidoctemplate-class.md)<br/>
Plantilla para documentos en la interfaz de múltiples documentos (MDI). Las aplicaciones MDI pueden tener varios documentos abiertos a la vez.

[CSingleDocTemplate](reference/csingledoctemplate-class.md)<br/>
Una plantilla para documentos en la interfaz de un único documento (SDI). Las aplicaciones SDI solo tienen un documento abierto a la vez.

## <a name="related-class"></a>Clase relacionada

[CCreateContext](reference/ccreatecontext-structure.md)<br/>
Estructura pasada por una plantilla de documento a las funciones de creación de ventanas para coordinar la creación de objetos de documento, vista y ventana de marco.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
