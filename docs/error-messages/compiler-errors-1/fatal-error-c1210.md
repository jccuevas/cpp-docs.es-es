---
title: Error irrecuperable C1210 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1210
dev_langs:
- C++
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d22a34f44fb2c97fe341cb313d7917a35506cdd
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704989"
---
# <a name="fatal-error-c1210"></a>Error irrecuperable C1210

> La versión del runtime instalada no admite /clr:pure ni /clr:safe

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

El error C1210 se produce cuando tiene un compilador para la versión actual, pero un Common Language Runtime de una versión anterior.

Parte de la funcionalidad del compilador podría no funcionar en una versión anterior de runtime.

Para solucionar el error C1210, instale la versión de Common Language Runtime pensada para su uso con el compilador.