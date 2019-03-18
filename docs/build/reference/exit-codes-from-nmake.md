---
title: Códigos de salida de NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
ms.openlocfilehash: 25ea4060e7b7a968b6a9da78f344e645c5d43a44
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826392"
---
# <a name="exit-codes-from-nmake"></a>Códigos de salida de NMAKE

NMAKE devuelve los siguientes códigos de salida:

|Código|Significado|
|----------|-------------|
|0|Ningún error (posiblemente una advertencia)|
|1|Generación incompleta (emitida solo cuando se usa/k)|
|2|Error en un programa, posiblemente debido a uno de los siguientes:|
||-Un error de sintaxis en el archivo MAKE|
||-Un código de error o de salida de un comando|
||-Una interrupción por el usuario|
|4|Error del sistema: memoria insuficiente|
|255|Destino no está actualizado (emite solo cuando se usa/q)|

## <a name="see-also"></a>Vea también

[Ejecución de NMAKE](running-nmake.md)
