---
title: Mensajes de error de ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: aa0440afae980e218c32ab3296bd7c6fb2b444d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62202216"
---
# <a name="ml-error-messages"></a>Mensajes de error de ML

Los mensajes de error generados por componentes MASM se dividen en tres categorías:

- **Errores irrecuperables.** Estos errores indican un problema grave que impide que la utilidad de completar el proceso normal.

- **Errores recuperables.** La utilidad puede completar su proceso. Si es así, su resultado no es probable que sea lo que desee.

- **Advertencias.** Estos mensajes indican las condiciones que pueden impedir la obtención de los resultados que desee.

Todos los mensajes de error adoptan la forma siguiente:

> *Utilidad*: *Nombre de archivo* (*línea*): {*Error_type*} (*código*): *Message_text*

donde:

*Utilidad*<br/>
El programa que envió el mensaje de error.

*Nombre de archivo*<br/>
El archivo que contiene la condición de generación de errores.

*Line*<br/>
La línea aproximada donde existe la condición de error.

*Error_type*<br/>
Grave Error, Error o advertencia.

*Código*<br/>
El código de error 5 o 6 dígitos únicos.

*Message_text*<br/>
Una descripción breve y general de la condición de error.

## <a name="see-also"></a>Vea también

[Referencia de Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>