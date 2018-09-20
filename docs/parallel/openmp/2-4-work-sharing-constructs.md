---
title: 2.4 construcciones de uso compartido | Microsoft Docs
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
ms.openlocfilehash: 719b33698b708761f0cd56e65a70a6ea8fa3b053
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411123"
---
# <a name="24-work-sharing-constructs"></a>2.4 Construcciones de uso compartido

Una construcción de uso compartido distribuye la ejecución de la instrucción asociada entre los miembros del equipo que alcanzarlo. Las directivas de uso compartido no iniciarán nuevos subprocesos, y no hay ninguna barrera implícita en la entrada a una construcción de uso compartido.

Construye la secuencia de uso compartido y **barrera** directivas encontradas deben ser el mismo para todos los subprocesos en un equipo.

OpenMP define las siguientes construcciones de uso compartido y se describen en las secciones siguientes:

- **para** directiva

- **las secciones** directiva

- **solo** directiva