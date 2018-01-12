---
title: Ejecutar un programa en el preprocesamiento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ef000f6611c9cb3794da8e46e6b905e57d5ecf92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="executing-a-program-in-preprocessing"></a>Ejecutar un programa en el preprocesamiento
Para usar el código de salida de un comando durante el preprocesamiento, especifique el comando, con los argumentos, entre corchetes ([]). Cualquier macro se expande antes de que se ejecuta el comando. NMAKE reemplaza la especificación de comandos con código de salida del comando, que puede usar en una expresión para controlar el preprocesamiento.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones de preprocesamiento de archivos MAKE](../build/expressions-in-makefile-preprocessing.md)