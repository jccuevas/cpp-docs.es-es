---
title: 'Traducción: Diagnóstico'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: 4863b97dc1db7ff295b5f786ca97da2551d0fa62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665002"
---
# <a name="translation-diagnostics"></a>Traducción: Diagnóstico

**ANSI 2.1.1.3** Cómo se identifica un diagnóstico

Microsoft C muestra mensajes de error con el formato:

> *filename* **(** *line-number* **) :** *diagnostic* **C**<em>number</em> *message*

donde *filename* es el nombre del archivo de código fuente en el que se encontró el error; *line-number* es el número de línea en el que el compilador detectó el error; *diagnostic* es un "error" o "advertencia"; *number* es un número único de cuatro dígitos (precedido de una **C**, como se indica en la sintaxis) que identifica el error o la advertencia; *message* es un mensaje explicativo.

## <a name="see-also"></a>Vea también

[Comportamiento definido por la implementación](../c-language/implementation-defined-behavior.md)