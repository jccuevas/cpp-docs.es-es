---
title: Códigos de salida de NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
ms.openlocfilehash: 07a104d90d91a027864022d4c82412318eb5fe3d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413243"
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

[Ejecución de NMAKE](../build/running-nmake.md)
