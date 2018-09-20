---
title: Clases de plantillas de documentos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.document
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87984bf06d8ca178d2a21ac8ff475f828690668e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406066"
---
# <a name="document-template-classes"></a>Clases de plantillas de documentos

Objetos de plantilla de documento coordinan la creación de documento, vista y los objetos de ventana de marco cuando un documento nuevo o se crea la vista.

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
La clase base para las plantillas de documento. No se utiliza esta clase nunca directamente; en su lugar, use una de las otras clases de plantilla de documento derivadas de esta clase.

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
Una plantilla para los documentos de la interfaz de múltiples documentos (MDI). Las aplicaciones MDI pueden tener varios documentos abiertos a la vez.

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
Una plantilla para los documentos de la interfaz de único documento (SDI). Las aplicaciones SDI tienen solo un documento abierto a la vez.

## <a name="related-class"></a>Clase relacionada

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
Una estructura pasada por una plantilla de documento a las funciones de creación de ventanas para coordinar la creación de objetos de documento, vista y ventana de marco.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

