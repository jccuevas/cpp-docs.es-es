---
title: Relación con la API de lenguaje C | Microsoft Docs
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
ms.openlocfilehash: f291a05b1347254989e4876af66c5d8137864020
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684166"
---
# <a name="relationship-to-the-c-language-api"></a>Relación con la API del lenguaje C
La única característica que establece la biblioteca Microsoft Foundation Class (MFC) además de otras bibliotecas de clases de Windows es la asignación muy similar a la API de Windows escrita en el lenguaje C. Además, puede mezclar con carácter general las llamadas a la biblioteca de clases libremente con llamadas directas a la API de Windows. Este acceso directo, sin embargo, implica que las clases son un reemplazo completo de dicha API. Los desarrolladores ocasionalmente deben realizar llamadas directas a algunas funciones de Windows, como [SetCursor](/windows/desktop/api/winuser/nf-winuser-setcursor) y [GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics), por ejemplo. Solo cuando hay una ventaja clara para hacerlo, se ajusta una función de Windows por una función miembro de clase.  
  
 Dado que a veces es necesario realizar llamadas de función nativas de Windows, debe tener acceso a la documentación de API de Windows del lenguaje C. Esta documentación se incluye con Microsoft Visual C++.  
  
> [!NOTE]
>  Para obtener información general de cómo funciona el marco de trabajo de la biblioteca MFC, vea [utilizando las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
## <a name="see-also"></a>Vea también  
 [Filosofía general de diseño de clases](../mfc/general-class-design-philosophy.md)
