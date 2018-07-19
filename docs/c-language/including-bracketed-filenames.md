---
title: Inclusión de nombres de archivo entre corchetes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ba45c21029a428784e1c8410dcf42295aa6350f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383831"
---
# <a name="including-bracketed-filenames"></a>Inclusión de nombres de archivo entre corchetes
**ANSI 3.8.2** El método para buscar archivos de código fuente que se pueden incluir  
  
 Para las especificaciones de archivo incluidas entre corchetes angulares, el preprocesador no busca en los directorios de los archivos principales. Un archivo "principal" es el archivo que contiene la directiva [#include](../preprocessor/hash-include-directive-c-cpp.md). En su lugar, comienza buscando el archivo en los directorios especificados en la línea de comandos del compilador detrás de /I. Si la opción /I no está presente o produce un error, el preprocesador utiliza la variable de entorno INCLUDE para buscar cualquier archivo de inclusión dentro de los paréntesis angulares. La variable de entorno INCLUDE puede contener varias rutas de acceso, separadas por punto y coma (**;**). Si aparece más de un directorio como parte de la opción /I o en la variable de entorno INCLUDE, el preprocesador los busca en el orden en que aparecen.  
  
## <a name="see-also"></a>Vea también  
 [Preprocesar directivas](../c-language/preprocessing-directives.md)