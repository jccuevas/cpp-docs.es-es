---
title: "Error de línea de comandos D8045 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D8045
dev_langs:
- C++
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9489535e0a1f9873d2c299ae8a9766bcbb5035dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-error-d8045"></a>Error de la línea de comandos D8045
no se puede compilar el archivo de C 'archivo' con la opción /clr  
  
 Sólo archivos de código de C++ fuente pueden pasarse a una compilación que utilice **/CLR**.  Use **/TP** para compilar un archivo .c como un archivo .cpp; vea [/TC, /Tp, / TC, /TP (especificar el tipo del archivo de origen)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) para obtener más información.  
  
 Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 También puede producirse el error D8045 si compila una aplicación ATL con Visual C++. Vea [Cómo: migrar a/CLR](../../dotnet/how-to-migrate-to-clr.md) para obtener más información.