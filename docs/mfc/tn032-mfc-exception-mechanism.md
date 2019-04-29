---
title: 'TN032: Mecanismo de excepciones de MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.exceptions
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 210e47e117cd602ba77edd330205385f54199ce5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305663"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: Mecanismo de excepciones de MFC

Las versiones anteriores de Visual C++ no eran compatibles con el mecanismo de excepción estándar de C++ y MFC proporciona macros **TRY/CATCH/THROW** que se usaron en su lugar. Esta versión de Visual C++ es totalmente compatible con las excepciones de C++. Esta nota trata algunos de los detalles de implementación avanzada de las macros anteriores e incluye información para la limpieza de objetos basado en pilas automáticamente. Dado que las excepciones de C++ admiten pila desenredo de forma predeterminada, esta nota técnica ya no es necesaria.

Consulte [excepciones: Uso de Macros de MFC y excepciones de C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) para obtener más información sobre las diferencias entre las macros MFC y las nuevas palabras clave de C++.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
