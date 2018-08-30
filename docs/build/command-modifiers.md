---
title: Modificadores de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9e1d883e0c7a2b214842b096fdf697ffc7d0192
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221746"
---
# <a name="command-modifiers"></a>Modificadores de comandos
Puede especificar uno o varios modificadores de comandos anterior a un comando, opcionalmente, separado por espacios o tabulaciones. Al igual que con los comandos, se deben aplicar la sangría modificadores.  
  
|Modificador|Propósito|  
|--------------|-------------|  
|@*Comando*|Impide la presentación del comando. No se suprime la presentación mediante los comandos. De forma predeterminada, NMAKE repite todos los comandos ejecutados. Utilizar /S para suprimir la presentación de la totalidad del archivo MAKE; usar **. SILENCIOSA** para suprimir la presentación de la parte del archivo MAKE.|  
|**-**\[*número*] *comando*|Desactiva la comprobación de errores de *comando*. De forma predeterminada, NMAKE se detiene cuando un comando devuelva un código de salida distinto de cero. IF -*número* es utilizado, NMAKE se detiene si el código de salida supera *número*. No pueden haber espacios o tabulaciones entre el guión y *número.* Debe haber al menos un espacio o tabulación entre `number` y *comando*. Usar /I para desactivar la comprobación de errores para la totalidad del archivo MAKE; usar **. OMITIR** para desactivar la comprobación de errores de la parte del archivo MAKE.|  
|**!** *command*|Ejecuta *comando* para cada archivo dependiente si *comando* usa <strong>$ \* \*</strong> (todos los archivos dependientes en la dependencia) o **$?** (todos los archivos dependientes en la dependencia con una marca de tiempo posterior que el destino.)|  
  
## <a name="see-also"></a>Vea también  
 [Comandos en un archivo MAKE](../build/commands-in-a-makefile.md)