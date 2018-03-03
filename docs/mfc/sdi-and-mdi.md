---
title: SDI y MDI | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7109651bc250f83d8ee7e162b647ef54dd5308d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sdi-and-mdi"></a>SDI y MDI
MFC simplifica la a trabajar con la interfaz de único documento (SDI) y las aplicaciones de interfaz de múltiples documentos (MDI).  
  
 SDI (aplicaciones) permiten solo una ventana de marco de documento abierto a la vez. Las aplicaciones MDI permiten documento varias ventanas de marco esté abierto en la misma instancia de una aplicación. Una aplicación MDI tiene una ventana dentro de qué MDI varias ventanas secundarias, que son ventanas de marco por sí mismos, pueden abrirse, que contiene un documento independiente. En algunas aplicaciones, las ventanas secundarias pueden ser de tipos diferentes, como ventanas de gráfico y las ventanas de hoja de cálculo. En ese caso, la barra de menús puede cambiar cuando se activan ventanas secundarias MDI de diferentes tipos.  
  
> [!NOTE]
>  En Windows 95 y versiones posteriores, las aplicaciones suelen SDI porque el sistema operativo ha adoptado una vista "centrado en documentos".  
  
 Para obtener más información, consulte [documentos, vistas y el marco de trabajo](../mfc/documents-views-and-the-framework.md).  
  
## <a name="see-also"></a>Vea también  
 [Uso de las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
