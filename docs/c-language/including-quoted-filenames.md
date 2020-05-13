---
title: Inclusión de nombres de archivo entre comillas
ms.date: 11/04/2016
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
ms.openlocfilehash: 4083519d6f6b9b4d037b0c2998737f3a5062c6cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232961"
---
# <a name="including-quoted-filenames"></a>Inclusión de nombres de archivo entre comillas

**ANSI 3.8.2** Compatibilidad con nombres entrecomillados para archivos de código fuente que se pueden incluir

Si detalla una especificación de ruta de acceso completa y no ambigua para el archivo de inclusión entre dos elementos de comillas dobles (" "), el preprocesador solo busca la especificación de ruta de acceso y omite los directorios estándar.

Para los archivos de inclusión especificados como [#include](../preprocessor/hash-include-directive-c-cpp.md) "especificación de ruta de acceso", la búsqueda de directorio comienza con los directorios del archivo primario y continúa con los directorios de los archivos primarios principales. De este modo, la búsqueda comienza en relación con el directorio que contiene el archivo de código fuente que se está procesando actualmente. Si no hay ningún archivo primario principal y no se ha encontrado el archivo, la búsqueda continúa como si el nombre de archivo estuviese entre corchetes angulares.

## <a name="see-also"></a>Vea también

[Preprocesar directivas](../c-language/preprocessing-directives.md)
