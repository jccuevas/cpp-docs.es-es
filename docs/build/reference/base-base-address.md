---
title: -BASE (dirección Base) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4090a3e8d2f9f3bdcb68875d94a1b84e7bff0f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="base-base-address"></a>/BASE (Dirección base)
```  
/BASE:{address[,size] | @filename,key}  
```  
  
 La opción BASE establece una dirección base para el programa, se reemplaza la ubicación predeterminada de .exe o archivo DLL. La dirección base predeterminada para un archivo .exe es 0 x 400000 para imágenes de 32 bits o 0x140000000 para las imágenes de 64 bits. Para un archivo DLL, la dirección base predeterminada es 0 x 10000000 para imágenes de 32 bits o 0x180000000 para las imágenes de 64 bits. En sistemas operativos que no admiten la selección aleatoria de diseño de espacio de direcciones (ASLR) o cuando se establece la opción /DYNAMICBASE:NO, en primer lugar el sistema operativo intenta cargar un programa en su especificado o la dirección base predeterminada. Si suficiente espacio no está disponible, el sistema vuelve a colocar el programa. Para evitarlo, use la [/FIXED](../../build/reference/fixed-fixed-base-address.md) opción.  
  
 El vinculador emite un error si *dirección* no es un múltiplo de 64 K. También puede especificar el tamaño del programa; el vinculador emite una advertencia si el programa no cabe en el tamaño especificado.  
  
 En la línea de comandos, otro método para especificar la dirección base es mediante un archivo de respuesta de la dirección base. Un archivo de respuesta de la dirección base es un archivo de texto que contiene las direcciones base y los tamaños opcionales de todas las DLL que se va a usar el programa y una clave de texto única para cada dirección base. Para especificar una dirección base mediante un archivo de respuesta, use una arroba (@) seguido del nombre del archivo de respuesta, *filename*, seguido de una coma, la `key` valor para la dirección base para utilizarla en el archivo. El vinculador busca *filename* en la ruta especificada, o si no se especifica ninguna ruta de acceso, en los directorios especificados en la variable de entorno LIB. Cada línea en *filename* representa una DLL y tiene la siguiente sintaxis:  
  
```  
  
key address [size] ;comment  
```  
  
 El `key` es una cadena de caracteres alfanuméricos y no distingue mayúsculas de minúsculas. Suele ser el nombre de un archivo DLL, pero no es necesario tener. El `key` va seguido de una base de *dirección* en notación de lenguaje C, hexadecimal o decimal y un máximo opcional `size`. Los tres argumentos están separados por espacios o tabulaciones. El vinculador emite una advertencia si especificado `size` es menor que el espacio de direcciones virtuales requerido por el programa. Un `comment` se especifica mediante un punto y coma (;) y puede estar en la misma o una línea independiente. El vinculador omite todo el texto desde el punto y coma al final de la línea. Este ejemplo muestra parte de un archivo:  
  
```  
main   0x00010000    0x08000000    ; for PROJECT.exe  
one    0x28000000    0x00100000    ; for DLLONE.DLL  
two    0x28100000    0x00300000    ; for DLLTWO.DLL  
```  
  
 Si el archivo que contiene estas líneas se denomina DLLS.txt, el comando de ejemplo siguiente aplica esta información:  
  
```  
link dlltwo.obj /dll /base:@dlls.txt,two  
```  
  
## <a name="remarks"></a>Comentarios  
 Por motivos de seguridad, Microsoft recomienda usar la [/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) opción en lugar de especificar las direcciones base para los archivos ejecutables. Esto genera una imagen ejecutable que se pueda reorganizar aleatoriamente en tiempo de carga mediante el uso de la característica de selección aleatoria (ASLR) de diseño del espacio de direcciones de Windows. La opción/DynamicBase está activada de forma predeterminada.  
  
 Otra manera de establecer la dirección base es mediante el uso de la *BASE* argumento en un [nombre](../../build/reference/name-c-cpp.md) o [biblioteca](../../build/reference/library.md) instrucción. El /BASE y [/DLL](../../build/reference/dll-build-a-dll.md) opciones juntas equivalen a la **biblioteca** instrucción.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **vinculador** carpeta.  
  
3.  Elija la **avanzadas** página de propiedades.  
  
4.  Modificar el **dirección Base** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)