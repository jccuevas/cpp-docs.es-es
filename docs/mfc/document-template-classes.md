---
title: Clases de plantillas de documentos
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 82b9ce4c242df7c85ada0722b2c1e993a0cf3f81
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446915"
---
# <a name="document-template-classes"></a>Clases de plantillas de documentos

Los objetos de plantilla de documento coordinan la creación de objetos de documentos, vistas y ventanas de marco cuando se crea un nuevo documento o vista.

[CDocTemplate (](../mfc/reference/cdoctemplate-class.md)<br/>
La clase base para las plantillas de documento. Nunca usará esta clase directamente; en su lugar, se usa una de las otras clases de plantilla de documento derivadas de esta clase.

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
Plantilla para documentos en la interfaz de múltiples documentos (MDI). Las aplicaciones MDI pueden tener varios documentos abiertos a la vez.

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
Una plantilla para documentos en la interfaz de un único documento (SDI). Las aplicaciones SDI solo tienen un documento abierto a la vez.

## <a name="related-class"></a>Clase relacionada

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
Estructura pasada por una plantilla de documento a las funciones de creación de ventanas para coordinar la creación de objetos de documento, vista y ventana de marco.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)
