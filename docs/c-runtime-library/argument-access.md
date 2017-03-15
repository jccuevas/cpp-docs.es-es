---
title: "Acceso a argumentos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.arguments"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macros de acceso a argumentos [C++]"
  - "listas de argumentos de longitud variable"
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Acceso a argumentos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`va_arg`, `va_end`, y las macros de `va_start` proporcionan acceso a los argumentos de la función cuando el número de argumentos es variable.  Estas macros se definen en STDARG.H para la compatibilidad con ANSI C y en VARARGS.H para la compatibilidad con el sistema UNIX V.  
  
### Macros de Argumento\-Access  
  
|Macro|Utilice|Equivalente de .NET Framework|  
|-----------|-------------|-----------------------------------|  
|[va\_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Argumento de recuperación desde la lista|[\<caps:sentence id\="tgt9" sentenceid\="f260effcc218d99ea9ab361455fd493c" class\="tgtSentence"\>System::ParamArrayAttribute Class\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)|  
|[va\_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Puntero de reinicio|[\<caps:sentence id\="tgt12" sentenceid\="f260effcc218d99ea9ab361455fd493c" class\="tgtSentence"\>System::ParamArrayAttribute Class\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)|  
|[va\_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Establezca el puntero a iniciar de la lista de argumentos|[\<caps:sentence id\="tgt15" sentenceid\="f260effcc218d99ea9ab361455fd493c" class\="tgtSentence"\>System::ParamArrayAttribute Class\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)