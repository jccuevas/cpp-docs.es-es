---
title: Las herramientas del vinculador LNK1223 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e50d29af6ac563fadd3a52e5b1d3d15201289083
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1223"></a>Error de las herramientas del vinculador LNK1223
archivo no válido o dañado: el archivo contiene contribuciones .pdata no válidas  
  
 En el caso de plataformas RISC que utilizan pdata, este error se produce si el compilador generó una sección .pdata con entradas no ordenadas.  
  
 Para corregir este problema, intente compilarla sin [/GL (optimización de todo el programa)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) habilitado. Los cuerpos de función vacíos también pueden producir este error en algunos casos.