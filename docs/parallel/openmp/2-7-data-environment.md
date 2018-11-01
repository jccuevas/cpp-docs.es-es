---
title: 2.7 Entorno de datos
ms.date: 11/04/2016
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
ms.openlocfilehash: b65dfc7d7694b36ef4f89351579cd73e07ab537c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491978"
---
# <a name="27-data-environment"></a>2.7 Entorno de datos

En esta sección se presenta una directiva y varias cláusulas para controlar el entorno de datos durante la ejecución de las regiones en paralelo, como sigue:

- Un **threadprivate** directiva (consulte la sección siguiente) se proporciona para hacer que variables estáticas del ámbito de bloque, ámbito de espacio de nombres o ámbito de archivo local a un subproceso.

- Las cláusulas que se pueden especificar en las directivas para controlar los atributos de uso compartido de las variables de la duración de las construcciones paralelas o uso compartido se describen en [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.