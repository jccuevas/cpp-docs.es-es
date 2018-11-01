---
title: Error irrecuperable A1017 de ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 22a16569364760d0cb1d01011405f7a11dd21cac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560828"
---
# <a name="ml-fatal-error-a1017"></a>Error irrecuperable A1017 de ML

**nombre de archivo de origen que faltan**

ML no encontró un archivo para ensamblar o pasar al vinculador.

Este error se genera cuando se proporcionan opciones de línea de comandos de ML sin especificar un nombre de archivo que va a actuar. Para montar los archivos que no tienen una extensión .asm, utilice el **/Ta** opción de línea de comandos.

Este error también puede generarse mediante la invocación de ML sin parámetros si la variable de entorno de Machine Learning contiene las opciones de línea de comandos.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>