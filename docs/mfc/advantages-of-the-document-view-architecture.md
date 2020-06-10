---
title: Ventajas de la arquitectura de vista-documento
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: 80f7141ec62d509defdea361586399bd375df0d1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623275"
---
# <a name="advantages-of-the-documentview-architecture"></a>Ventajas de la arquitectura documento/vista

La principal ventaja de utilizar la arquitectura de documento y vista de MFC es que la arquitectura admite varias vistas del mismo documento. (Si no necesita varias vistas y la pequeña sobrecarga de documento o vista es excesiva en la aplicación, puede evitar la arquitectura. [Alternativas a la arquitectura documento/vista](alternatives-to-the-document-view-architecture.md)).

Supongamos que la aplicación permite a los usuarios ver datos numéricos en un formulario de hoja de cálculo o en un gráfico. Es posible que un usuario desee ver simultáneamente los datos sin procesar, en el formulario de la hoja de cálculo y un gráfico que resulte de los datos. Estas vistas independientes se muestran en ventanas de marco independientes o en paneles divisores dentro de una sola ventana. Ahora Supongamos que el usuario puede editar los datos de la hoja de cálculo y ver los cambios reflejados al instante en el gráfico.

En MFC, la vista de hoja de cálculo y la vista de gráfico se basarían en distintas clases derivadas de CView. Ambas vistas se asociarían a un solo objeto de documento. El documento almacena los datos (o quizás los obtiene de una base de datos). Ambas vistas acceden al documento y muestran los datos que recuperan de ella.

Cuando un usuario actualiza una de las vistas, el objeto de vista llama a `CDocument::UpdateAllViews` . Esa función notifica a todas las vistas del documento y cada vista se actualiza con los datos más recientes del documento. La única llamada a `UpdateAllViews` sincroniza las distintas vistas.

Este escenario sería difícil de codificar sin la separación de datos de la vista, especialmente si las vistas almacenaban los datos. Con documento o vista, es fácil. El marco de trabajo realiza la mayoría de las tareas de coordinación.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Alternativas a documento/vista](alternatives-to-the-document-view-architecture.md)

- [CDocument](reference/cdocument-class.md)

- [CView](reference/cview-class.md)

- [CDocument:: UpdateAllViews](reference/cdocument-class.md#updateallviews)

- [CView:: GetDocument](reference/cview-class.md#getdocument)

## <a name="see-also"></a>Consulte también

[Arquitectura documento/vista](document-view-architecture.md)
