---
title: Las herramientas del vinculador LNK4237 advertencia | Microsoft Docs
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
ms.openlocfilehash: fcc109fe3ccf06e0461deed449517850271a2024
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39209396"
---
# <a name="linker-tools-warning-lnk4237"></a>Advertencia de las herramientas del vinculador LNK4237
/ SUBSYSTEM: Native especificada al importar desde 'dll'; Utilice/SUBSYSTEM: Console o/SUBSYSTEM: Windows.  
  
 [/ SUBSYSTEM: Native](../../build/reference/subsystem-specify-subsystem.md) se especificó al generar una aplicación de windows (Win32) que utiliza directamente uno o varios de los siguientes:  
  
-   kernel32.dll  
  
-   Gdi32.dll  
  
-   user32.dll  
  
-   uno de lo msvcrt\* archivos DLL.  
  
 Resolver esta advertencia mediante la especificación no **/SUBSYSTEM: Native**.