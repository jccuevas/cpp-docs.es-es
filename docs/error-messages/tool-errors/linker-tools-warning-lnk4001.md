---
title: Las herramientas del vinculador LNK4001 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acf65c00c5c039769a05e009dcfe46ea42633ac4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4001"></a>Advertencia de las herramientas del vinculador LNK4001
ningún archivo objeto especificado; bibliotecas usadas  
  
 Uno o más archivos .lib, pero ningún archivo .obj, se pasó al vinculador.  
  
 Dado que el vinculador no es capaz de obtener acceso a información en un archivo .lib que puede tener acceso en un archivo .obj, esta advertencia indica que tendrá que especificar explícitamente otras opciones del vinculador. Por ejemplo, es podrán que deba especificar el [/máquina](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), o [/Entry](../../build/reference/entry-entry-point-symbol.md) opciones.