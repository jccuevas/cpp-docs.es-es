---
title: Error PRJ0033 al compilar del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0033
dev_langs:
- C++
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0cd7bcc0239ce88a19ae6009195f120a88be59ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0033"></a>Error PRJ0033 al compilar el proyecto
La propiedad 'Dependencias adicionales' para la compilación personalizada del paso de archivo 'archivo' contenía 'macro' que se evalúa como 'expansión_de_macro'.  
  
 Un paso de compilación personalizada en un archivo contenía un error en su dependencia adicional, probablemente debido a un problema de evaluación de macro. Este error también puede significar que la ruta de acceso tiene un formato incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.  
  
 Para resolver este error, corrija la macro o corrija la especificación de ruta de acceso. La ruta evaluada es una ruta de acceso absoluta del directorio de proyecto.