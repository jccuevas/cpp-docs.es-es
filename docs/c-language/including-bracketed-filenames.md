---
title: Inclusión de nombres de archivo entre corchetes
ms.date: 11/04/2016
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
ms.openlocfilehash: 87de00814f58ed86ee33abdcf96dd210f418c5ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233104"
---
# <a name="including-bracketed-filenames"></a>Inclusión de nombres de archivo entre corchetes

**ANSI 3.8.2** El método para buscar archivos de código fuente que se pueden incluir

Para las especificaciones de archivo incluidas entre corchetes angulares, el preprocesador no busca en los directorios de los archivos principales. Un archivo "principal" es el archivo que contiene la directiva [#include](../preprocessor/hash-include-directive-c-cpp.md). En su lugar, comienza buscando el archivo en los directorios especificados en la línea de comandos del compilador detrás de /I. Si la opción /I no está presente o produce un error, el preprocesador utiliza la variable de entorno INCLUDE para buscar cualquier archivo de inclusión dentro de los paréntesis angulares. La variable de entorno INCLUDE puede contener varias rutas de acceso, separadas por punto y coma ( **;** ). Si aparece más de un directorio como parte de la opción /I o en la variable de entorno INCLUDE, el preprocesador los busca en el orden en que aparecen.

## <a name="see-also"></a>Vea también

[Preprocesar directivas](../c-language/preprocessing-directives.md)
