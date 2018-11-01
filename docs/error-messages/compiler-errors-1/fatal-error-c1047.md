---
title: Error irrecuperable C1047
ms.date: 11/04/2016
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
ms.openlocfilehash: 053c4d828b3583d0e16ab8f4fe03a4b0bbed96f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663201"
---
# <a name="fatal-error-c1047"></a>Error irrecuperable C1047

El objeto o el archivo de biblioteca 'file' se creó con un compilador anterior a otros objetos; recompile las bibliotecas y los objetos antiguos.

El error C1047 se produce cuando los archivos o bibliotecas de objeto compilados con **/LTCG** están vinculados entre sí, pero donde se crean esos archivos o bibliotecas de objetos con versiones diferentes del conjunto de herramientas de Visual C++.

Esto puede suceder si empieza a usar una nueva versión del compilador pero no realiza una recompilación limpia de las bibliotecas o los archivos de objetos existentes.

Para resolver el error C1047, recompile todos los archivos y bibliotecas de objetos.