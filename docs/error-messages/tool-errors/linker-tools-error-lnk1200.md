---
title: Las herramientas del vinculador LNK1200 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03ecd51142bf30230b6b177a36e007345e93bf2c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059321"
---
# <a name="linker-tools-error-lnk1200"></a>Error de las herramientas del vinculador LNK1200

Error al leer la base de datos de programa 'filename'

No se pudo leer la base de datos de programa (PDB).

Este error puede deberse a daños en el archivo.

Si `filename` es el archivo PDB de un archivo de objeto, vuelva a compilar el archivo de objeto mediante [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Si `filename` es el archivo PDB para el archivo de salida principal, y este error se produjo durante una vinculación incremental, elimine el archivo PDB y volver a vincular.