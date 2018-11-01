---
title: comment (C/C++)
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: ec80e8cf177becdc25bdf49d6dfa9ad9c7794b88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612831"
---
# <a name="comment-cc"></a>comment (C/C++)

Inserta un registro de comentario en un archivo objeto o ejecutable.

## <a name="syntax"></a>Sintaxis

```
#pragma comment( comment-type [,"commentstring"] )
```

## <a name="remarks"></a>Comentarios

El *tipo de comentario* es uno de los identificadores predefinidos, se describe a continuación, que especifica el tipo de registro de comentario. El elemento opcional *commentstring* es un literal de cadena que proporciona información adicional para algunos tipos de comentario. Dado que *commentstring* es una cadena literal, obedece todas las reglas para los literales de cadena con respecto a los caracteres de escape, las comillas incrustadas (`"`) y concatenación.

### <a name="compiler"></a>compilador

Coloca el nombre y número de versión del compilador en el archivo objeto. El vinculador no tiene en cuenta este registro de comentario. Si proporciona un *commentstring* parámetro de este tipo de registro, el compilador genera una advertencia.

### <a name="exestr"></a>exestr

Lugares *commentstring* en el archivo objeto. En el momento de la vinculación, esta cadena se coloca en el archivo ejecutable. La cadena no se carga en memoria cuando se carga el archivo ejecutable; sin embargo, se puede encontrar con un programa que encuentre las cadenas imprimibles en los archivos. Un uso para este tipo de registro de comentario es incrustar un número de versión o información similar en un archivo ejecutable.

`exestr` está desusado y se quitará en una futura versión; el vinculador no procesa el registro de comentario.

### <a name="lib"></a>lib

Inserta un registro de búsqueda de biblioteca en el archivo objeto. Este tipo de comentario debe ir acompañada de un *commentstring* parámetro que contiene el nombre (y posiblemente la ruta de acceso) de la biblioteca que desea que el vinculador busque. El nombre de la biblioteca sigue los registros de búsqueda de biblioteca predeterminado en el archivo objeto; el vinculador busca esta biblioteca como si hubiera designado en la línea de comandos siempre que la biblioteca no se especifica con [/NODEFAULTLIB](../build/reference/nodefaultlib-ignore-libraries.md). Puede colocar varios registros de búsqueda de biblioteca en el mismo archivo de código fuente; cada registro aparece en el archivo objeto en el mismo orden en el que se encuentra en el archivo de código fuente.

Si el orden de la biblioteca predeterminada y una biblioteca agregada es importante, la compilación con el [/Zl](../build/reference/zl-omit-default-library-name.md) conmutador impedirá que el nombre de biblioteca predeterminado que se va a colocar en el módulo de objeto. Entonces, se puede usar una segunda directiva pragma de comentario para insertar el nombre de biblioteca predeterminada después de la biblioteca agregada. Las bibliotecas incluidas con estas directivas pragma aparecerán en el módulo de objeto en el mismo orden en que se encuentran en el código fuente.

### <a name="linker"></a>vinculador

Coloca un [opción del vinculador](../build/reference/linker-options.md) en el archivo objeto. Puede utilizar este tipo de comentario para especificar una opción del vinculador en lugar de pasarla a la línea de comandos o de especificarla en el entorno de desarrollo. Por ejemplo, puede especificar la opción /include para forzar la inclusión de un símbolo:

```
#pragma comment(linker, "/include:__mySymbol")
```

Solo lo siguiente (*tipo de comentario*) opciones del vinculador están disponibles para pasarse al identificador del vinculador:

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>usuario

Coloca un comentario general en el archivo objeto. El *commentstring* parámetro contiene el texto del comentario. El vinculador no tiene en cuenta este registro de comentario.

La siguiente directiva pragma hace que el vinculador busque la biblioteca EMAPI.LIB durante la vinculación. El vinculador busca primero en el directorio de trabajo actual y en la ruta de acceso especificada en la variable de entorno LIB.

```
#pragma comment( lib, "emapi" )
```

La directiva pragma siguiente hace que el compilador coloque el nombre y el número de versión del compilador en el archivo objeto:

```
#pragma comment( compiler )
```

> [!NOTE]
> Para los comentarios que toman un *commentstring* parámetro, puede utilizar una macro en cualquier lugar donde utilizaría un literal de cadena, siempre que la macro se expande a un literal de cadena. También puede concatenar cualquier combinación de literales de cadena y macros que se expandan a literales de cadena. Por ejemplo, la siguiente instrucción es aceptable:

```
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)