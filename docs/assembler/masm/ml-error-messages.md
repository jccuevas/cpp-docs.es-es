---
title: Mensajes de error de ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: 2db928d22219d33f89396bb29530680d4b3c8dba
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856948"
---
# <a name="ml-error-messages"></a>Mensajes de error de ML

Los mensajes de error generados por los componentes de MASM se dividen en tres categorías:

- **Errores irrecuperables.** Esto indica un problema grave que impide que la utilidad complete su proceso normal.

- **Errores no graves.** La utilidad puede completar su proceso. Si es así, no es probable que su resultado sea el que desee.

- **ADVERTENCIAS.** Estos mensajes indican condiciones que pueden impedir que se obtengan los resultados deseados.

Todos los mensajes de error tienen el siguiente formato:

> *Utilidad*: *filename* (*línea*): {*Error_type*} (*código*): *Message_text*

donde:

\ de la *utilidad*
Programa que envió el mensaje de error.

*Nombre de archivo*\
El archivo que contiene la condición de generación de errores.

\ de *línea*
La línea aproximada en la que existe la condición de error.

*Error_type*\
Error irrecuperable, error o advertencia.

*Código*\
Código de error único de 5 o 6 dígitos.

*Message_text*\
Descripción breve y general de la condición de error.

## <a name="see-also"></a>Vea también

[Referencia de Microsoft macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)
