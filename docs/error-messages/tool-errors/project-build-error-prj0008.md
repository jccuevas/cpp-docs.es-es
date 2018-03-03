---
title: Error PRJ0008 al compilar del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0008
dev_langs:
- C++
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1740b0cf1edfc90258de4fe26478298ddf2875c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0008"></a>Error PRJ0008 al compilar el proyecto
No se pudo eliminar el archivo 'archivo'.  
  
 **Asegúrese de que el archivo no está abierto en otro proceso y no está protegida contra escritura.**  
  
 Al volver a generar o al limpiar, Visual C++ elimina todos los archivos conocidos de intermedios y de salida de la compilación, así como los archivos que cumplen las especificaciones de comodines en el **extensiones para eliminar al limpiar** propiedad en la [General Página de propiedades de configuración de configuración](../../ide/general-property-page-project.md).  
  
 Verá este error si no se puede eliminar un archivo de Visual C++. Para resolver el error, asigne al archivo y su directorio de escritura para el usuario que se va a generar.