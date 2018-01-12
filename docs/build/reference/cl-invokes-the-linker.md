---
title: CL invoca el vinculador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cl
dev_langs: C++
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 32a3bdd1e227b894ca5a32ddfaa8c46a478a19f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cl-invokes-the-linker"></a>CL invoca el vinculador
CL invoca automáticamente el vinculador después de compilar a menos que se utiliza la opción /c. CL pasa al vinculador los nombres de los archivos .obj creados durante la compilación y los nombres de cualquier otro archivo especificado en la línea de comandos. El vinculador usará las opciones enumeradas en la variable de entorno LINK. Puede usar la opción para especificar las opciones del vinculador en la línea de comandos de CL. Opciones que siguen a la opción reemplazan a las que en la variable de entorno LINK. Las opciones en la tabla siguiente suprimen la vinculación.  
  
|Opción|Descripción|  
|------------|-----------------|  
|/c|Compilar sin vincular|  
|/ /P E, /EP,|Preprocesa sin compilar o vincular|  
|/Zg|Generar prototipos de función|  
|/Zs|Compruebe la sintaxis|  
  
 Para obtener más información acerca de la vinculación, vea [opciones del vinculador](../../build/reference/linker-options.md).  
  
## <a name="example"></a>Ejemplo  
 Se supone que está compilando los archivos de código fuente de C tres: MAIN.c, MOD1.c y MOD2.c. Cada archivo incluye una llamada a una función definida en un archivo diferente:  
  
-   MAIN.c llama a la función `func1` en MOD1.c y la función `func2` de MOD2.c.  
  
-   MOD1.c llama a las funciones de biblioteca estándar `printf_s` y `scanf_s`.  
  
-   MOD2.c llama a las funciones gráficos `myline` y `mycircle`, que se definen en la biblioteca MYGRAPH.lib.  
  
 Para compilar este programa, compile con la siguiente línea de comandos:  
  
```  
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib  
```  
  
 En primer lugar CL compila los archivos de código fuente de C y crea los archivos de objetos MAIN.obj, MOD1.obj y MOD2.obj. El compilador coloca el nombre de la biblioteca estándar en cada archivo obj. Para obtener más información, consulte [utilizar la biblioteca en tiempo de ejecución](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
 CL pasa los nombres de los archivos .obj, junto con el nombre de MYGRAPH.lib al vinculador. El vinculador resuelve las referencias externas de la siguiente manera:  
  
1.  En MAIN.obj, la referencia a `func1` se resuelve mediante la definición de MOD1.obj; la referencia a `func2` se resuelve con la definición de MOD2.obj.  
  
2.  En MOD1.obj, las referencias a `printf_s` y `scanf_s` se resuelven usando las definiciones de la biblioteca que el vinculador encuentre mencionada en MOD1.obj.  
  
3.  En MOD2.obj, las referencias a `myline` y `mycircle` se resuelven con las definiciones de MYGRAPH.lib.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)