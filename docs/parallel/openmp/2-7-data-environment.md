---
title: 2.7 entorno de datos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e018a2c1b20bef640852ced913dc90266e733c06
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="27-data-environment"></a>2.7 Entorno de datos
Esta sección presenta una directiva y varias cláusulas para controlar el entorno de datos durante la ejecución de regiones en paralelo, como se indica a continuación:  
  
-   A **threadprivate** directiva (vea la sección siguiente) se proporciona para poner el ámbito de archivo, ámbito de espacio de nombres o las variables de ámbito de bloque estática local a un subproceso.  
  
-   Las cláusulas que se pueden especificar en las directivas para controlar los atributos de uso compartido de variables para la duración de las construcciones paralelas o uso compartido se describen en [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en página 25.