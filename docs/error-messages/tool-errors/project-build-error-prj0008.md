---
title: Error PRJ0008 al compilar del proyecto | Documentos de Microsoft
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
ms.openlocfilehash: 4011a27b7e6707f9c9b4e3ed386306b00f2792cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317650"
---
# <a name="project-build-error-prj0008"></a>Error PRJ0008 al compilar el proyecto
No se pudo eliminar el archivo 'archivo'.  
  
 **Asegúrese de que el archivo no está abierto en otro proceso y no está protegida contra escritura.**  
  
 Al volver a generar o al limpiar, Visual C++ elimina todos los archivos conocidos de intermedios y de salida de la compilación, así como los archivos que cumplen las especificaciones de comodines en el **extensiones para eliminar al limpiar** propiedad en la [General Página de propiedades de configuración de configuración](../../ide/general-property-page-project.md).  
  
 Verá este error si no se puede eliminar un archivo de Visual C++. Para resolver el error, asigne al archivo y su directorio de escritura para el usuario que se va a generar.