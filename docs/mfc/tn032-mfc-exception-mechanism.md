---
title: 'TN032: Mecanismo de excepciones de MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.exceptions
dev_langs:
- C++
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aee8ce02af874e1c3c30243a35e8f36acfce63f0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414763"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: Mecanismo de excepciones de MFC

Las versiones anteriores de Visual C++ no eran compatibles con el mecanismo de excepción estándar de C++ y MFC proporciona macros **TRY/CATCH/THROW** que se usaron en su lugar. Esta versión de Visual C++ es totalmente compatible con las excepciones de C++. Esta nota trata algunos de los detalles de implementación avanzada de las macros anteriores e incluye información para la limpieza de objetos basado en pilas automáticamente. Dado que las excepciones de C++ admiten pila desenredo de forma predeterminada, esta nota técnica ya no es necesaria.

Consulte [excepciones: uso de Macros de MFC y excepciones de C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) para obtener más información sobre las diferencias entre las macros MFC y las nuevas palabras clave de C++.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

