---
title: 2.7 entorno de datos | Documentos de Microsoft
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
ms.openlocfilehash: d1b0f253ce14ffc5d3740e582a9a51feea56ad32
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690070"
---
# <a name="27-data-environment"></a>2.7 Entorno de datos
Esta sección presenta una directiva y varias cláusulas para controlar el entorno de datos durante la ejecución de regiones en paralelo, como se indica a continuación:  
  
-   A **threadprivate** directiva (vea la sección siguiente) se proporciona para poner el ámbito de archivo, ámbito de espacio de nombres o las variables de ámbito de bloque estática local a un subproceso.  
  
-   Las cláusulas que se pueden especificar en las directivas para controlar los atributos de uso compartido de variables para la duración de las construcciones paralelas o uso compartido se describen en [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en página 25.