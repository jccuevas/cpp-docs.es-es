---
title: Compilador advertencia (nivel 3) C4622 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4622
dev_langs:
- C++
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d91e3c914d6c3feeb9d2326c94efe2bc54ac98f4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023246"
---
# <a name="compiler-warning-level-3-c4622"></a>Advertencia del compilador (nivel 3) C4622

Reemplazando la información de depuración formada durante la creación del encabezado precompilado en el archivo objeto: 'file'

Se perdió la información de CodeView del archivo especificado al compilarse con la opción [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (use encabezados precompilado.).

Cambie el nombre del archivo objeto (mediante [/fo](../../build/reference/fo-object-file-name.md)) al crear o usar el archivo de encabezado precompilado y vincúlelo con el nuevo archivo de objeto.