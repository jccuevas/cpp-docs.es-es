---
title: '&lt;filesystem&gt;'
description: Describe las clases, las funciones y los tipos del encabezado filesystem de la biblioteca C++ estándar.
ms.date: 01/22/2020
f1_keywords:
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- filesystem
- experimental
- char
- wchar_t
- char16_t
- char32_t
ms.openlocfilehash: f9e384953a4e675ad6235a274c447031976a1585
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441708"
---
# &lt;filesystem&gt;

Incluya el encabezado &lt;filesystem> para el acceso a las clases y funciones que manipulan y recuperan información sobre rutas de acceso, archivos y directorios.

## <a name="syntax"></a>Sintaxis

```cpp
#include <filesystem> // C++17 standard header file name
#include <experimental/filesystem> // Header file for pre-standard implementation
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> En el lanzamiento de Visual Studio 2017, el encabezado \<filesystem> no era todavía un C++ estándar. C++en Visual Studio 2017 RTW implementa el último borrador estándar, que se encuentra en [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf). Visual Studio 2017 versión 15,7 y versiones posteriores admiten el nuevo \<de C++ 17 filesystem> estándar.
> Se trata de una implementación completamente nueva, incompatible con la versión de `std::experimental` anterior. Lo hizo necesario la compatibilidad con symlink, las correcciones de errores y los cambios en el comportamiento estándar requerido. Actualmente, incluido \<filesystem> proporciona el nuevo `std::filesystem` y el `std::experimental::filesystem`anterior. La inclusión de \<experimental/filesystem> solo proporciona la implementación de experimental anterior. La implementación de experimental se quitará en la próxima versión de lanzamiento de las bibliotecas.

Este encabezado admite sistemas de archivos para una de las dos clases generales de sistemas operativos host: Microsoft Windows y POSIX.

Mientras que la mayoría de las funciones son comunes a ambos sistemas operativos, en este documento se identifican las diferencias. Por ejemplo:

- Windows admite varios nombres de raíz, como `c:` o `\\network_name`. Un sistema de archivos consta de un bosque de árboles, cada uno con su propio directorio raíz, como `c:\` o `\\network_name\`, y cada uno con su propio directorio actual, para completar un nombreruta relativo (uno que no es un nombreruta absoluto).

- POSIX admite un único árbol, sin nombre de raíz, el directorio raíz único `/`y un único directorio actual.

Otra diferencia importante es la representación nativa de rutas de acceso:

- Windows usa una secuencia terminada en NULL de **wchar_t** codificada como UTF-16 (uno o varios elementos para cada carácter).

- POSIX usa una secuencia terminada en NULL de **char** codificada como UTF-8 (uno o varios elementos para cada carácter).

- Un objeto de clase `path` almacena el nombreruta en forma nativa, pero admite la conversión sencilla entre esta forma almacenada y varias formas externas:

  - Una secuencia terminada en NULL de **char** , codificada como favoreceda por el sistema operativo.

  - Una secuencia terminada en NULL de **char** codificada como UTF-8.

  - Una secuencia terminada en NULL de **wchar_t** , codificada como favoreceda por el sistema operativo.

  - Una secuencia terminada en NULL de **char16_t** codificada como UTF-16.

  - Una secuencia terminada en NULL de **char32_t** codificada como UTF-32.

  Las interconversiones entre estas representaciones se realizan, según sea necesario, mediante el uso de una o varias facetas `codecvt`. Si no se especifica ningún objeto de configuración regional específico, estas caras se obtienen de la configuración regional global.

Otra diferencia es el detalle con el que cada sistema operativo permite especificar permisos de acceso a archivos o directorios:

- Windows registra si un archivo es de solo lectura o grabable, un atributo que no tiene ningún significado para los directorios.

- POSIX registra si un archivo se puede leer, escribir o ejecutar (examinar, si se trata de un directorio). Además, si cada operación se permite para el propietario, el grupo del propietario o para todos los demás permisos.

Un aspecto común a ambos sistemas es la estructura impuesta en una ruta de acceso una vez superado el nombre de raíz. En el `c:/abc/xyz/def.ext`pathname:

- El nombre de raíz es `c:`.

- El directorio raíz es `/`.

- La ruta de acceso raíz es `c:/`.

- La ruta de acceso relativa es `abc/xyz/def.ext`.

- La ruta de acceso primaria es `c:/abc/xyz`.

- El nombre de archivo es `def.ext`.

- El tallo es `def`.

- La extensión es `.ext`.

Una diferencia menor es el separador preferido entre la secuencia de directorios de un nombreruta. Ambos sistemas operativos permiten escribir una barra diagonal `/`, pero en algunos contextos Windows prefiere una barra diagonal inversa `\`. La implementación almacena su separador preferido en el `preferred_separator` del miembro de datos en `path`.

Por último, los objetos `path` tienen una característica importante: puede usarlos siempre que se necesite un argumento FILENAME en las clases definidas en el encabezado [\<fstream >](fstream.md).

Para obtener más información y ejemplos de código, vea [navegación delC++sistema de archivos ()](../standard-library/file-system-navigation.md).

## <a name="members"></a>Members

### <a name="classes"></a>Clases

|||
|-|-|
|[directory_entry (clase)](../standard-library/directory-entry-class.md)|Describe un objeto devuelto por un `directory_iterator` o un `recursive_directory_iterator` y contiene un `path`.|
|[directory_iterator (clase)](../standard-library/directory-iterator-class.md)|Describe un iterador de entrada que establece una secuencia por los nombres de archivo en un directorio de sistema de archivos.|
|[filesystem_error (clase)](../standard-library/filesystem-error-class.md)|Clase base para excepciones que se producen para notificar un desbordamiento de sistema de bajo nivel.|
|[Path (clase)](../standard-library/path-class.md)|Define una clase que almacena un objeto de tipo de plantilla `String` adecuado para su uso como nombre de archivo.|
|[recursive_directory_iterator (clase)](../standard-library/recursive-directory-iterator-class.md)|Describe un iterador de entrada que establece una secuencia por los nombres de archivo en un directorio de sistema de archivos. El iterador también puede descender a subdirectorios.|
|[file_status (clase)](../standard-library/file-status-class.md)|Ajusta un `file_type`.|

### <a name="structs"></a>Estructuras

|||
|-|-|
|[estructura de space_info](../standard-library/space-info-structure.md)|Contiene información sobre un volumen.|

## <a name="functions"></a>Functions

[\<filesystemfunciones >](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operadores

[operadores de > de filesystemde \<](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Enumeraciones

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Enumeración que se usa con [copy_file](../standard-library/filesystem-functions.md#copy_file) y determina el comportamiento si ya existe un archivo de destino.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Enumeración que especifica las opciones de los iteradores de directorio.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Enumeración de tipos de archivo.|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)| Enumera las opciones de la función `permissions`. |
|[perms](../standard-library/filesystem-enumerations.md#perms)|Un tipo de máscara de bits que se usa para transmitir los permisos y las opciones de permisos.|

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
