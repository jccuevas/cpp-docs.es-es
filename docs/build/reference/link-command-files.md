---
title: Archivos de comandos LINK | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6614af87f072c54353ead39c2c5ca789da18dbb8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="link-command-files"></a>Archivos de comandos de LINK
Puede pasar argumentos de línea de comandos al vínculo de la forma de un archivo de comandos. Para especificar un archivo de comandos al vinculador, use la sintaxis siguiente:  
  
```  
LINK @commandfile  
```  
  
 El `commandfile` es el nombre de un archivo de texto. No se permite ningún espacio o tabulación entre el signo de arroba (@) y el nombre de archivo. No hay ninguna extensión predeterminada; debe especificar el nombre de archivo completo, incluida la extensión. No se puede usar caracteres comodín. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo. VÍNCULO no usa una variable de entorno para buscar el archivo.  
  
 En el archivo de comandos, los argumentos pueden ser separados por espacios o tabulaciones, (como en la línea de comandos) y caracteres de nueva línea.  
  
 Puede especificar todos o parte de la línea de comandos en un archivo de comandos. Puede usar más de un archivo de comandos en un comando de LINK. VÍNCULO acepta datos proporcionados por el archivo de comandos como si se especifica en esa ubicación en la línea de comandos. Archivos de comandos no se pueden anidar. VÍNCULO repite el contenido de archivos de comandos, a menos que la [/nologo](../../build/reference/nologo-suppress-startup-banner-linker.md) se especifica la opción.  
  
## <a name="example"></a>Ejemplo  
 El siguiente comando para generar un archivo DLL pasa los nombres de las bibliotecas y archivos de objeto en archivos de comandos diferentes y usa un tercer archivo de comandos para la especificación de la opción/EXPORTS:  
  
```  
link /dll @objlist.txt @liblist.txt @exports.txt  
```  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)