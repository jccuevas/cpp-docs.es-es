---
title: Error del compilador de recursos RC2148 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2148
dev_langs:
- C++
helpviewer_keywords:
- RC2148
ms.assetid: 0290065c-35d3-4815-80c5-40bf7132ae1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b78bf8e9eb9ebe86dae75856ea3c0b6f5d34a26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075915"
---
# <a name="resource-compiler-error-rc2148"></a>Error del compilador de recursos RC2148

Identificador de SUBIDIOMA demasiado grande

El valor de identificador de SUBIDIOMA estaba fuera del intervalo.

La instrucción **LANGUAGE** debe usar la sintaxis siguiente:

**LANGUAGE** *Id_idioma_primario*,*Id_idioma_secundario*

Identificadores de SUBIDIOMA válidos se definen como **sublang dentro** constantes en el archivo WINNT.h.