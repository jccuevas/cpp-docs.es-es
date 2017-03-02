---
title: Compilador advertencia (nivel 1) C4274 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4274
dev_langs:
- C++
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: fbba1e6dde180e77afe7ed8960849ee8cc0fd108
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4274"></a>Compilador advertencia (nivel 1) C4274
\#Ident omitida; Consulte la documentación de #pragma comment (exestr, 'string')  
  
 La `#ident` directiva, que inserta una cadena especificada por el usuario en el objeto o archivo ejecutable, está en desuso. Por consiguiente, el compilador omite la directiva.  
  
> [!CAUTION]
>  Advertencia C4274 aconseja utilizar la [#pragma comment (exestr, 'string')](../../preprocessor/comment-c-cpp.md) (directiva). Sin embargo, este Consejo está desusado y se revisarán en una versión futura del compilador. Si utiliza la `#pragma` la directiva, la herramienta del vinculador (LINK.exe) omite el registro de comentario producido por la directiva y emite la advertencia [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). En lugar de la `#ident` directiva, se recomienda que utilice una cadena de recurso de la versión de archivo en la aplicación.  
  
## <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Quitar el `#ident "` *cadena* `"` directiva.  
  
## <a name="see-also"></a>Vea también  
 [Comment (C/C ++)](../../preprocessor/comment-c-cpp.md)   
 [Herramientas del vinculador LNK4229 de advertencia](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)   
 [Trabajar con archivos de recursos](../../windows/working-with-resource-files.md)
