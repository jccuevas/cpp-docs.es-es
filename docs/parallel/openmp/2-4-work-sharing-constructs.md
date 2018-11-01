---
title: 2.4 Construcciones de uso compartido
ms.date: 11/04/2016
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
ms.openlocfilehash: e7bf8d37ecdc6a3ef451c9d9746fb47a76a16eb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502887"
---
# <a name="24-work-sharing-constructs"></a>2.4 Construcciones de uso compartido

Una construcción de uso compartido distribuye la ejecución de la instrucción asociada entre los miembros del equipo que alcanzarlo. Las directivas de uso compartido no iniciarán nuevos subprocesos, y no hay ninguna barrera implícita en la entrada a una construcción de uso compartido.

Construye la secuencia de uso compartido y **barrera** directivas encontradas deben ser el mismo para todos los subprocesos en un equipo.

OpenMP define las siguientes construcciones de uso compartido y se describen en las secciones siguientes:

- **para** directiva

- **las secciones** directiva

- **solo** directiva