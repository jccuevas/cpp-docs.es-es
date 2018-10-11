---
title: 'Traducción: Diagnóstico | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d297cfd4f4dee49d3344ae2f159f85682f05ea2f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017591"
---
# <a name="translation-diagnostics"></a>Traducción: Diagnóstico

**ANSI 2.1.1.3** Cómo se identifica un diagnóstico

Microsoft C muestra mensajes de error con el formato:

> *filename* **(** *line-number* **) :** *diagnostic* **C**<em>number</em> *message*

donde *filename* es el nombre del archivo de código fuente en el que se encontró el error; *line-number* es el número de línea en el que el compilador detectó el error; *diagnostic* es un "error" o "advertencia"; *number* es un número único de cuatro dígitos (precedido de una **C**, como se indica en la sintaxis) que identifica el error o la advertencia; *message* es un mensaje explicativo.

## <a name="see-also"></a>Vea también

[Comportamiento definido por la implementación](../c-language/implementation-defined-behavior.md)