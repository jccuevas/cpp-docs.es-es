---
title: Advertencia PRJ0041 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0041
dev_langs:
- C++
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7677c5718783065f64e52f98f7ddbed76e905d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038144"
---
# <a name="project-build-warning-prj0041"></a>Advertencia PRJ0041 al compilar el proyecto

No se puede encontrar que falta la dependencia 'dependencia' archivo 'archivo'. El proyecto aún puede compilarse, pero puede que continúe pareciendo obsoleto hasta que se encuentra este archivo.

Un archivo (archivo de recursos o.idl/.odl, por ejemplo, contiene una instrucción include que el sistema del proyecto no se pudo resolver.

Dado que el sistema del proyecto no procesa las instrucciones de preprocesador (#if, por ejemplo), la instrucción infractor no puede ser realmente parte de la compilación.

Para resolver esta advertencia, elimine todo el código en archivos .rc innecesario o agregar archivos de marcador de posición del nombre adecuado.