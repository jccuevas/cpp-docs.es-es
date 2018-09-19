---
title: Diagnóstico impreso por la función assert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac5473a2dd592bbd9af2f65044d3d7d97515dc37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103391"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnóstico impreso por la función assert

**ANSI 4.2** El diagnóstico impreso por la función **assert** y su comportamiento de finalización

La función **assert** imprime un mensaje de diagnóstico y llama a la rutina **abort** si la expresión es false (0). El mensaje de diagnóstico tiene la forma

> **Error de aserción**: <em>expression</em>**, archivo** <em>filename</em>**, línea** *linenumber*

donde *filename* es el nombre del archivo de código fuente y *linenumber* es el número de línea de la aserción que produjo un error en el archivo de código fuente. No se realiza ninguna acción si la *expresión* es true (distinto de cero).

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)