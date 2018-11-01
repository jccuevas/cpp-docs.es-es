---
title: Ventajas de la arquitectura de vista-documento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 213fc108b11d6056df6696f92658e74a736c4a16
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392845"
---
# <a name="advantages-of-the-documentview-architecture"></a>Ventajas de la arquitectura documento/vista

La ventaja clave de la arquitectura documento/vista MFC es que la arquitectura admite varias vistas del mismo documento particularmente bien. (Si no necesita varias vistas y la mínima sobrecarga de documento/vista es excesiva en la aplicación, puede evitar la arquitectura. [Alternativas a la arquitectura documento/vista](../mfc/alternatives-to-the-document-view-architecture.md).)

Supongamos que la aplicación permite a los usuarios ver los datos numéricos en forma de hoja de cálculo o en forma de gráfico. Un usuario podría desear ver simultáneamente tanto los datos sin procesar, en formato de hoja de cálculo y un gráfico que es el resultado de los datos. Mostrar estas vistas independientes en ventanas de marco independiente o en paneles divisores dentro de una sola ventana. Ahora supongamos que el usuario puede editar los datos en la hoja de cálculo y vea los cambios reflejan al instante en el gráfico.

En MFC, la vista de la hoja de cálculo y la vista del gráfico podrían basarse en distintas clases derivadas de CView. Ambas vistas sería asociados a un objeto de documento único. El documento almacena los datos (o quizás los obtiene de una base de datos). Ambas vistas tengan acceso al documento y mostrar los datos que se recuperan de ella.

Cuando un usuario actualiza una de las vistas, que permite ver las llamadas de objeto `CDocument::UpdateAllViews`. Notifica a esa función de las vistas del documento y cada vista se actualiza con los datos más recientes del documento. La única llamada a `UpdateAllViews` sincroniza las distintas vistas.

Este escenario sería difícil de código sin la separación de datos de la vista, especialmente si las vistas almacenan los datos por sí mismos. Documento/vista, es fácil. El marco de trabajo realiza la mayor parte del trabajo de coordinación para usted.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Alternativas al documento/vista](../mfc/alternatives-to-the-document-view-architecture.md)

- [CDocument](../mfc/reference/cdocument-class.md)

- [CView](../mfc/reference/cview-class.md)

- [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)

- [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)

## <a name="see-also"></a>Vea también

[Arquitectura documento/vista](../mfc/document-view-architecture.md)

