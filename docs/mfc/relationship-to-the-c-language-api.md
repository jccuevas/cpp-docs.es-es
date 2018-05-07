---
title: Relación con la API del lenguaje C | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d06c4adfa5493929a24c233fa923451c7bf0f95
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="relationship-to-the-c-language-api"></a>Relación con la API del lenguaje C
La característica única que establece la biblioteca (Microsoft Foundation Classes) además de otras bibliotecas de clases para Windows es la asignación muy próxima a la API de Windows escritos en el lenguaje C. Además, puede mezclar generalmente llamadas a la biblioteca de clases libremente con llamadas directas a la API de Windows. Este acceso directo, sin embargo, implica que las clases son un reemplazo completo para la API. Los desarrolladores ocasionalmente deben realizar llamadas directas a algunas funciones de Windows, como [SetCursor](http://msdn.microsoft.com/library/windows/desktop/ms648393) y [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385), por ejemplo. Una función de Windows se ajusta mediante una función de miembro de clase solo cuando hay una ventaja clara para hacerlo.  
  
 Dado que a veces es necesario realizar llamadas de función nativo de Windows, debe tener acceso a la documentación de API de Windows del lenguaje C. Esta documentación se incluye con Microsoft Visual C++.  
  
> [!NOTE]
>  Para obtener información general de cómo funciona el marco de trabajo de la biblioteca MFC, vea [usar las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
## <a name="see-also"></a>Vea también  
 [Filosofía general de diseño de clases](../mfc/general-class-design-philosophy.md)
