---
title: Error irrecuperable A1017 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb98eab68da417526a75beaa57870ce906c85a8d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688564"
---
# <a name="ml-fatal-error-a1017"></a>Error irrecuperable A1017 de ML

**nombre de archivo de origen que faltan**

ML no encontró un archivo para ensamblar o pasar al vinculador.

Este error se genera cuando se proporcionan opciones de línea de comandos de ML sin especificar un nombre de archivo que va a actuar. Para montar los archivos que no tienen una extensión .asm, utilice el **/Ta** opción de línea de comandos.

Este error también puede generarse mediante la invocación de ML sin parámetros si la variable de entorno de Machine Learning contiene las opciones de línea de comandos.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>