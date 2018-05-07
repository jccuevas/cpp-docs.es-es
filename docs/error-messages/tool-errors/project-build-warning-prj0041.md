---
title: Advertencia PRJ0041 al compilar del proyecto | Documentos de Microsoft
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
ms.openlocfilehash: 6e845967b0a7116d6edade98b571de5bc1bcd9a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-warning-prj0041"></a>Advertencia PRJ0041 al compilar el proyecto
No se puede encontrar que falta la dependencia 'dependencia' archivo 'archivo'. El proyecto aún puede generarse, pero puede seguir apareciendo obsoletos hasta que se encuentra este archivo.  
  
 Un archivo (archivo de recursos o.idl/.odl, por ejemplo, contiene una instrucción include que el sistema del proyecto no se pudo resolver.  
  
 Dado que el sistema del proyecto no procesa las instrucciones de preprocesador (por ejemplo, #if), la instrucción infractor no sea realmente parte de la compilación.  
  
 Para resolver esta advertencia, elimine todo el código necesario en los archivos .rc o agregue archivos de marcador de posición del nombre adecuado.