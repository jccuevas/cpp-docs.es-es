---
title: Las herramientas del vinculador LNK4237 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4237
dev_langs:
- C++
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 718058dae02e9dfe9b653abea91993ec6662f5c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4237"></a>Advertencia de las herramientas del vinculador LNK4237
/ SUBSYSTEM: Native especificado al importar desde 'dll'; Utilice /SUBSYSTEM:CONSOLE o/SUBSYSTEM: Windows.  
  
 [/ SUBSYSTEM: Native](../../build/reference/subsystem-specify-subsystem.md) se especificó al generar una aplicación de windows (Win32) que utiliza directamente uno o varios de los siguientes:  
  
-   kernel32.dll  
  
-   Gdi32.dll  
  
-   user32.dll  
  
-   uno de los archivos DLL msvcrt *.  
  
 Resolver esta advertencia, no especifica **/SUBSYSTEM: Native**.