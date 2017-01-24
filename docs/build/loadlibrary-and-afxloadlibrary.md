---
title: "LoadLibrary y AfxLoadLibrary | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LoadLibrary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxLoadLibrary (método)"
  - "DLL [C++], AfxLoadLibrary"
  - "DLL [C++], LoadLibrary"
  - "vinculación explícita [C++]"
  - "LoadLibrary (método)"
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LoadLibrary y AfxLoadLibrary
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los procesos llaman a [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187) \(o [AfxLoadLibrary](../Topic/AfxLoadLibrary.md)\) para vincularse explícitamente a un archivo DLL.  Si la función es correcta, asigna el archivo DLL especificado al espacio de direcciones del proceso de llamada y devuelve un identificador al archivo DLL que se puede utilizar con otras funciones en la vinculación explícita, por ejemplo `GetProcAddress` y `FreeLibrary`.  
  
 `LoadLibrary` intenta encontrar el archivo DLL mediante la misma secuencia de búsqueda que se utiliza para la vinculación implícita.  Si el sistema no encuentra el archivo DLL o la función de punto de entrada devuelve el valor FALSE, `LoadLibrary` devolverá el valor NULL.  Si la llamada a `LoadLibrary` especifica un módulo de DLL que se asignó al espacio de direcciones del proceso de llamada, la función devuelve un identificador del archivo DLL e incrementa la cuenta de referencia del módulo.  
  
 Si el archivo DLL tiene una función de punto de entrada, el sistema operativo llamará a la función en el contexto del subproceso que llamó a `LoadLibrary`.  No se llamará a la función de punto de entrada si el archivo DLL ya está adjunto al proceso a causa de una llamada anterior a `LoadLibrary` que no tiene una llamada correspondiente a la función `FreeLibrary`.  
  
 Para las aplicaciones MFC que cargan archivos DLL de extensión, se recomienda usar `AfxLoadLibrary` en lugar de `LoadLibrary`.  `AfxLoadLibrary` administra la sincronización de subprocesos antes de la llamada a `LoadLibrary`.  La interfaz \(prototipo de función\) a `AfxLoadLibrary` es la misma que para `LoadLibrary`.  
  
 Si Windows no puede cargar el archivo DLL, el proceso podría intentar recuperarse del error.  Por ejemplo, podría notificar el error al usuario y pedirle que especifique otra ruta de acceso al archivo DLL.  
  
> [!IMPORTANT]
>  Si el código se va a ejecutar con Windows NT 4, Windows 2000 o Windows XP \(anterior a SP1\), asegúrese de especificar la ruta de acceso de las DLL.  En estos sistemas operativos, se busca primero en el directorio actual cuando se cargan archivos.  Si no proporciona la ruta de acceso calificada del archivo, es posible que se cargue un archivo que no sea el que se pensó.  
  
## ¿Qué desea hacer?  
  
-   [Vincular de forma implícita](../build/linking-implicitly.md)  
  
-   [Determinar el método de vinculación que se va a utilizar](../build/determining-which-linking-method-to-use.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [La ruta de acceso de búsqueda que Windows utiliza para buscar un archivo DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [FreeLibrary y AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)   
 [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)   
 [AfxLoadLibrary](../Topic/AfxLoadLibrary.md)