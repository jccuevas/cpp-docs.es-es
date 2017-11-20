---
title: Acceso a argumentos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.arguments
dev_langs: C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c216c009d84771fdf34426b6121a89eb4b3f73e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="argument-access"></a>Acceso a argumentos
Las macros `va_arg`, `va_end` y `va_start` proporcionan acceso a argumentos de función cuando el número de argumentos es variable. Estas macros se definen en STDARG.H para la compatibilidad con ANSI C y en VARARGS.H para la compatibilidad con System V de UNIX.  
  
### <a name="argument-access-macros"></a>Macros de acceso a argumentos  
  
|Macro|Uso|  
|-----------|-------------------------------|  
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Recuperar argumentos de una lista|  
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Restablecer el puntero|  
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Establecer el puntero al principio de la lista de argumentos|  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)