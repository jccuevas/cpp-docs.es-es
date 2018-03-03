---
title: Modificadores de comandos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 610725bf52522cd5041d2f6dcadb422bf942458a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="command-modifiers"></a>Modificadores de comandos
Puede especificar uno o varios de los modificadores de comandos precediendo a un comando, opcionalmente, separado por espacios o tabulaciones. Al igual que con los comandos, se deben aplicar la sangría modificadores.  
  
|Modificador|Propósito|  
|--------------|-------------|  
|@*comando*|Impide la presentación del comando. No se suprime la presentación mediante comandos. De forma predeterminada, NMAKE repite todos los comandos ejecutados. Utilizar /S para suprimir la presentación de la totalidad del archivo MAKE; usar **. SILENCIOSA** para suprimir la presentación de la parte del archivo MAKE.|  
|**-**[`number` ]*comando*|Desactiva la comprobación de errores de *comando*. De forma predeterminada, NMAKE se detiene si un comando devuelve un código de salida distinto de cero. IF -`number` es usa, NMAKE se detiene si el código de salida supera `number`. No pueden haber espacios ni tabulaciones entre el guión y *número.* Debe haber al menos un espacio o tabulación entre `number` y *comando*. Utilizar /I para desactivar la comprobación de errores para la totalidad del archivo MAKE; usar **. OMITIR** para desactivar la comprobación de errores de la parte del archivo MAKE.|  
|**!** *command*|Ejecuta *comando* para cada archivo dependiente si *comando* utiliza  **$ \* \***  (todos los archivos dependientes en la dependencia) o **$?** (todos los archivos dependientes existentes en la dependencia con una marca de tiempo posterior que el destino).|  
  
## <a name="see-also"></a>Vea también  
 [Comandos en un archivo MAKE](../build/commands-in-a-makefile.md)