---
title: "Error irrecuperable C1189 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1189"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1189"
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1189
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#error : mensaje de error suministrado por el usuario  
  
 La directiva `#error` genera el error C1189.  El desarrollador que codifica la directiva especifica el texto del mensaje de error.  Para obtener más información, vea [\#error \(Directiva\)](../../preprocessor/hash-error-directive-c-cpp.md).  
  
 El ejemplo siguiente genera el error C1189.  En el ejemplo, el desarrollador emite un mensaje de error personalizado porque no se define el identificador `_WIN32`:  
  
```  
// C1189.cpp  
#undef _WIN32  
#if !defined(_WIN32)  
#error _WIN32 must be defined   // C1189  
#endif  
```  
  
 Este error también podría aparecer si compila un proyecto ATL mediante la opción del compilador MIDL **\/robust**.  Utilice el modificador **\/robust** para compilar sólo [!INCLUDE[win2kfamily](../../c-runtime-library/includes/win2kfamily_md.md)] y versiones posteriores de Windows.  Para corregir este error, utilice uno de los siguientes procedimientos:  
  
-   Cambie esta línea en el archivo dlldatax.c:  
  
```  
#define _WIN32_WINNT 0x0400   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
 a:  
  
```  
#define _WIN32_WINNT 0x0500   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
-   Use la página de propiedades **Avanzadas** en la carpeta de la página de propiedades **MIDL** para quitar el modificador **\/robust** y especificar, a continuación, el modificador **\/no\_robust**.  Para obtener más información, vea [Páginas de propiedades MIDL: Avanzadas](../../ide/midl-property-pages-advanced.md).  
  
## Vea también  
 [\#define \(Directiva\)](../../preprocessor/hash-define-directive-c-cpp.md)