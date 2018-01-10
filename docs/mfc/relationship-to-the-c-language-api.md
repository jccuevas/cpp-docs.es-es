---
title: "Relación con la API del lenguaje C | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.mfc
dev_langs: C++
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 26458242ab6afcf69d6e70065ba70e31f0adbe74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="relationship-to-the-c-language-api"></a>Relación con la API del lenguaje C
La característica única que establece la biblioteca (Microsoft Foundation Classes) además de otras bibliotecas de clases para Windows es la asignación muy próxima a la API de Windows escritos en el lenguaje C. Además, puede mezclar generalmente llamadas a la biblioteca de clases libremente con llamadas directas a la API de Windows. Este acceso directo, sin embargo, implica que las clases son un reemplazo completo para la API. Los desarrolladores ocasionalmente deben realizar llamadas directas a algunas funciones de Windows, como [SetCursor](http://msdn.microsoft.com/library/windows/desktop/ms648393) y [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385), por ejemplo. Una función de Windows se ajusta mediante una función de miembro de clase solo cuando hay una ventaja clara para hacerlo.  
  
 Dado que a veces es necesario realizar llamadas de función nativo de Windows, debe tener acceso a la documentación de API de Windows del lenguaje C. Esta documentación se incluye con Microsoft Visual C++.  
  
> [!NOTE]
>  Para obtener información general de cómo funciona el marco de trabajo de la biblioteca MFC, vea [usar las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
## <a name="see-also"></a>Vea también  
 [Filosofía general de diseño de clases](../mfc/general-class-design-philosophy.md)
