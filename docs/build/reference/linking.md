---
title: Referencia del enlazador MSVC
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: d46874b5eaff889834df284ba90e6c6f196d8d66
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079509"
---
# <a name="linking"></a>Vinculación

En un C++ proyecto de, el paso de *vinculación* se realiza después de que el compilador haya compilado el código fuente en archivos objeto (*. obj). El enlazador (link. exe) combina los archivos objeto en un único archivo ejecutable.

Las opciones del enlazador se pueden establecer dentro o fuera de Visual Studio. En Visual Studio, puede acceder a las opciones del enlazador haciendo clic con el botón derecho en un nodo del proyecto en **Explorador de soluciones** y eligiendo **propiedades** para mostrar las páginas de propiedades. Elija **vinculador** en el panel izquierdo para expandir el nodo y ver todas las opciones.

## <a name="linker-command-line-syntax"></a>Sintaxis de línea de comandos del vinculador

Al ejecutar LINK fuera de Visual Studio, puede especificar la entrada de una o varias maneras:

- En la línea de comandos

- Usar archivos de comandos

- En variables de entorno

Las opciones de LINK First processes especificadas en la variable de entorno LINK, seguidas de las opciones en el orden en que se especifican en la línea de comandos y en los archivos de comandos. Si una opción se repite con argumentos diferentes, tiene prioridad la última que se procesa.

Las opciones se aplican a toda la compilación; no se pueden aplicar opciones a archivos de entrada específicos.

Para ejecutar el vínculo. Use la siguiente sintaxis de comando:

```
LINK arguments
```

Los `arguments` incluyen opciones y nombres de archivo, y se pueden especificar en cualquier orden. Las opciones se procesan en primer lugar y luego los archivos. Utilice uno o varios espacios o tabulaciones para separar los argumentos.

> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

## <a name="command-line"></a>Línea de comandos

En la línea de comandos, una opción consta de un especificador de opción, ya sea un guión (-) o una barra diagonal (/), seguido del nombre de la opción. Los nombres de opción no pueden abreviarse. Algunas opciones toman un argumento, que se especifica después de dos puntos (:). No se permiten espacios ni pestañas dentro de una especificación de opción, excepto en una cadena entrecomillada en la opción/COMMENT. Especifique argumentos numéricos en notación decimal o de lenguaje C. Los nombres de opciones y sus argumentos de nombre de archivo o palabra clave no distinguen mayúsculas de minúsculas, pero los identificadores como argumentos distinguen mayúsculas de minúsculas

Para pasar un archivo al vinculador, especifique el nombre de archivo en la línea de comandos después del comando LINK. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo, y puede usar caracteres comodín en el nombre de archivo. Si omite la extensión de punto (.) y nombre de archivo, el vínculo presupone. obj con el fin de buscar el archivo. LINK no utiliza las extensiones de nombre de archivo ni la falta de ellos para hacer suposiciones sobre el contenido de los archivos. determina el tipo de archivo mediante su examen y lo procesa en consecuencia.

Link. exe devuelve cero si es correcto (sin errores).  De lo contrario, el vinculador devuelve el número de error que detuvo el vínculo.  Por ejemplo, si el vinculador genera LNK1104, el enlazador devuelve 1104.  En consecuencia, el número de error más bajo devuelto en un error por parte del enlazador es 1000.  Un valor devuelto de 128 representa un problema de configuración con el sistema operativo o un archivo. config; el cargador no cargó Link. exe o C2. dll.

## <a name="link-command-files"></a>Archivos de comandos de LINK

Puede pasar argumentos de línea de comandos a LINK en forma de archivo de comandos. Para especificar un archivo de comandos para el vinculador, utilice la siguiente sintaxis:

> **Vínculo \@** <em>commandfile</em>

*Commandfile* es el nombre de un archivo de texto. No se permiten espacios ni tabulaciones entre el signo de arroba ( **\@** ) y el nombre de archivo. No hay ninguna extensión predeterminada; debe especificar el nombre de archivo completo, incluida cualquier extensión. No se pueden usar caracteres comodín. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo. LINK no utiliza una variable de entorno para buscar el archivo.

En el archivo de comandos, los argumentos pueden estar separados por espacios o tabulaciones (como en la línea de comandos) y por caracteres de nueva línea.

Puede especificar toda o parte de la línea de comandos en un archivo de comandos. Puede usar más de un archivo de comandos en un comando LINK. LINK acepta la entrada del archivo de comandos como si se hubiera especificado en esa ubicación en la línea de comandos. Los archivos de comandos no se pueden anidar. LINK repite el contenido de los archivos de comandos, a menos que se especifique la opción [/nologo](nologo-suppress-startup-banner-linker.md) .

## <a name="example"></a>Ejemplo

El siguiente comando para compilar un archivo DLL pasa los nombres de las bibliotecas y los archivos de objeto en archivos de comandos independientes y usa un tercer archivo de comandos para la especificación de la opción/EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Variables de entorno de LINK

La herramienta LINK usa las variables de entorno siguientes:

- VÍNCULO y \_\_de vínculo, si se define. La herramienta LINK antepone las opciones y los argumentos definidos en la variable de entorno LINK y anexa las opciones y los argumentos definidos en la variable de entorno \_LINK\_ a los argumentos de la línea de comandos antes del procesamiento.

- LIB, si se define. Las herramientas de vínculo utilizan la ruta de acceso de LIB al buscar un objeto, una biblioteca u otro archivo especificado en la línea de comandos o mediante la opción [/base](base-base-address.md) . También usa esta ruta para buscar un archivo .pdb denominado en un objeto. La variable LIB puede contener una o varias especificaciones de ruta de acceso, separadas por punto y coma. Una ruta de acceso debe apuntar al subdirectorio \lib de la instalación de Visual C++.

- PATH, si la herramienta debe ejecutar CVTRES y no encuentra el archivo en el mismo directorio de la propia LINK. (LINK requiere CVTRES para vincular un archivo. res). La ruta de acceso debe apuntar al subdirectorio \bin C++ de la instalación visual.

- TMP, para especificar un directorio al vincular archivos .res u OMF.

## <a name="see-also"></a>Consulte también

[C/C++ Building Reference](c-cpp-building-reference.md)
[Opciones del enlazador de MSVC](linker-options.md)
[archivos de definición de módulo (. def)](module-definition-dot-def-files.md)
[compatibilidad del vinculador con las dll de carga retrasada](linker-support-for-delay-loaded-dlls.md)
