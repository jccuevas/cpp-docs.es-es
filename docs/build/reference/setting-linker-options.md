---
title: Establecer las opciones del vinculador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18728994be3f44152a263fb8a6009728e33a42a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374926"
---
# <a name="setting-linker-options"></a>Establecer las opciones del vinculador
Opciones del vinculador pueden establecerse dentro o fuera del entorno de desarrollo. El tema de cada opción del vinculador explica cómo se puede establecer en el entorno de desarrollo. Vea [opciones del vinculador](../../build/reference/linker-options.md) para obtener una lista completa.  
  
 Al ejecutar vínculo fuera del entorno de desarrollo, se puede especificar la entrada de una o más maneras:  
  
-   En la [línea de comandos](../../build/reference/linker-command-line-syntax.md)  
  
-   Usar [archivos de comandos](../../build/reference/link-command-files.md)  
  
-   En [variables de entorno](../../build/reference/link-environment-variables.md)  
  
 Opciones de procesos primer vínculo especificado en la variable de entorno LINK, y luego las opciones en el orden en que se especifican en la línea de comandos y en archivos de comandos. Si una opción se repite con diferentes argumentos, la penúltima procesa tiene prioridad.  
  
 Opciones se aplican a la generación completa; No hay ninguna opción puede aplicarse a los archivos de entrada específicos.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)