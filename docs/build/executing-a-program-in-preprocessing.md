---
title: Ejecutar un programa en el preprocesamiento
ms.date: 11/04/2016
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
ms.openlocfilehash: a78c9ddc498383d460e617bc26f4e70eb7275eec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577429"
---
# <a name="executing-a-program-in-preprocessing"></a>Ejecutar un programa en el preprocesamiento

Para usar el código de salida de un comando durante el preprocesamiento, especifique el comando, con los argumentos, entre corchetes ([]). Antes de ejecutar el comando, se expanden las macros. NMAKE reemplaza la especificación de comando con el código de salida del comando, que se puede usar en una expresión para controlar el preprocesamiento.

## <a name="see-also"></a>Vea también

[Expresiones de preprocesamiento de archivos MAKE](../build/expressions-in-makefile-preprocessing.md)