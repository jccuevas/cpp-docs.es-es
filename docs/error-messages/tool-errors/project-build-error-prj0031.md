---
title: Error PRJ0031 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0031
dev_langs:
- C++
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce97e8f540295f5a2968fce22312b8e0e34cfd2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076897"
---
# <a name="project-build-error-prj0031"></a>Error PRJ0031 al compilar el proyecto

La propiedad 'Outputs' de la compilación personalizada del paso de archivo 'archivo' contenía 'macro' que se evalúa como 'expansión_de_macro'.

Un paso de compilación personalizada en un archivo tenía un resultado erróneo debido probablemente a un problema de evaluación de macro. Este error también puede significar que la ruta de acceso es incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.

Para resolver este error, corrija la macro o corrija la especificación de ruta de acceso. La ruta de acceso evaluada es una ruta de acceso absoluta del directorio de proyecto.