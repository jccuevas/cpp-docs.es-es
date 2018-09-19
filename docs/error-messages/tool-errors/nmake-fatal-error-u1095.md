---
title: Error grave de NMAKE U1095 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1095
dev_langs:
- C++
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964ec1d029e56a5d9d78659ad919c71a4e44506d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039886"
---
# <a name="nmake-fatal-error-u1095"></a>Error grave de NMAKE U1095

línea de comandos expandida 'líneaDeComandos' es demasiado largo

Después de la expansión de macro, la línea de comandos especificada supera el límite de longitud de las líneas de comandos para el sistema operativo.

MS-DOS permite hasta 128 caracteres en una línea de comandos.

Si el comando es para un programa que puede aceptar la entrada de línea de comandos desde un archivo, cambie el comando y proporcione la entrada desde un archivo en disco o un archivo en línea. Por ejemplo, vínculo y LIB aceptan la entrada desde un archivo de respuesta.