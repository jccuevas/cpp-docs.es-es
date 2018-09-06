---
title: Archivos de comandos de vínculo | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- syntax, LINK command files
- command files [C++]
- LINK tool [C++]
- text files, passing arguments to LINK
- LINK tool [C++], command-line syntax
- command files [C++], LINK
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8934758d8aa406ea7b7c959b1fc535cde32195b1
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894686"
---
# <a name="link-command-files"></a>Archivos de comandos de LINK

Puede pasar argumentos de línea de comandos para el vínculo en forma de un archivo de comandos. Para especificar un archivo de comandos del vinculador, use la sintaxis siguiente:

> **VÍNCULO \@**  <em>/commandfile</em>

El */commandfile* es el nombre de un archivo de texto. No se permite ningún espacio o tabulación entre la arroba (**\@**) y el nombre de archivo. No hay ninguna extensión predeterminada; debe especificar el nombre de archivo completo, incluida la extensión. No se puede usar caracteres comodín. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo. VÍNCULO no utiliza una variable de entorno para buscar el archivo.

En el archivo de comandos, se pueden separar los argumentos con espacios o tabulaciones (como en la línea de comandos) y caracteres de nueva línea.

Puede especificar toda o parte de la línea de comandos en un archivo de comandos. Puede usar más de un archivo de comandos en un comando de LINK. VÍNCULO acepta la entrada de archivo de comandos como si se especificaron en esa ubicación en la línea de comandos. Archivos de comandos no se pueden anidar. VÍNCULO refleje el contenido de archivos de comandos, a menos que el [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md) se especifica la opción.

## <a name="example"></a>Ejemplo

El siguiente comando para generar un archivo DLL pasa los nombres de los archivos objeto y bibliotecas de archivos de comandos independientes y usa un tercer archivo de comandos para la especificación de la opción/EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
[Opciones del vinculador](../../build/reference/linker-options.md)