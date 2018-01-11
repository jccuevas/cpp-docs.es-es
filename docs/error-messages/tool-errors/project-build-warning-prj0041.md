---
title: Advertencia PRJ0041 al compilar del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0041
dev_langs: C++
helpviewer_keywords: PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 231b58cb0c13d1a3f87e010a5100da564b0be806
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-warning-prj0041"></a>Advertencia PRJ0041 al compilar el proyecto
No se puede encontrar que falta la dependencia 'dependencia' archivo 'archivo'. El proyecto aún puede generarse, pero puede seguir apareciendo obsoletos hasta que se encuentra este archivo.  
  
 Un archivo (archivo de recursos o.idl/.odl, por ejemplo, contiene una instrucción include que el sistema del proyecto no se pudo resolver.  
  
 Dado que el sistema del proyecto no procesa las instrucciones de preprocesador (por ejemplo, #if), la instrucción infractor no sea realmente parte de la compilación.  
  
 Para resolver esta advertencia, elimine todo el código necesario en los archivos .rc o agregue archivos de marcador de posición del nombre adecuado.