---
title: 2.4 trabajo construcciones de uso compartido | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5353bc51f6a701201520f700057ef76ce7778191
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="24-work-sharing-constructs"></a>2.4 Construcciones de uso compartido
Una construcción de uso compartido de trabajo distribuye la ejecución de la instrucción asociada entre los miembros del equipo que se encuentra. Las directivas de uso compartido no iniciarán nuevos subprocesos y no hay ninguna barrera implícita en la entrada a una construcción de uso compartido.  
  
 Construye la secuencia de uso compartido y **barrera** directivas encontradas deben ser el mismo para todos los subprocesos en un equipo.  
  
 OpenMP define las siguientes construcciones de uso compartido y se describen en las secciones siguientes:  
  
-   **para** (directiva)  
  
-   **secciones** directiva  
  
-   **solo** (directiva)