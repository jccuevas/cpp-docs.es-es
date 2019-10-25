---
title: comment (pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: 3175ad5318bcc6fd9aa6233258ccec9033c89be8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219102"
---
# <a name="comment-pragma"></a>comment (pragma)

Inserta un registro de comentario en un archivo objeto o ejecutable.

## <a name="syntax"></a>Sintaxis

> **#pragma comment (** *Comentario-Type* [ **,** "*comment-String*"] **)**

## <a name="remarks"></a>Comentarios

El *tipo de comentario* es uno de los identificadores predefinidos, que se describen a continuación, que especifica el tipo de registro de comentario. La *cadena de comentario* opcional es un literal de cadena que proporciona información adicional para algunos tipos de comentario. Dado que *comment-String* es un literal de cadena, obedece todas las reglas para los literales de cadena con respecto a los caracteres de escape,`"`las comillas incrustadas () y la concatenación.

### <a name="compiler"></a>compilador

Coloca el nombre y número de versión del compilador en el archivo objeto. El vinculador no tiene en cuenta este registro de comentario. Si proporciona un parámetro *de cadena de comentario* para este tipo de registro, el compilador genera una advertencia.

### <a name="lib"></a>lib

Inserta un registro de búsqueda de biblioteca en el archivo objeto. Este tipo de comentario debe ir acompañado de un parámetro de *cadena de comentario* que contiene el nombre (y, posiblemente, la ruta de acceso) de la biblioteca que desea que busque el enlazador. El nombre de la biblioteca sigue los registros predeterminados de búsqueda de biblioteca en el archivo objeto; el enlazador busca esta biblioteca como si hubiera sido denominada en la línea de comandos siempre que la biblioteca no se especifique con [/NODEFAULTLIB](../build/reference/nodefaultlib-ignore-libraries.md). Puede colocar varios registros de búsqueda de biblioteca en el mismo archivo de código fuente; cada registro aparece en el archivo objeto en el mismo orden en el que se encuentra en el archivo de código fuente.

Si el orden de la biblioteca predeterminada y una biblioteca agregada es importante, la compilación con el modificador [/ZL](../build/reference/zl-omit-default-library-name.md) impedirá que el nombre de biblioteca predeterminado se coloque en el módulo de objeto. Entonces, se puede usar una segunda directiva pragma de comentario para insertar el nombre de biblioteca predeterminada después de la biblioteca agregada. Las bibliotecas incluidas con estas directivas pragma aparecerán en el módulo de objeto en el mismo orden en que se encuentran en el código fuente.

### <a name="linker"></a>vinculador

Coloca una [opción](../build/reference/linker-options.md) del vinculador en el archivo objeto. Puede utilizar este tipo de comentario para especificar una opción del vinculador en lugar de pasarla a la línea de comandos o de especificarla en el entorno de desarrollo. Por ejemplo, puede especificar la opción /include para forzar la inclusión de un símbolo:

```C
#pragma comment(linker, "/include:__mySymbol")
```

Solo las siguientes opciones del enlazador (*tipo de comentario*) están disponibles para pasarse al identificador del enlazador:

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>usuario

Coloca un comentario general en el archivo objeto. El parámetro de *cadena de comentario* contiene el texto del comentario. El vinculador no tiene en cuenta este registro de comentario.

## <a name="examples"></a>Ejemplos

La siguiente directiva pragma hace que el vinculador busque la biblioteca EMAPI.LIB durante la vinculación. El vinculador busca primero en el directorio de trabajo actual y en la ruta de acceso especificada en la variable de entorno LIB.

```C
#pragma comment( lib, "emapi" )
```

La directiva pragma siguiente hace que el compilador coloque el nombre y el número de versión del compilador en el archivo objeto:

```C
#pragma comment( compiler )
```

En el caso de los comentarios que toman un parámetro *de cadena de comentario* , puede usar una macro en cualquier lugar donde se usaría un literal de cadena, siempre que la macro se expanda a un literal de cadena. También puede concatenar cualquier combinación de literales de cadena y macros que se expandan a literales de cadena. Por ejemplo, la siguiente instrucción es aceptable:

```C
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
