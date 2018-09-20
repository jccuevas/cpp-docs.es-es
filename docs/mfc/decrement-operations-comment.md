---
title: --Comentario operations | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73c4a7a70c9f2ed987337426793bd462c2a94309
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372501"
---
# <a name="-operations-comment"></a>// Operations (Comentario)

El `// Operations` sección de una declaración de clase MFC contiene funciones de miembro que se pueden llamar en el objeto para que sea lo ni realizar acciones (realizar operaciones). Estas funciones normalmente que no son de**const** porque normalmente tienen efectos secundarios. Pueden ser virtuales o no virtuales según las necesidades de la clase. Normalmente, estos miembros son públicos.

En el ejemplo de lista de clase `CStdioFile`, en [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md), la lista incluye dos funciones miembro bajo este comentario: `ReadString` y `WriteString`.

Al igual que con los atributos, las operaciones se pueden subdividir.

## <a name="see-also"></a>Vea también

[Uso de los archivos de código fuente de MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)<br/>
[Implementation (comentario)](../mfc/decrement-implementation-comment.md)<br/>
[Comentario de constructores](../mfc/decrement-constructors-comment.md)<br/>
[Comentario Attributes](../mfc/decrement-attributes-comment.md)<br/>
[Overridables (comentario)](../mfc/decrement-overridables-comment.md)

