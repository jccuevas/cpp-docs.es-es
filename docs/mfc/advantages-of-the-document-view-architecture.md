---
title: Ventajas de la arquitectura de vista-documento | Documentos de Microsoft
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
ms.openlocfilehash: 45065b38128a2e3239b1fd10ded490fdcbcb3eac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="advantages-of-the-documentview-architecture"></a>Ventajas de la arquitectura documento/vista
La ventaja clave de la arquitectura documento/vista MFC es que la arquitectura admite varias vistas del mismo documento particularmente bien. (Si no necesita varias vistas y la mínima sobrecarga de documento/vista es excesiva en su aplicación, puede evitar la arquitectura. [Alternativas a la arquitectura documento/vista](../mfc/alternatives-to-the-document-view-architecture.md).)  
  
 Suponga que la aplicación permite a los usuarios ver datos numéricos en forma de hoja de cálculo o en forma de gráfico. Un usuario podría ser aconsejable ver simultáneamente tanto los datos sin procesar, en formato de hoja de cálculo y un gráfico que es el resultado de los datos. Mostrar estas vistas independientes en ventanas de marco distintas o en paneles divisores dentro de una sola ventana. Ahora suponga que el usuario puede editar los datos en la hoja de cálculo y ver los cambios reflejados instantáneamente en el gráfico.  
  
 En MFC, se basa la vista de hoja de cálculo y la vista de gráfico en distintas clases derivadas de CView. Ambas vistas estarían asociados a un objeto de documento único. El documento almacena los datos (o quizás obtiene de una base de datos). Ambas vistas tengan acceso al documento y mostrar los datos que se recuperan de ella.  
  
 Cuando un usuario actualiza una de las vistas, que ver llamadas del objeto `CDocument::UpdateAllViews`. Esa función avisa a todas las vistas del documento y cada vista se actualiza automáticamente con los datos más recientes del documento. La única llamada a `UpdateAllViews` sincroniza las distintas vistas.  
  
 Este escenario sería difícil código sin la separación de datos de vista, especialmente si las vistas almacenan los datos propios. Con el documento/vista, es fácil. El marco de trabajo realiza la mayor parte del trabajo de coordinación para usted.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Alternativas al documento/vista](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [CDocument](../mfc/reference/cdocument-class.md)  
  
-   [CView](../mfc/reference/cview-class.md)  
  
-   [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)  
  
-   [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura documento/vista](../mfc/document-view-architecture.md)

