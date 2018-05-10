---
title: 2.4 trabajo construcciones de uso compartido | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c00eb94055f26954a283a6172f69228804832ac4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="24-work-sharing-constructs"></a>2.4 Construcciones de uso compartido
Una construcción de uso compartido de trabajo distribuye la ejecución de la instrucción asociada entre los miembros del equipo que se encuentra. Las directivas de uso compartido no iniciarán nuevos subprocesos y no hay ninguna barrera implícita en la entrada a una construcción de uso compartido.  
  
 Construye la secuencia de uso compartido y **barrera** directivas encontradas deben ser el mismo para todos los subprocesos en un equipo.  
  
 OpenMP define las siguientes construcciones de uso compartido y se describen en las secciones siguientes:  
  
-   **para** (directiva)  
  
-   **secciones** directiva  
  
-   **solo** (directiva)