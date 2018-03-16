---
title: 2.4 trabajo construcciones de uso compartido | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 476e4e23b22527accaa095d80b827c95aed58c15
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
---
# <a name="24-work-sharing-constructs"></a>2.4 Construcciones de uso compartido
Una construcción de uso compartido de trabajo distribuye la ejecución de la instrucción asociada entre los miembros del equipo que se encuentra. Las directivas de uso compartido no iniciarán nuevos subprocesos y no hay ninguna barrera implícita en la entrada a una construcción de uso compartido.  
  
 Construye la secuencia de uso compartido y **barrera** directivas encontradas deben ser el mismo para todos los subprocesos en un equipo.  
  
 OpenMP define las siguientes construcciones de uso compartido y se describen en las secciones siguientes:  
  
-   **para** (directiva)  
  
-   **secciones** directiva  
  
-   **solo** (directiva)