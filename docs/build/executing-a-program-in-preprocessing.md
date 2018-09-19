---
title: Ejecutar un programa en el preprocesamiento | Microsoft Docs
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
ms.openlocfilehash: e2b0571e67e7c5d24cf31dce6fce548735cad966
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721466"
---
# <a name="executing-a-program-in-preprocessing"></a>Ejecutar un programa en el preprocesamiento

Para usar el código de salida de un comando durante el preprocesamiento, especifique el comando, con los argumentos, entre corchetes ([]). Antes de ejecutar el comando, se expanden las macros. NMAKE reemplaza la especificación de comando con el código de salida del comando, que se puede usar en una expresión para controlar el preprocesamiento.

## <a name="see-also"></a>Vea también

[Expresiones de preprocesamiento de archivos MAKE](../build/expressions-in-makefile-preprocessing.md)