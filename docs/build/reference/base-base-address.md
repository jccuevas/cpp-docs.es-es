---
title: /BASE (Dirección base)
ms.date: 09/05/2018
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
helpviewer_keywords:
- base addresses [C++]
- programs [C++], preventing relocation
- semicolon [C++], specifier
- -BASE linker option
- key address size
- environment variables [C++], LIB
- programs [C++], base address
- LIB environment variable
- BASE linker option
- DLLs [C++], linking
- /BASE linker option
- '@ symbol for base address'
- executable files [C++], base address
- at sign symbol for base address
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
ms.openlocfilehash: 87fdceea4ac71fe4bf0a53d7ae8e473bc97a01d7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416753"
---
# <a name="base-base-address"></a>/BASE (Dirección base)

Especifica la dirección base para un programa.

## <a name="syntax"></a>Sintaxis

> **/BASE:**{*address*[**,**<em>size</em>] | **\@**<em>filename</em>**,**<em>key</em>}

## <a name="remarks"></a>Comentarios

> [!NOTE]
> Por motivos de seguridad, Microsoft recomienda usar la [/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) opción en lugar de especificar las direcciones base para los archivos ejecutables. Esto genera una imagen ejecutable que puede reubicarse aleatoriamente durante la carga mediante el uso de la característica de selección aleatoria (ASLR) de diseño del espacio de direcciones de Windows. La opción/DynamicBase se está activada de forma predeterminada.

La opción BASE establece una dirección base para el programa, se reemplaza la ubicación predeterminada de .exe o archivo DLL. La dirección base predeterminada para un archivo .exe es 0 x 400000 para imágenes de 32 bits o 0x140000000 para imágenes de 64 bits. Para un archivo DLL, la dirección base predeterminada es 0 x 10000000 para imágenes de 32 bits o 0x180000000 para imágenes de 64 bits. En sistemas operativos que no admiten la selección aleatoria de diseño de espacio de direcciones (ASLR), o cuando la opción: no se ha establecido, en primer lugar el sistema operativo intenta cargar un programa en su especificado o la dirección base predeterminada. Si hay suficiente espacio no existe, el sistema vuelve a colocar el programa. Para evitarlo, utilice el [/FIXED](../../build/reference/fixed-fixed-base-address.md) opción.

El enlazador emite un error si *dirección* no es un múltiplo de 64 K. Opcionalmente, puede especificar el tamaño del programa; el enlazador emite una advertencia si el sistema no cabe en el tamaño especificado.

En la línea de comandos, otra manera de especificar la dirección base es mediante un archivo de respuesta de la dirección base. Un archivo de respuesta de la dirección base es un archivo de texto que contiene las direcciones base y los tamaños opcionales de todos los archivos DLL que utilizará el programa y una clave de texto única para cada dirección base. Para especificar una dirección base utilizando un archivo de respuesta, use una arroba (**\@**) seguido del nombre del archivo de respuesta, *filename*, seguido por una coma, a continuación, el *clave*valor para la dirección base utilizar en el archivo. El vinculador busca *filename* en la ruta especificada, o si no se especifica ninguna ruta de acceso, en los directorios especificados en la variable de entorno LIB. Cada línea en *filename* representa una DLL y tiene la siguiente sintaxis:

> *key* *address* [*size*] **;** *comment*

El *clave* es una cadena de caracteres alfanuméricos y no distingue mayúsculas de minúsculas. Suele ser el nombre de un archivo DLL, pero no es necesario que sea. El *clave* va seguido de una base de *dirección* en notación de lenguaje C, hexadecimal o decimal y un máximo opcional *tamaño*. Los tres argumentos están separados por espacios o tabulaciones. El enlazador emite una advertencia si especificado *tamaño* es menor que el espacio de direcciones virtuales requerido por el programa. Un *comentario* especificado por un punto y coma (**;**) y puede estar en la misma o una línea independiente. El vinculador omite todo el texto desde el punto y coma al final de la línea. En este ejemplo se muestra parte de este tipo de archivo:

```
main   0x00010000    0x08000000    ; for PROJECT.exe
one    0x28000000    0x00100000    ; for DLLONE.DLL
two    0x28100000    0x00300000    ; for DLLTWO.DLL
```

Si el archivo que contiene estas líneas se denomina DLLS.txt, el comando de ejemplo siguiente aplica esta información:

```
link dlltwo.obj /dll /base:@dlls.txt,two
```

Otra forma de establecer la dirección base es mediante la *BASE* argumento en un [nombre](../../build/reference/name-c-cpp.md) o [biblioteca](../../build/reference/library.md) instrucción. La opción /BASE y [/DLL](../../build/reference/dll-build-a-dll.md) juntos son equivalentes a la **biblioteca** instrucción.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **avanzadas** página de propiedades.

1. Modificar el **dirección Base** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
