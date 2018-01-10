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
ms.workload: cplusplus
ms.openlocfilehash: 97db036822687936f3f8e4084c065c8ec64ca23e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="argument-access"></a>Acceso a argumentos
Las macros `va_arg`, `va_end` y `va_start` proporcionan acceso a argumentos de función cuando el número de argumentos es variable. Estas macros se definen en STDARG.H para la compatibilidad con ANSI C y en VARARGS.H para la compatibilidad con System V de UNIX.  
  
### <a name="argument-access-macros"></a>Macros de acceso a argumentos  
  
|Macro|Usar|  
|-----------|-------------------------------|  
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Recuperar argumentos de una lista|  
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Restablecer el puntero|  
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Establecer el puntero al principio de la lista de argumentos|  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)