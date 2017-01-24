---
title: "CL invoca el vinculador | Microsoft Docs"
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
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador) [C++], compilar sin vincular"
  - "cl.exe (compilador) [C++], controlar el vinculador"
  - "compilar código fuente [C++], sin vincular"
  - "invocar al vinculador desde el compilador"
  - "LINK (herramienta) [C++], invocar desde el compilador CL"
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CL invoca el vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Salvo que se use la opción \/c, CL invocará automáticamente el vinculador una vez finalizada la compilación.  CL pasará al vinculador los nombres de los archivos .obj creados durante la compilación, así como de cualquier otro archivo que se especifique en la línea de comandos.  El vinculador usará las opciones enumeradas en la variable de entorno LINK.  Se puede usar la opción \/link para especificar opciones del vinculador en la línea de comandos de CL.  Las opciones que sigan a \/link reemplazarán a las de la variable de entorno LINK.  Las opciones de la tabla siguiente suprimen la vinculación:  
  
|Opción|Descripción|  
|------------|-----------------|  
|\/c|Compila sin vincular|  
|\/E, \/EP, \/P|Preprocesa sin compilar o vincular|  
|\/Zg|Genera prototipos de función|  
|\/Zs|Comprueba la sintaxis|  
  
 Si desea más detalles sobre la vinculación, vea [Opciones del vinculador](../../build/reference/linker-options.md).  
  
## Ejemplo  
 Suponga que está compilando tres archivos de código fuente de C: MAIN.c, MOD1.c y MOD2.c.  Cada archivo incluye una llamada a una función definida en un archivo diferente:  
  
-   MAIN.c llama a la función `func1` de MOD1.c y a la función `func2` de MOD2.c.  
  
-   MOD1.c llama a las funciones de biblioteca estándar `printf_s` y `scanf_s`.  
  
-   MOD2.c llama a las funciones de gráficos `myline` y `mycircle`, definidas en la biblioteca MYGRAPH.lib.  
  
 Para generar el programa, compile con la siguiente línea de comandos:  
  
```  
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib  
```  
  
 CL compila en primer lugar los archivos de código fuente en C y crea los archivos de objetos MAIN.obj, MOD1.obj y MOD2.obj.  El compilador sitúa el nombre de la biblioteca estándar en todos los archivos .obj.  Para obtener información detallada, vea [Utilizar la biblioteca en tiempo de ejecución](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
 CL pasa al vinculador los nombres de los archivos .obj, junto con el nombre de MYGRAPH.lib.  El vinculador resuelve las referencias externas de la siguiente manera:  
  
1.  En MAIN.obj, la referencia a `func1` se resuelve con la definición de MOD1.obj; la referencia a `func2` se resuelve con la definición de MOD2.obj.  
  
2.  En MOD1.obj, las referencias a `printf_s` y `scanf_s` se resuelven usando las definiciones de la biblioteca que el vinculador encuentre mencionadas en MOD1.obj.  
  
3.  En MOD2.obj, las referencias a `myline` y `mycircle` se resuelven con las definiciones de MYGRAPH.lib.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)