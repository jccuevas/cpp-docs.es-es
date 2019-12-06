---
title: '&lt;filesystem&gt;'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
ms.openlocfilehash: 0f2c90bd7c1d88a94d1dab05b98442111faa71a2
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898815"
---
# <a name="ltfilesystemgt"></a>&lt;filesystem&gt;

Incluya el encabezado &lt;filesystem> para tener acceso a las clases y funciones con las que se manipula y recupera información sobre las rutas de acceso, los archivos y los directorios.

## <a name="syntax"></a>Sintaxis

```cpp
#include <experimental/filesystem> // C++-standard header file name
#include <filesystem> // Microsoft-specific implementation header file name
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> A partir del lanzamiento de Visual Studio 2017, el encabezado \<filesystem > todavía no era un C++ estándar. C++en Visual Studio 2017 (MSVC v141) implementa el último borrador estándar, que se encuentra en [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf).

Este encabezado admite sistemas de archivos para una de las dos clases generales de sistemas operativos host: Microsoft Windows y POSIX.

Mientras que la mayoría de las funciones son comunes a ambos sistemas operativos, en este documento se identifican las diferencias. Por ejemplo:

- Windows admite varios nombres de raíz, como c: o \\\network_name. Un sistema de archivos consta de un bosque de árboles, cada uno con su propio directorio raíz (por ejemplo, c:\ o \\\network_name\\), y cada uno con su propio directorio actual, para completar una ruta de acceso relativa (una que no es una ruta de acceso absoluta).

- POSIX admite un único árbol, sin nombre raíz, el directorio raíz único/y un único directorio actual.

Otra diferencia importante es la representación nativa de rutas de acceso:

- Windows usa una secuencia terminada en null de wchar_t, codificada como UTF-16 (uno o dos elementos para cada carácter).

- POSIX usa una secuencia terminada en NULL de Char, codificada como UTF-8 (uno o varios elementos para cada carácter).

- Un objeto de ruta de acceso de clase almacena la ruta de acceso en forma nativa, pero admite la conversión sencilla entre esta forma almacenada y varias formas externas:

- Una secuencia terminada en null de char, codificada según la preferencia del sistema operativo.

- Una secuencia terminada en null de char, codificada como UTF-8.

- Una secuencia terminada en null de wchar_t, codificada según la preferencia del sistema operativo.

- Una secuencia terminada en null de char16_t, codificada como UTF-16.

- Una secuencia terminada en null de char32_t, codificada como UTF-32.

Las interconversiones entre estas representaciones se realizan, según sea necesario, mediante el uso de una o varias facetas `codecvt`. Si no se designa un objeto de configuración regional específica, estas facetas se obtienen de la configuración regional global.

Otra diferencia es el detalle con el que cada sistema operativo permite especificar permisos de acceso a archivos o directorios:

1. Windows registra si un archivo es de solo lectura o editable, un atributo que no tiene sentido en el caso de los directorios.

1. POSIX registra si un archivo se puede leer, escribir o ejecutar (examinar si es un directorio), el propietario, el grupo del propietario o cualquier persona, además de algunos otros permisos.

Un aspecto común a ambos sistemas es la estructura impuesta en una ruta de acceso una vez superado el nombre de raíz. Para la ruta de acceso c:/abc/xyz/def.ext:

- El nombre de raíz es c:.

- El directorio raíz es /.

- La ruta de acceso raíz es c:/.

- La ruta de acceso relativa es abc/xyz/def.ext.

- La ruta de acceso principal es c:/abc/xyz.

- El nombre de archivo es def.ext.

- La raíz es def.

- La extensión es. ext.

Una diferencia menor es el **separador preferido**, entre la secuencia de directorios de una ruta de acceso. Ambos sistemas operativos le permiten escribir una barra diagonal /, pero, en algunos contextos, Windows prefiere una barra diagonal inversa \\.

Por último, una característica importante de los objetos de ruta de acceso es que pueden usarse cada vez que se necesite un argumento filename en las clases definidas en el encabezado \<fstream>.

Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

## <a name="members"></a>Members

### <a name="classes"></a>Clases

|||
|-|-|
|[directory_entry (Clase)](../standard-library/directory-entry-class.md)|Describe un objeto devuelto por un `directory_iterator` o `recursive_directory_iterator` y que contiene una ruta de acceso.|
|[directory_iterator (Clase)](../standard-library/directory-iterator-class.md)|Describe un iterador de entrada que establece una secuencia por los nombres de archivo en un directorio de sistema de archivos.|
|[filesystem_error (Clase)](../standard-library/filesystem-error-class.md)|Clase base para excepciones que se producen para notificar un desbordamiento de sistema de bajo nivel.|
|[path (Clase)](../standard-library/path-class.md)|Define una clase que almacena un objeto de tipo de plantilla `String` adecuado para su uso como nombre de archivo.|
|[recursive_directory_iterator (Clase)](../standard-library/recursive-directory-iterator-class.md)|Describe un iterador de entrada que establece una secuencia por los nombres de archivo en un directorio de sistema de archivos. El iterador también puede descender a subdirectorios.|
|[file_status (Clase)](../standard-library/file-status-class.md)|Ajusta un `file_type`.|

### <a name="structs"></a>Structs

|||
|-|-|
|[space_info (Estructura)](../standard-library/space-info-structure.md)|Contiene información sobre un volumen.|

## <a name="functions"></a>Funciones

[\<filesystem> (Funciones)](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operadores

[\<filesystem> (Operadores)](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Enumeraciones

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Enumeración que se usa con [copy_file](../standard-library/filesystem-functions.md#copy_file) y determina el comportamiento si ya existe un archivo de destino.|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Enumeración que se usa con [copy_file](../standard-library/filesystem-functions.md#copy_file) y determina el comportamiento si ya existe un archivo de destino.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Enumeración que especifica las opciones de los iteradores de directorio.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Enumeración de tipos de archivo.|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)||
|[perms](../standard-library/filesystem-enumerations.md#perms)|Un tipo de máscara de bits que se usa para transmitir los permisos y las opciones de permisos.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
