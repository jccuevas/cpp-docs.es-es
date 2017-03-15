---
title: "Elegir el formato de los archivos de entrada .netmodule | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Elegir el formato de los archivos de entrada .netmodule
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un archivo de MSIL .obj \(compilado con [\/clr](../../build/reference/clr-common-language-runtime-compilation.md)\) también se puede utilizar como un archivo .netmodule.  Los archivos .obj contienen metadatos y símbolos nativos.  .netmodules solo contienen metadatos.  
  
 Se puede pasar un archivo MSIL .obj a cualquier otro compilador de Visual Studio mediante la opción del compilador \/addmodule \(pero tenga en cuenta que el archivo .obj pasa a formar parte del ensamblado resultante y se debe distribuir con el ensamblado\).  Por ejemplo, Visual C\# y Visual Basic tienen la opción del compilador \/addmodule.  
  
> [!NOTE]
>  En la mayoría de los casos, deberá pasar al vinculador el archivo .obj de compilación que creó el módulo de .net.  Una excepción a esto es si el .netmodule se creó con [\/clr: puro](../../build/reference/clr-common-language-runtime-compilation.md).  Pasar un archivo de módulo .dll o .netmodule MSIL al vinculador puede dar lugar a LNK1107.  
  
 archivos .obj, junto con sus archivos asociados .h, que hace referencia mediante \#include en origen, permiten a las aplicaciones de C\+\+ para utilizar tipos nativos en el módulo, mientras que en un archivo .netmodule, solo los tipos administrados se pueden utilizar en la aplicación de c\+\+.  Si intenta pasar un archivo .obj a \#using, la información sobre tipos nativos no estará disponible. En lugar de ello, utilice \#include con el archivo .h del archivo .obj.  
  
 Otros compiladores de Visual Studio sólo pueden utilizar tipos administrados desde un módulo.  
  
 Utilice para determinar si necesita utilizar un .netmodule o un archivo .obj como módulo entró en Visual C\+\+ el vinculador:  
  
-   Si compila con un compilador de Visual Studio distinta de Visual C\+\+, genere un .netmodule y utilice el .netmodule como entrada del vinculador.  
  
-   Si usa el compilador de Visual C\+\+ para generar los módulos y si los módulos se utilizan para compilar algo distinto de una biblioteca, use los archivos .obj generados por el compilador como módulo escrito al vinculador; no utilice el archivo .netmodule como entrada.  
  
-   Si se van a utilizar los módulos para crear una biblioteca nativa \(no una administrada\), use archivos .obj como entrada de módulo al vinculador y genere un archivo de biblioteca .lib.  
  
-   Si los módulos se utilizan para compilar una biblioteca administrada, y si toda la entrada del módulo al vinculador es comprobable \(generado con \/clr:safe\), archivos de uso .obj como entrada del módulo al vinculador y generar un archivo de biblioteca .dll \(ensamblado\) o .netmodule \(módulo\).  
  
-   Si los módulos se utilizan para compilar una biblioteca administrada, y si toda la entrada del módulo al vinculador genera con \/clr:pure o \/clr:safe, archivos de uso .obj como entrada del módulo al vinculador y generar un archivo .dll \(ensamblado\) o .netmodule \(módulo\) si solo desea exponer tipos administrados de la biblioteca.  Si desea exponer tipos administrados de la biblioteca y también que las aplicaciones de C\+\+ utilicen los tipos nativos de la biblioteca, ésta consistirá en los archivos .obj para los módulos de componentes de bibliotecas \(también querrá distribuir los archivos .h para cada módulo, para que se pueda hacer referencia a ellos con \#include desde el código fuente\).  
  
-   Si se van a utilizar los módulos para crear una biblioteca administrada y si la entrada de alguno de los módulos al vinculador se va a crear simplemente con \/clr, use archivos .obj como entrada de módulo al vinculador y genere un archivo .dll \(ensamblado\).  Si desea exponer tipos administrados de la biblioteca y también que las aplicaciones de C\+\+ utilicen los tipos nativos de la biblioteca, ésta consistirá en los archivos .obj para los módulos de componentes de bibliotecas \(también querrá distribuir los archivos .h para cada módulo, para que se pueda hacer referencia a ellos con \#include desde el código fuente\).  
  
## Vea también  
 [.Archivos netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md)