---
title: Error grave de NMAKE U1095
ms.date: 11/04/2016
f1_keywords:
- U1095
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
ms.openlocfilehash: 55c7ca7d237655b7e20406e7f28e5b2471bdec53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193464"
---
# <a name="nmake-fatal-error-u1095"></a>Error grave de NMAKE U1095

línea de comandos expandida ' CommandLine ' demasiado larga

Después de la expansión de macros, la línea de comandos dada supera el límite de longitud de las líneas de comandos del sistema operativo.

MS-DOS permite hasta 128 caracteres en una línea de comandos.

Si el comando es para un programa que puede aceptar la entrada de la línea de comandos de un archivo, cambie el comando y proporcione la entrada de un archivo en disco o en un archivo insertado. Por ejemplo, LINK y LIB aceptan la entrada de un archivo de respuesta.
