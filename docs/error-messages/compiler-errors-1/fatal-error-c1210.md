---
title: Error irrecuperable C1210
ms.date: 11/04/2016
f1_keywords:
- C1210
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
ms.openlocfilehash: a90ca3e3b55642f1a6cd847997b83e4b7db46818
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591816"
---
# <a name="fatal-error-c1210"></a>Error irrecuperable C1210

> La versión del runtime instalada no admite /clr:pure ni /clr:safe

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

El error C1210 se produce cuando tiene un compilador para la versión actual, pero un Common Language Runtime de una versión anterior.

Parte de la funcionalidad del compilador podría no funcionar en una versión anterior de runtime.

Para solucionar el error C1210, instale la versión de Common Language Runtime pensada para su uso con el compilador.