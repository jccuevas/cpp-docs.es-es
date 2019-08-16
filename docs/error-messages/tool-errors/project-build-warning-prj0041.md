---
title: Advertencia PRJ0041 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: b0fceff05ffe35515965b7e0a880c8b4c941b07e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297728"
---
# <a name="project-build-warning-prj0041"></a>Advertencia PRJ0041 al compilar el proyecto

No se puede encontrar que falta la dependencia 'dependencia' archivo 'archivo'. El proyecto aún puede compilarse, pero puede que continúe pareciendo obsoleto hasta que se encuentra este archivo.

Un archivo (archivo de recursos o.idl/.odl, por ejemplo, contiene una instrucción include que el sistema del proyecto no se pudo resolver.

Dado que el sistema del proyecto no procesa las instrucciones de preprocesador (#if, por ejemplo), la instrucción infractor no puede ser realmente parte de la compilación.

Para resolver esta advertencia, elimine todo el código en archivos .rc innecesario o agregar archivos de marcador de posición del nombre adecuado.