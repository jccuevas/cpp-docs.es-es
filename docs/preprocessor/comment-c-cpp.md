---
title: "comment (C/C++) | Microsoft Docs"
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
  - "vc-pragma.comment"
  - "comment_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "anotaciones [C++]"
  - "comment (pragma)"
  - "comentarios [C++], archivos compilados"
  - "pragma (directivas), comentario"
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# comment (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inserta un registro de comentario en un archivo objeto o ejecutable.  
  
## Sintaxis  
  
```  
  
#pragma comment( comment-type [,"commentstring"] )  
```  
  
## Comentarios  
 El elemento *comment\-type* es uno de los identificadores predefinidos \(se describe más adelante\), que especifica el tipo de registro del comentario.  El elemento `commentstring` opcional es un literal de cadena que proporciona información adicional para algunos tipos de comentario.  Dado que `commentstring` es un literal de cadena, obedece todas las reglas para los literales de cadena con respecto a los caracteres de escape, las comillas incrustadas \(**"**\) y la concatenación.  
  
 **compiler**  
 Coloca el nombre y número de versión del compilador en el archivo objeto.  El vinculador no tiene en cuenta este registro de comentario.  Si se proporciona un parámetro `commentstring` para este tipo de registro, el compilador genera una advertencia.  
  
 **exestr**  
 Coloca `commentstring` en el archivo objeto.  En el momento de la vinculación, esta cadena se coloca en el archivo ejecutable.  La cadena no se carga en memoria cuando se carga el archivo ejecutable; sin embargo, se puede encontrar con un programa que encuentre las cadenas imprimibles en los archivos.  Un uso para este tipo de registro de comentario es incrustar un número de versión o información similar en un archivo ejecutable.  
  
 `exestr` está desusado y se quitará en una futura versión; el vinculador no procesa el registro de comentario.  
  
 **lib**  
 Inserta un registro de búsqueda de biblioteca en el archivo objeto.  Este tipo de comentario debe ir acompañado de un parámetro `commentstring` que contenga el nombre \(y posiblemente la ruta de acceso\) de la biblioteca que desea que el vinculador busque.  El nombre de biblioteca sigue los registros de búsqueda de biblioteca predeterminados en el archivo objeto; el vinculador busca esta biblioteca como si se hubiera designado en la línea de comandos, siempre que la biblioteca no se especifique con [\/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md).  Puede colocar varios registros de búsqueda de biblioteca en el mismo archivo de código fuente; cada registro aparece en el archivo objeto en el mismo orden en el que se encuentra en el archivo de código fuente.  
  
 Si el orden de la biblioteca predeterminada y una biblioteca agregada es importante, la compilación con el modificador [\/Zl](../build/reference/zl-omit-default-library-name.md) evitará que el nombre de biblioteca predeterminado se sitúe en el módulo de objeto.  Entonces, se puede usar una segunda directiva pragma de comentario para insertar el nombre de biblioteca predeterminada después de la biblioteca agregada.  Las bibliotecas incluidas con estas directivas pragma aparecerán en el módulo de objeto en el mismo orden en que se encuentran en el código fuente.  
  
 **linker**  
 Coloca una [opción del vinculador](../build/reference/linker-options.md) en el archivo objeto.  Puede utilizar este tipo de comentario para especificar una opción del vinculador en lugar de pasarla a la línea de comandos o de especificarla en el entorno de desarrollo.  Por ejemplo, puede especificar la opción \/include para forzar la inclusión de un símbolo:  
  
```  
#pragma comment(linker, "/include:__mySymbol")  
```  
  
 Solo las siguientes opciones del vinculador \(*comment\-type*\) están disponibles para pasarlas al identificador del vinculador:  
  
-   [\/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)  
  
-   [\/EXPORT](../build/reference/export-exports-a-function.md)  
  
-   [\/INCLUDE](../build/reference/include-force-symbol-references.md)  
  
-   [\/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)  
  
-   [\/MERGE](../build/reference/merge-combine-sections.md)  
  
-   [\/SECTION](../build/reference/section-specify-section-attributes.md)  
  
 **usuario**  
 Coloca un comentario general en el archivo objeto.  El parámetro `commentstring` contiene el texto del comentario.  El vinculador no tiene en cuenta este registro de comentario.  
  
 La siguiente directiva pragma hace que el vinculador busque la biblioteca EMAPI.LIB durante la vinculación.  El vinculador busca primero en el directorio de trabajo actual y en la ruta de acceso especificada en la variable de entorno LIB.  
  
```  
#pragma comment( lib, "emapi" )  
```  
  
 La directiva pragma siguiente hace que el compilador coloque el nombre y el número de versión del compilador en el archivo objeto:  
  
```  
#pragma comment( compiler )  
```  
  
> [!NOTE]
>  Para los comentarios que toman un parámetro `commentstring`, se puede utilizar una macro en cualquier lugar donde utilizaría un literal de cadena, siempre que la macro se expanda a un literal de cadena.  También puede concatenar cualquier combinación de literales de cadena y macros que se expandan a literales de cadena.  Por ejemplo, la siguiente instrucción es aceptable:  
  
```  
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )   
```  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)