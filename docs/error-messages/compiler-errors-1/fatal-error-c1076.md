---
title: Error irrecuperable C1076 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1076
dev_langs:
- C++
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 617db809cfaeb4d0e0003a3dfc2e9568726b0c58
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1076"></a>Error irrecuperable C1076
límite del compilador : se ha alcanzado el límite del montón interno; utilice /Zm para especificar un límite más alto  
  
 Este error puede producirse por un exceso de símbolos o de instancias de la plantilla.  
  
 Para resolver este error:  
  
1.  Use la [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opción para establecer el límite de memoria del compilador en el valor especificado en el [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) mensaje de error. Para obtener más información que incluye cómo establecer este valor en [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)], vea la sección comentarios en [/Zm (especificar memoria asignación límite de encabezado precompilado)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).  
  
2.  Si usa los compiladores hospedados de 32 bits en un sistema operativo de 64 bits, utilice en su lugar los compiladores hospedados de 64 bits. Para obtener más información, consulte [Cómo: habilitar un 64-Bit Visual C++ Toolset en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).  
  
3.  Elimine los archivos de inclusión innecesarios.  
  
4.  Elimine las variables globales que no son necesarias (por ejemplo, asignando memoria dinámicamente, en lugar de declarar una matriz grande).  
  
5.  Elimine las declaraciones que no utilice.  
  
6.  Divida las funciones grandes en funciones más pequeñas.  
  
7.  Divida las clases grandes en clases más pequeñas.  
  
8.  Divida el archivo actual en archivos más pequeños.  
  
 Si el error C1076 se produce inmediatamente después de iniciarse la compilación, el valor especificado para **/Zm** probablemente es demasiado alto para el programa. Reducir el **/Zm** valor.