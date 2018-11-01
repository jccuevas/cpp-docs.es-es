---
title: Error irrecuperable C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: 0bfd0c03378b1a9c616a014ac96153b3ab04af9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569219"
---
# <a name="fatal-error-c1054"></a>Error irrecuperable C1054

límite del compilador: los inicializadores están demasiado anidados

El código supera el límite de anidamiento de inicializadores (10-15 niveles, dependiendo de la combinación de tipos que se está inicializando).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Simplifique los tipos de datos que se está inicializando para reducir el anidamiento.

1. Inicialice las variables en instrucciones independientes después de la declaración.