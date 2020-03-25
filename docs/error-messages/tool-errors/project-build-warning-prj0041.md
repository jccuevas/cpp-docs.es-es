---
title: Advertencia PRJ0041 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: bb6469b1daf193223a9b3361cc3e4bfb96d0c751
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191942"
---
# <a name="project-build-warning-prj0041"></a>Advertencia PRJ0041 al compilar el proyecto

No se encuentra la dependencia ' Dependency ' que falta para el archivo ' file '. El proyecto todavía puede compilarse, pero puede que siga apareciendo sin actualizar hasta que se encuentre este archivo.

Un archivo (archivo de recursos o archivo. idl/. ODL, por ejemplo, contiene una instrucción include que el sistema del proyecto no pudo resolver.

Dado que el sistema del proyecto no procesa instrucciones de preprocesador (#if, por ejemplo), es posible que la instrucción infractora no forme parte realmente de la compilación.

Para resolver esta advertencia, elimine todo el código innecesario en los archivos. RC o agregue los archivos de marcador de posición con el nombre adecuado.
