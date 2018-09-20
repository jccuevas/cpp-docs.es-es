---
title: 2.7 entorno de datos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17c60c621defa15c034f57d0af8f14637db54f03
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378142"
---
# <a name="27-data-environment"></a>2.7 Entorno de datos

En esta sección se presenta una directiva y varias cláusulas para controlar el entorno de datos durante la ejecución de las regiones en paralelo, como sigue:

- Un **threadprivate** directiva (consulte la sección siguiente) se proporciona para hacer que variables estáticas del ámbito de bloque, ámbito de espacio de nombres o ámbito de archivo local a un subproceso.

- Las cláusulas que se pueden especificar en las directivas para controlar los atributos de uso compartido de las variables de la duración de las construcciones paralelas o uso compartido se describen en [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.