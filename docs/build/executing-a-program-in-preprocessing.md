---
title: Ejecutar un programa en el preprocesamiento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da87a87a2e97736d202b7ddb9be2dbec54fed44d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367204"
---
# <a name="executing-a-program-in-preprocessing"></a>Ejecutar un programa en el preprocesamiento
Para usar el código de salida de un comando durante el preprocesamiento, especifique el comando, con los argumentos, entre corchetes ([]). Cualquier macro se expande antes de que se ejecuta el comando. NMAKE reemplaza la especificación de comandos con código de salida del comando, que puede usar en una expresión para controlar el preprocesamiento.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones de preprocesamiento de archivos MAKE](../build/expressions-in-makefile-preprocessing.md)