---
title: "Archivos de entrada de la elección del formato de archivo .netmodule | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0be66a528585bd86c4dbc39c17917229c3353bd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Elegir el formato de los archivos de entrada .netmodule
Un archivo MSIL .obj (compilado con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md)) también puede usarse como un archivo .netmodule.  los archivos .obj contienen metadatos y símbolos nativos.  archivos .netmodule sólo contienen metadatos.  
  
 Puede pasar un archivo MSIL .obj a cualquier otro compilador de Visual Studio a través de la opción del compilador/addmodule (pero tenga en cuenta que el archivo .obj pasa a formar parte del ensamblado resultante y se debe enviar con el ensamblado).  Por ejemplo, Visual C# y Visual Basic tienen la opción del compilador/addmodule.  
  
> [!NOTE]
>  En la mayoría de los casos, debe pasar al vinculador el archivo .obj desde la compilación que creó el módulo. NET.  Una excepción a esto es si se ha creado el archivo .netmodule con [/CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md).  Pasar un archivo de módulo de archivo .dll o .netmodule MSIL al vinculador puede producir el error LNK1107.  
  
 los archivos .obj, junto con sus archivos .h asociados, que se hace referencia a través de #include en origen, permiten que las aplicaciones de C++ utilizar los tipos nativos en el módulo, mientras que en un archivo .netmodule, solo los tipos administrados pueden utilizarse en una aplicación de C++.  Si intenta pasar un archivo .obj a #using, información sobre los tipos nativos no estará disponible; #include archivo .h del archivo .obj en su lugar.  
  
 Otros compiladores de Visual Studio solo pueden utilizar los tipos administrados desde un módulo.  
  
 Para determinar si necesita usar un archivo .netmodule o un archivo .obj como entrada de módulo al vinculador de Visual C++, utilice lo siguiente:  
  
-   Si está compilando con un compilador de Visual Studio distinto de Visual C++, genere un archivo .netmodule y úselo como entrada al vinculador.  
  
-   Si está utilizando el compilador de Visual C++ para crear módulos y si los módulos se usará para generar un valor distinto de una biblioteca, use los archivos .obj creados por el compilador como entrada de módulo al vinculador; No utilice el archivo .netmodule como entrada.  
  
-   Si los módulos se utilizará para generar una biblioteca nativa (no administrada), use archivos .obj como entrada de módulo al vinculador y genere un archivo de biblioteca .lib.  
  
-   Si los módulos que se utilizará para generar una biblioteca administrada y todas las entradas de módulo al vinculador será comprobable (generado con/CLR: safe), use archivos .obj como entrada de módulo al vinculador y generar un archivo .dll (ensamblado) o un archivo de biblioteca de .netmodule (módulo).  
  
-   Si los módulos que se utilizará para generar una biblioteca administrada y si todas las entradas de módulo al vinculador se producirán con **/CLR: pure** o **/CLR: safe**, use archivos .obj como entrada de módulo al vinculador y genere un (.dll ensamblado) o .netmodule (módulo) si sólo desea exponer tipos administrados de la biblioteca. Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015. Si desea exponer tipos administrados de la biblioteca y si también desea que las aplicaciones de C++ para utilizar los tipos nativos en la biblioteca, la biblioteca constará de los archivos .obj para los módulos de componente de bibliotecas (también deberá distribuir los archivos .h para cada módulo por lo que sí pueden hacer referencia con #include de código fuente).  
  
-   Si los módulos que se utilizará para generar una biblioteca administrada y si se generará una o varias entradas módulos del vinculador simplemente con/CLR, use archivos .obj como entrada de módulo al vinculador y genere un archivo .dll (ensamblado).  Si desea exponer tipos administrados de la biblioteca y si también desea que las aplicaciones de C++ para utilizar los tipos nativos en la biblioteca, la biblioteca constará de los archivos .obj para los módulos de componente de bibliotecas (también deberá distribuir los archivos .h para cada módulo por lo que sí pueden hacer referencia con #include de código fuente).  
  
## <a name="see-also"></a>Vea también  
 [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md)