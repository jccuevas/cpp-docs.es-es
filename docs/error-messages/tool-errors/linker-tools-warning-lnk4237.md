---
title: Las herramientas del vinculador LNK4237 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4237
dev_langs:
- C++
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5acccf52d3738985c7a83432342952af03bf78b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4237"></a>Advertencia de las herramientas del vinculador LNK4237
/ SUBSYSTEM: Native especificado al importar desde 'dll'; Utilice /SUBSYSTEM:CONSOLE o/SUBSYSTEM: Windows.  
  
 [/ SUBSYSTEM: Native](../../build/reference/subsystem-specify-subsystem.md) se especificó al generar una aplicación de windows (Win32) que utiliza directamente uno o varios de los siguientes:  
  
-   kernel32.dll  
  
-   Gdi32.dll  
  
-   user32.dll  
  
-   uno de los archivos DLL msvcrt *.  
  
 Resolver esta advertencia, no especifica **/SUBSYSTEM: Native**.