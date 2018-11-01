---
title: Error irrecuperable del compilador de recursos RC1020
ms.date: 11/04/2016
f1_keywords:
- RC1020
helpviewer_keywords:
- RC1020
ms.assetid: 3e073ebf-9136-4bf8-ac6a-3c642ed64594
ms.openlocfilehash: ac4a9d521728b22966f6d8824479d13cc7394601
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631707"
---
# <a name="resource-compiler-fatal-error-rc1020"></a>Error irrecuperable del compilador de recursos RC1020

'#endif' inesperado

Un `#endif` directiva apareciese sin coincidencia `#if`, **#ifdef**, o **#ifndef** directiva.

Asegúrese de que hay una coincidencia `#endif` para cada `#if`, **#ifdef**, y **#ifndef** instrucción.