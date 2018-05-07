---
title: Error de línea de comandos D8045 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8045
dev_langs:
- C++
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cf1248c072374cbe65d74136dfd1a8680e483b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-error-d8045"></a>Error de la línea de comandos D8045
no se puede compilar el archivo de C 'archivo' con la opción /clr  
  
 Sólo archivos de código de C++ fuente pueden pasarse a una compilación que utilice **/CLR**.  Use **/TP** para compilar un archivo .c como un archivo .cpp; vea [/TC, /Tp, / TC, /TP (especificar el tipo del archivo de origen)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) para obtener más información.  
  
 Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 También puede producirse el error D8045 si compila una aplicación ATL con Visual C++. Vea [Cómo: migrar a/CLR](../../dotnet/how-to-migrate-to-clr.md) para obtener más información.