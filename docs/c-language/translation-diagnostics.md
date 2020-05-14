---
title: 'Conversión: Diagnóstico'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: a274b7c5f29b091b2bf29922abfa4d66d3447b47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344972"
---
# <a name="translation-diagnostics"></a>Conversión: Diagnóstico

**ANSI 2.1.1.3** Cómo se identifica un diagnóstico

Microsoft C muestra mensajes de error con el formato:

> *filename* **(** *line-number* **) :** *diagnostic* **C**<em>number</em> *message*

donde *filename* es el nombre del archivo de código fuente en el que se encontró el error; *line-number* es el número de línea en el que el compilador detectó el error; *diagnostic* es un "error" o "advertencia"; *number* es un número único de cuatro dígitos (precedido de una **C**, como se indica en la sintaxis) que identifica el error o la advertencia; *message* es un mensaje explicativo.

## <a name="see-also"></a>Vea también

[Comportamiento definido por la implementación](../c-language/implementation-defined-behavior.md)
