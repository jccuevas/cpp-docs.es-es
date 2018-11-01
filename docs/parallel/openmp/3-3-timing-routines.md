---
title: 3.3 Rutinas temporales
ms.date: 11/04/2016
ms.assetid: 21060d64-cbe8-4e38-8718-3a68d6a57be3
ms.openlocfilehash: 404e9e168c916b70c7cd32042822f290cd560e98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630482"
---
# <a name="33-timing-routines"></a>3.3 Rutinas temporales

Las funciones descritas en esta sección admiten un temporizador del reloj portátil:

- El `omp_get_wtime` función devuelve el tiempo de reloj transcurrido.

- El `omp_get_wtick` función devuelve los segundos entre ciclos de reloj sucesivos.