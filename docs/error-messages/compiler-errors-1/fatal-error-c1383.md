---
title: Error irrecuperable C1383 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1383
dev_langs:
- C++
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24e9d7652c96c84f94bafbf2c808f2e5430037b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1383"></a>Error irrecuperable C1383
la opción /GL del compilador es incompatible con la versión instalada de Common Language Runtime  
  
 El error C1383 se genera si utiliza una versión anterior de Common Language Runtime con un compilador más reciente y cuando se compila con **/clr** y **/GL.**  
  
 Para solucionarlo, no utilice **/GL** con **/clr** o instale la versión de Common Language Runtime que se distribuía con su compilador.  
  
 Para obtener más información, consulte [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) y [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md).