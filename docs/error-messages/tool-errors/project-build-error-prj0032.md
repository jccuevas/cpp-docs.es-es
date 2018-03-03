---
title: Error PRJ0032 al compilar del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0032
dev_langs:
- C++
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92497027db3a2449914696f03fc86a144a48b62e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0032"></a>Error PRJ0032 al compilar el proyecto
La propiedad 'Outputs' del paso de compilación personalizada de nivel de proyecto contenía 'macro' que se evalúa como 'expansión_de_macro'.  
  
 Un paso de compilación personalizada en un proyecto presentó un resultado erróneo debido probablemente a un problema de evaluación de macro. Este error también puede significar que la ruta de acceso tiene un formato incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.  
  
 Para resolver este error, corrija la macro o corrija la especificación de ruta de acceso. La ruta evaluada es una ruta de acceso absoluta del directorio de proyecto.