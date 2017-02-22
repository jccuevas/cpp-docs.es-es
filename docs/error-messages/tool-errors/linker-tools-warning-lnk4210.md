---
title: "Advertencia de las herramientas del vinculador LNK4210 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4210"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4210"
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Advertencia de las herramientas del vinculador LNK4210
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la sección sección existe; podría haber terminadores o inicializadores estáticos no controlados  
  
 Una parte del código ha introducido inicializadores o terminadores estáticos, pero CRT o su equivalente \(que debe ejecutarlos\) no estaba en ejecución al iniciarse la aplicación.  Ejemplos de código que podrían causar esto:  
  
-   Variable de clase global con un constructor, un destructor o una tabla de función virtual.  
  
-   Variable global inicializada con una constante sin tiempo de compilación.  
  
 Para corregir este problema, realice una de las acciones siguientes:  
  
-   Quite todo el código que contenga inicializadores estáticos.  
  
-   No utilice [\/NOENTRY](../../build/reference/noentry-no-entry-point.md).  Después de quitar \/NOENTRY, tal vez tenga que agregar msvcrt.lib, libcmt.lib o libcmtd.lib a la línea de comandos del vinculador.  
  
-   Agregue msvcrt.lib, libcmt.lib o libcmtd.lib a la línea de comandos del vinculador.  
  
-   Al pasar de la compilación \/clr:pure a \/clr, quite la opción [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) de la línea del vinculador.  Esto habilitará la inicialización de CRT, que permite ejecutar los inicializadores estáticos en el inicio de la aplicación.  
  
-   Si el proyecto se compila con [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) y si a \/ENTRY se pasa una función que no sea `_DllMainCRTStartup`, la función debe llamar a CRT\_INIT.  Vea [Comportamiento de la biblioteca en tiempo de ejecución](../../build/run-time-library-behavior.md) y el artículo Q94248 de Knowledge Base, [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;94248](http://support.microsoft.com/default.aspx?scid=kb;en-us;94248) para obtener más información.  
  
 La opción del compilador [\/GS](../../build/reference/gs-buffer-security-check.md) requiere código de inicio de la biblioteca CRT.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)