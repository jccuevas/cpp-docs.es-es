---
title: FreeLibrary y AfxFreeLibrary | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
dev_langs:
- C++
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d5f2c1cce980f97e7a99ff2347daceac05f984f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary y AfxFreeLibrary
Procesos que se vinculan explícitamente a una llamada DLL el [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188) funcionar cuando el módulo del archivo DLL ya no es necesario. Esta función disminuye recuento de referencias del módulo y, si el recuento de referencias es cero, elimina la asignación del espacio de direcciones del proceso.  
  
 En una aplicación MFC, utilice [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) en lugar de `FreeLibrary` para descargar un archivo DLL de extensión MFC. La interfaz (prototipo de función) para `AfxFreeLibrary` es el mismo que `FreeLibrary`.  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Cómo vincular implícitamente a un archivo DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Determinar qué método de vinculación para usar](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [LoadLibrary y AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)   
 [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)   
 [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)