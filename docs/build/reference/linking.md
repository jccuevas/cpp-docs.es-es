---
title: Referencia del enlazador MSVC
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 2503e212e7325fc97f9057861cb85d5cf0571094
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336501"
---
# <a name="linking"></a>Vinculación

En un proyecto de C++, el paso de *vinculación* se realiza después de que el compilador haya compilado el código fuente en archivos de objeto (*.obj). El vinculador (link.exe) combina los archivos de objeto en un único archivo ejecutable.

Las opciones del vinculador se pueden establecer dentro o fuera de Visual Studio. En Visual Studio, tiene acceso a las opciones del vinculador haciendo clic con el botón secundario en un nodo de proyecto en el **Explorador** de soluciones y seleccionando **Propiedades** para mostrar las páginas de propiedades. Elija **Vinculador** en el panel izquierdo para expandir el nodo y ver todas las opciones.

## <a name="linker-command-line-syntax"></a>Sintaxis de línea de comandos del vinculador

Al ejecutar LINK fuera de Visual Studio, puede especificar la entrada de una o varias maneras:

- En la línea de comandos

- Uso de archivos de comandos

- En variables de entorno

LINK primero procesa las opciones especificadas en la variable de entorno LINK, seguidas de las opciones en el orden en que se especifican en la línea de comandos y en los archivos de comandos. Si una opción se repite con argumentos diferentes, el último procesado tiene prioridad.

Las opciones se aplican a toda la compilación; no se pueden aplicar opciones a archivos de entrada específicos.

Para ejecutar LINK. EXE, utilice la siguiente sintaxis de comandos:

```
LINK arguments
```

Las `arguments` opciones de inclusión y los nombres de archivo y se pueden especificar en cualquier orden. Las opciones se procesan primero y, a continuación, los archivos. Utilice uno o más espacios o pestañas para separar argumentos.

> [!NOTE]
> Puede iniciar esta herramienta solo desde el símbolo del sistema de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

## <a name="command-line"></a>Línea de comandos

En la línea de comandos, una opción consta de un especificador de opción, ya sea un guión (-) o una barra diagonal (/), seguido del nombre de la opción. Los nombres de opción no pueden abreviarse. Algunas opciones toman un argumento, especificado después de dos puntos (:). No se permiten espacios ni tabulaciones dentro de una especificación de opción, excepto dentro de una cadena entre comillas en la opción /COMMENT. Especifique argumentos numéricos en notación decimal o en lenguaje C. Los nombres de opción y sus argumentos de palabra clave o nombre de archivo no distinguen entre mayúsculas y minúsculas, pero los identificadores como argumentos distinguen entre mayúsculas y minúsculas.

Para pasar un archivo al vinculador, especifique el nombre de archivo en la línea de comandos después del comando LINK. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo y puede utilizar comodines en el nombre de archivo. Si omite el punto (.) y la extensión de nombre de archivo, LINK asume .obj con el fin de encontrar el archivo. LINK no utiliza extensiones de nombre de archivo o la falta de ellas para hacer suposiciones sobre el contenido de los archivos; determina el tipo de archivo examinándolo y lo procesa en consecuencia.

link.exe devuelve cero para el éxito (sin errores).  De lo contrario, el vinculador devuelve el número de error que detuvo el vínculo.  Por ejemplo, si el vinculador genera LNK1104, el vinculador devuelve 1104.  En consecuencia, el número de error más bajo devuelto en un error por el vinculador es 1000.  Un valor devuelto de 128 representa un problema de configuración con el sistema operativo o un archivo .config; el cargador no cargaba link.exe ni c2.dll.

## <a name="link-command-files"></a>Archivos de comandos de LINK

Puede pasar argumentos de línea de comandos a LINK en forma de archivo de comandos. Para especificar un archivo de comandos en el vinculador, utilice la sintaxis siguiente:

> **Archivo \@ ** <em>de comandos</em> LINK

El *archivo de comandos* es el nombre de un archivo de texto. No se permite espacio ni tabulación entre el signo de ar (**\@**) y el nombre de archivo. No hay ninguna extensión predeterminada; debe especificar el nombre de archivo completo, incluida cualquier extensión. No se pueden usar comodines. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo. LINK no utiliza una variable de entorno para buscar el archivo.

En el archivo de comandos, los argumentos se pueden separar por espacios o tabulaciones (como en la línea de comandos) y por caracteres de nueva línea.

Puede especificar toda o parte de la línea de comandos en un archivo de comandos. Puede utilizar más de un archivo de comandos en un comando LINK. LINK acepta la entrada del archivo de comandos como si se especificara en esa ubicación en la línea de comandos. Los archivos de comandos no se pueden anidar. LINK se hace eco del contenido de los archivos de comandos, a menos que se especifique la opción [/NOLOGO.](nologo-suppress-startup-banner-linker.md)

## <a name="example"></a>Ejemplo

El siguiente comando para crear un archivo DLL pasa los nombres de archivos de objeto y bibliotecas en archivos de comandos independientes y utiliza un tercer archivo de comandos para la especificación de la opción /EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Variables de entorno de LINK

La herramienta LINK usa las variables de entorno siguientes:

- LINK \_y\_LINK , si están definidos. La herramienta LINK antepone las opciones y argumentos definidos en la variable \_de\_ entorno LINK y anexa las opciones y argumentos definidos en la variable de entorno LINK a los argumentos de línea de comandos antes del procesamiento.

- LIB, si se define. Las herramientas LINK utilizan la ruta DE ACCESO LIB al buscar un objeto, biblioteca u otro archivo especificado en la línea de comandos o mediante la opción [/BASE.](base-base-address.md) También usa esta ruta para buscar un archivo .pdb denominado en un objeto. La variable LIB puede contener una o varias especificaciones de ruta de acceso, separadas por punto y coma. Una ruta de acceso debe apuntar al subdirectorio \lib de la instalación de Visual C++.

- PATH, si la herramienta debe ejecutar CVTRES y no encuentra el archivo en el mismo directorio de la propia LINK. (LINK requiere CVTRES para vincular un archivo .res.) PATH debe apuntar al subdirectorio .bin de la instalación de Visual C++.

- TMP, para especificar un directorio al vincular archivos .res u OMF.

## <a name="see-also"></a>Consulte también

[C/C++ Building Reference](c-cpp-building-reference.md)
[MSVC Linker Options](linker-options.md)
[Module-Definition (.def) Files](module-definition-dot-def-files.md)
[Linker Support for Delay-Loaded DLLs](linker-support-for-delay-loaded-dlls.md)
