---
title: Error PRJ0033 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0033
dev_langs:
- C++
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c70bd942123c48866c3353443b478de4953668de
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036077"
---
# <a name="project-build-error-prj0033"></a>Error PRJ0033 al compilar el proyecto

La propiedad 'Dependencias adicionales' para la compilación personalizada del paso de archivo 'archivo' contenía 'macro' que se evalúa como 'expansión_de_macro'.

Un paso de compilación personalizada en un archivo contenía un error en su dependencia adicional, probablemente debido a un problema de evaluación de macro. Este error también puede significar que la ruta de acceso es incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.

Para resolver este error, corrija la macro o corrija la especificación de ruta de acceso. La ruta de acceso evaluada es una ruta de acceso absoluta del directorio de proyecto.