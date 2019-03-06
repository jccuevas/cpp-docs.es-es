---
title: Ejecutar un programa en el preprocesamiento
ms.date: 11/04/2016
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
ms.openlocfilehash: d95079349981b073533bb00abcd053454542a044
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413308"
---
# <a name="executing-a-program-in-preprocessing"></a>Ejecutar un programa en el preprocesamiento

Para usar el código de salida de un comando durante el preprocesamiento, especifique el comando, con los argumentos, entre corchetes ([]). Antes de ejecutar el comando, se expanden las macros. NMAKE reemplaza la especificación de comando con el código de salida del comando, que se puede usar en una expresión para controlar el preprocesamiento.

## <a name="see-also"></a>Vea también

[Expresiones de preprocesamiento de archivos MAKE](../build/expressions-in-makefile-preprocessing.md)
