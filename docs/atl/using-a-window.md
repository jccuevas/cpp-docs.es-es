---
title: Uso de una ventana (ATL) | Documentos de Microsoft
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
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a2be573e10190b385274de9afab498c77a094550
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-a-window"></a>Uso de una ventana
Clase [CWindow](../atl/reference/cwindow-class.md) le permite usar una ventana. Una vez que se adjunta una ventana a un `CWindow` objeto, a continuación, puede llamar a `CWindow` métodos para manipular la ventana. `CWindow`También contiene un `HWND` operador que se va a convertir un `CWindow` el objeto a un `HWND`. Por lo tanto puede pasar un `CWindow` objeto a cualquier función que requiera un identificador de una ventana. Puede mezclar fácilmente `CWindow` llamadas a métodos y las llamadas de función de Win32, sin crear ningún objeto temporal.  
  
 Dado que `CWindow` tiene solo dos miembros de datos (un identificador de ventana y las dimensiones predeterminadas), no impone ninguna sobrecarga en el código. Además, muchas de las `CWindow` métodos simplemente encapsulan las funciones de API de Win32 correspondientes. Mediante el uso de `CWindow`, el `HWND` miembro se pasa automáticamente a la función de Win32.  
  
 Además de usar `CWindow` directamente, también puede derivar de él para agregar datos o código a la clase. ATL deriva tres clases de `CWindow`: [CWindowImpl](../atl/implementing-a-window.md), [CDialogImpl](../atl/implementing-a-dialog-box.md), y [CContainedWindowT](../atl/using-contained-windows.md).  
  
## <a name="see-also"></a>Vea también  
 [Clases de ventana](../atl/atl-window-classes.md)

