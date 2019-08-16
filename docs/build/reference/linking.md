---
title: Referencia MSVC del vinculador
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 3a9eebef0a264b0131311b5ca96011a4d56264a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176634"
---
# <a name="linking"></a>Vinculación

En un proyecto de C++, el *vinculación* paso se realiza después de que el compilador ha compilado el código fuente en archivos objeto (*.obj). El vinculador (link.exe) combina los archivos de objeto en un único archivo ejecutable. 

Opciones del vinculador se pueden establecer dentro o fuera de Visual Studio. En Visual Studio, para acceder a las opciones del vinculador, con el botón secundario en un nodo de proyecto en **el Explorador de soluciones** y eligiendo **propiedades** para mostrar las páginas de propiedades. Elija **vinculador** en el panel izquierdo para expandir el nodo y ver todas las opciones. 


## <a name="linker-command-line-syntax"></a>Sintaxis de línea de comandos del vinculador

Al ejecutar vínculo fuera de Visual Studio, puede especificar la entrada en una o más maneras:

- En la línea de comandos

- Utilizar archivos de comandos

- En las variables de entorno

Opciones de los procesos primer vínculo especificado en la variable de entorno LINK, seguido de las opciones en el orden en que se especifican en la línea de comandos y en archivos de comandos. Si se repite una opción con distintos argumentos, la última de ellas procesa tiene prioridad.

Las opciones se aplican a toda la compilación; No hay opciones pueden aplicarse a archivos de entrada concretos.

Para ejecutar el vínculo. EXE, use la siguiente sintaxis de comando:

```
LINK arguments
```

El `arguments` incluyen opciones y los nombres de archivo y puede especificarse en cualquier orden. Las opciones son procesa primero y, a continuación, los archivos. Utilice uno o más espacios o tabulaciones para separar los argumentos.

> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

## <a name="command-line"></a>Línea de comandos

En la línea de comandos, una opción consta de un especificador de opción, un guión (-) o una barra diagonal (/), seguido del nombre de la opción. Los nombres de opción no pueden abreviarse. Algunas opciones toman un argumento, especificado después de dos puntos (:). No se permiten espacios ni tabulaciones dentro de una especificación de opción, excepto dentro de una cadena entre comillas en la opción/Comment. Especifique los argumentos numéricos en notación de lenguaje de C o decimal. Los nombres de opción y sus argumentos de la palabra clave o nombre de archivo no distinguen mayúsculas de minúsculas, pero los identificadores como argumentos distinguen mayúsculas de minúsculas.

Para pasar un archivo al vinculador, especifique el nombre de archivo en la línea de comandos después del comando de vínculo. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo, y puede usar caracteres comodín en el nombre de archivo. Si se omiten el punto (.) y la extensión de nombre de archivo, vínculo supone .obj con el fin de encontrar el archivo. VÍNCULO no usa extensiones de nombre de archivo o la falta de ellos para realizar suposiciones sobre el contenido de los archivos; Determina el tipo de archivo mediante el examen de él y lo procesa en consecuencia.

Link.exe devuelve cero si es correcto (sin errores).  En caso contrario, devuelve el número de error que detuvo el vínculo.  Por ejemplo, si el vinculador genera LNK1104, el vinculador devuelve 1104.  En consecuencia, el número más bajo de error devuelto en un error por el enlazador es 1000.  Un valor devuelto de 128 representa un problema de configuración con el sistema operativo o un archivo .config; no cargó el cargador de link.exe o c2.dll.

## <a name="link-command-files"></a>Archivos de comandos de LINK

Puede pasar argumentos de línea de comandos para el vínculo en forma de un archivo de comandos. Para especificar un archivo de comandos del vinculador, use la sintaxis siguiente:

> **VÍNCULO \@**  <em>/commandfile</em>

El */commandfile* es el nombre de un archivo de texto. No se permite ningún espacio o tabulación entre la arroba (**\@**) y el nombre de archivo. No hay ninguna extensión predeterminada; debe especificar el nombre de archivo completo, incluida la extensión. No se puede usar caracteres comodín. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo. VÍNCULO no utiliza una variable de entorno para buscar el archivo.

En el archivo de comandos, se pueden separar los argumentos con espacios o tabulaciones (como en la línea de comandos) y caracteres de nueva línea.

Puede especificar toda o parte de la línea de comandos en un archivo de comandos. Puede usar más de un archivo de comandos en un comando de LINK. VÍNCULO acepta la entrada de archivo de comandos como si se especificaron en esa ubicación en la línea de comandos. Archivos de comandos no se pueden anidar. VÍNCULO refleje el contenido de archivos de comandos, a menos que el [/NOLOGO](nologo-suppress-startup-banner-linker.md) se especifica la opción.

## <a name="example"></a>Ejemplo

El siguiente comando para generar un archivo DLL pasa los nombres de los archivos objeto y bibliotecas de archivos de comandos independientes y usa un tercer archivo de comandos para la especificación de la opción/EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Variables de entorno de LINK

La herramienta LINK usa las variables de entorno siguientes:

- VÍNCULO y \_vínculo\_, si ha definido. La herramienta LINK antepone las opciones y argumentos definidos en la variable de entorno LINK y anexa las opciones y argumentos definan en el \_vínculo\_ variable de entorno para los argumentos de línea de comandos antes del procesamiento.

- LIB, si se define. La herramienta LINK usa la ruta de acceso LIB para buscar un objeto, biblioteca u otro archivo especificado en la línea de comandos o mediante el [/base](base-base-address.md) opción. También usa esta ruta para buscar un archivo .pdb denominado en un objeto. La variable LIB puede contener una o varias especificaciones de ruta de acceso, separadas por punto y coma. Una ruta de acceso debe apuntar al subdirectorio \lib de la instalación de Visual C++.

- PATH, si la herramienta debe ejecutar CVTRES y no encuentra el archivo en el mismo directorio de la propia LINK. (LINK requiere CVTRES para vincular un archivo. res). PATH debe apuntar al subdirectorio \bin de la instalación de Visual C++.

- TMP, para especificar un directorio al vincular archivos .res u OMF.

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/c ++](c-cpp-building-reference.md)
[las opciones del vinculador MSVC](linker-options.md)
[archivos de definición de módulo (.def)](module-definition-dot-def-files.md)
[compatibilidad con vinculador Archivos DLL de carga retrasada](linker-support-for-delay-loaded-dlls.md)
