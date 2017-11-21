---
title: Error PRJ0031 al compilar del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0031
dev_langs: C++
helpviewer_keywords: PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5aafec3bb4213ec8785cb6f05e0cc5e2ecc72e4a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0031"></a>Error PRJ0031 al compilar el proyecto
La propiedad 'Outputs' de la compilación personalizada del paso de archivo 'archivo' contenía 'macro' que se evalúa como 'expansión_de_macro'.  
  
 Un paso de compilación personalizada en un archivo presentó un resultado erróneo debido probablemente a un problema de evaluación de macro. Este error también puede significar que la ruta de acceso tiene un formato incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.  
  
 Para resolver este error, corrija la macro o corrija la especificación de ruta de acceso. La ruta evaluada es una ruta de acceso absoluta del directorio de proyecto.