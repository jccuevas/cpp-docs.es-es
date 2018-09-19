---
title: Error PRJ0008 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0008
dev_langs:
- C++
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7c24634a845423de590228af01cb9f4779e37ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062792"
---
# <a name="project-build-error-prj0008"></a>Error PRJ0008 al compilar el proyecto

No se pudo eliminar el archivo 'archivo'.

**Asegúrese de que el archivo no está abierto por otro proceso y no está protegido contra escritura.**

Durante una regeneración o limpiar, Visual C++ elimina todos los archivos conocidos de intermedios y de salida de la compilación, así como los archivos que cumplan las especificaciones del comodín en el **extensiones para eliminar al limpiar** propiedad en el [General Página de propiedades de opciones de configuración](../../ide/general-property-page-project.md).

Verá este error si no puede eliminar un archivo de Visual C++. Para resolver el error, asegúrese del archivo y su directorio de escritura para el usuario que se va a generar.