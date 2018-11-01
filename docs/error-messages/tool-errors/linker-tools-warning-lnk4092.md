---
title: Advertencia de las herramientas del vinculador LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 0b18002135d225a90f7e45adc2ff57a64c0a79f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531042"
---
# <a name="linker-tools-warning-lnk4092"></a>Advertencia de las herramientas del vinculador LNK4092

la sección 'sección' compartida modificable contiene reubicaciones; imagen no se ejecute correctamente

El enlazador emite esta advertencia siempre tiene una sección compartida para avisar de un problema potencialmente grave.

Es una manera de compartir datos entre varios procesos marcar una sección como "compartido". Sin embargo, al marcar una sección como compartido puede causar problemas. Por ejemplo, tiene un archivo DLL que contiene declaraciones como ésta en una sección de datos compartido:

```
int var = 1;
int *pvar = &var;
```

No se puede resolver el vinculador `pvar` porque su valor depende de dónde se carga la DLL en la memoria, por lo que pone un registro de reubicación en el archivo DLL. Cuando se carga el archivo DLL en la memoria, la dirección de `var` se puede resolver y `pvar` asignado. Si otro proceso carga el mismo archivo DLL pero no puede cargarla en la misma dirección, la reubicación de la dirección de `var` se actualizará para el segundo proceso y espacio de direcciones del primer proceso apuntará a la dirección equivocada.