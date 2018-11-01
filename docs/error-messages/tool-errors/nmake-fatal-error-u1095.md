---
title: Error grave de NMAKE U1095
ms.date: 11/04/2016
f1_keywords:
- U1095
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
ms.openlocfilehash: 0ff71a229defe7a12886c1154a69bcf0432b8cca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548777"
---
# <a name="nmake-fatal-error-u1095"></a>Error grave de NMAKE U1095

línea de comandos expandida 'líneaDeComandos' es demasiado largo

Después de la expansión de macro, la línea de comandos especificada supera el límite de longitud de las líneas de comandos para el sistema operativo.

MS-DOS permite hasta 128 caracteres en una línea de comandos.

Si el comando es para un programa que puede aceptar la entrada de línea de comandos desde un archivo, cambie el comando y proporcione la entrada desde un archivo en disco o un archivo en línea. Por ejemplo, vínculo y LIB aceptan la entrada desde un archivo de respuesta.