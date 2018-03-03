---
title: "Sintaxis de línea de comandos del vinculador | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ce42aa031b91d5a4ec21ed14ac7cb47643e1325
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-command-line-syntax"></a>Sintaxis de la línea de comandos del vinculador
Para ejecutar el vínculo. EXE, use la siguiente sintaxis de comando:  
  
```  
LINK arguments  
```  
  
 El `arguments` incluyen opciones y nombres de archivo y puede especificarse en cualquier orden. Opciones son procesa primero, a continuación, en archivos. Use uno o más espacios o tabulaciones para separar los argumentos.  
  
> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.  
  
 En la línea de comandos, una opción consta de un especificador de opción, un guión (-) o una barra diagonal (/), seguido del nombre de la opción. Los nombres de opción no pueden abreviarse. Algunas opciones toman un argumento, ir precedido por dos puntos (:). No se permiten espacios ni tabulaciones dentro de una especificación de opción, excepto dentro de una cadena entre comillas en la opción/Comment. Especifique los argumentos numéricos en formato decimal o notación del lenguaje c. Los nombres de opción y sus argumentos de palabra clave o nombre de archivo no distinguen mayúsculas de minúsculas, pero los identificadores como argumentos distinguen mayúsculas de minúsculas.  
  
 Para pasar un archivo al vinculador, especifique el nombre de archivo en la línea de comandos después del comando de vínculo. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo, y puede usar caracteres comodín en el nombre de archivo. Si se omiten el punto (.) y la extensión de nombre de archivo, LINK supondrá .obj con el fin de buscar el archivo. LINK no usa las extensiones de nombre de archivo o la falta de ellos para realizar suposiciones sobre el contenido de archivos; Determina el tipo de archivo mediante el examen de él y lo procesa en consecuencia.  
  
 Link.exe devuelve cero para correcto (sin errores).  En caso contrario, el vinculador devuelve el número de error que detuvo el vínculo.  Por ejemplo, si el vinculador genera LNK1104, el vinculador devuelve 1104.  En consecuencia, el menor número de error devolviendo el vinculador produce un error es 1000.  Un valor devuelto de 128 representa un problema de configuración con el sistema operativo o un archivo .config; el cargador no cargó link.exe o c2.dll.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)