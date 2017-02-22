---
title: "Error de la l&#237;nea de comandos D8045 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D8045"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D8045"
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error de la l&#237;nea de comandos D8045
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede compilar el archivo de C 'archivo' con la opción \/clr  
  
 Sólo pueden pasarse archivos de código fuente de C\+\+ a una compilación que utilice **\/clr**.  Utilice **\/TP** para compilar un archivo .c como un archivo .cpp; vea [\/Tc, \/Tp, \/TC, \/TP \(Especificar el tipo de archivo de código fuente\)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) para obtener más información.  
  
 Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 También puede producirse el error D8045 si compila una aplicación ATL con Visual C\+\+.  Para obtener más información, vea [Cómo: Migrar a \/clr](../../dotnet/how-to-migrate-to-clr.md).