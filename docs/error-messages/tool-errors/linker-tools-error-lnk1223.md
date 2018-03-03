---
title: Las herramientas del vinculador LNK1223 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c330077e8de73b8eeb71b0a418eb89d2ec0ebfdc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1223"></a>Error de las herramientas del vinculador LNK1223
archivo no válido o dañado: el archivo contiene contribuciones .pdata no válidas  
  
 En el caso de plataformas RISC que utilizan pdata, este error se produce si el compilador generó una sección .pdata con entradas no ordenadas.  
  
 Para corregir este problema, intente compilarla sin [/GL (optimización de todo el programa)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) habilitado. Los cuerpos de función vacíos también pueden producir este error en algunos casos.