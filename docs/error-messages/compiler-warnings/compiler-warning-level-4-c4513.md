---
title: Advertencia del compilador (nivel 4) C4513
ms.date: 11/04/2016
f1_keywords:
- C4513
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
ms.openlocfilehash: cbde035a988e5f6ac64303b2ed159b885ece8684
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520086"
---
# <a name="compiler-warning-level-4-c4513"></a>Advertencia del compilador (nivel 4) C4513

'class': no se pudo generar un destructor

El compilador no puede generar un destructor predeterminado para la clase dada; no se creó ningún destructor. El destructor está en una clase base que no sea accesible para la clase derivada. Si la clase base tiene un destructor privado, hacerla pública o protegida.