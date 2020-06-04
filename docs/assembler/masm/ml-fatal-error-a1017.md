---
title: Error irrecuperable A1017 de ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 523fed26afae5a88c5f154283487d3453a2e48c7
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318064"
---
# <a name="ml-fatal-error-a1017"></a>Error irrecuperable A1017 de ML

**falta el nombre de archivo de origen**

ML no pudo encontrar un archivo para ensamblar o pasar al vinculador.

Este error se genera cuando se asignan opciones de línea de comandos de ML sin especificar un nombre de archivo en el que actuar. Para ensamblar archivos que no tengan una extensión. ASM, use la opción de línea de comandos **/TA** .

Este error también se puede generar mediante la invocación de ML sin parámetros si la variable de entorno de ML contiene opciones de línea de comandos.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](ml-error-messages.md)
