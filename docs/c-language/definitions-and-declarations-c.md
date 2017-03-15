---
title: "Definiciones y declaraciones (C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exportar funciones"
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Definiciones y declaraciones (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 La interfaz DLL hace referencia a todos los elementos \(funciones y datos\) que se sabe que se van a exportar mediante algún programa del sistema, es decir, todos los elementos declarados como **dllimport** o `dllexport`.  Todas las declaraciones incluidas en la interfaz DLL deben especificar el atributo **dllimport** o `dllexport`.  Sin embargo, la definición solo puede especificar el atributo `dllexport`.  Por ejemplo, la definición de función siguiente genera un error del compilador:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllImport int func()    /* Error; dllimport prohibited in */  
                        /* definition. */  
{  
   return 1;  
}  
```  
  
 Este código también genera un error:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllImport int i = 10;      /* Error; this is a definition. */  
```  
  
 Sin embargo, esta es la sintaxis correcta:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport int i = 10;      /* Okay: this is an export definition. */  
```  
  
 El uso de `dllexport` implica una definición, mientras que **dllimport** implica una declaración.  Debe utilizar la palabra clave `extern` con `dllexport` para forzar una declaración; en caso contrario, se asume una definición.  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
extern DllImport int k;   /* These are correct and imply */  
Dllimport int j;          /* a declaration. */      
```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Funciones de importación y exportación de archivos DLL](../c-language/dll-import-and-export-functions.md)