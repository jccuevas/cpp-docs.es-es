---
title: Error irrecuperable C1210
ms.date: 11/04/2016
f1_keywords:
- C1210
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
ms.openlocfilehash: 50bafa522c931c909b5ce163a78305ffc028765a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203390"
---
# <a name="fatal-error-c1210"></a>Error irrecuperable C1210

> La versión del runtime instalada no admite /clr:pure ni /clr:safe

Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

El error C1210 se produce cuando tiene un compilador para la versión actual, pero un Common Language Runtime de una versión anterior.

Parte de la funcionalidad del compilador podría no funcionar en una versión anterior de runtime.

Para solucionar el error C1210, instale la versión de Common Language Runtime pensada para su uso con el compilador.
