---
title: Error del compilador de recursos RC2147 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2147
dev_langs:
- C++
helpviewer_keywords:
- RC2147
ms.assetid: 09974f06-1731-4e70-b373-f9218e0ee8d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f3ca510dfd61e92a33f599c7ef261e03b8ad2cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032856"
---
# <a name="resource-compiler-error-rc2147"></a>Error del compilador de recursos RC2147

Identificador de SUBIDIOMA no es un número

El valor de identificador de SUBIDIOMA debe ser un número.

La instrucción **LANGUAGE** debe usar la sintaxis siguiente:

**LANGUAGE** *Id_idioma_primario*,*Id_idioma_secundario*

Identificadores de SUBIDIOMA válidos se definen como **sublang dentro** constantes en el archivo WINNT.h.