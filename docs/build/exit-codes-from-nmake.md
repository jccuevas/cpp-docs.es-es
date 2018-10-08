---
title: Códigos de salida de NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c70c76292b62560b1d9895aca2851b4cf56802b
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861803"
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