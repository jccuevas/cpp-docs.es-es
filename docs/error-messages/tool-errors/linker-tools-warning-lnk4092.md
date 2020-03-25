---
title: Advertencia de las herramientas del vinculador LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 706ab843f4b079b507033af76a7f407816fce820
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183363"
---
# <a name="linker-tools-warning-lnk4092"></a>Advertencia de las herramientas del vinculador LNK4092

la sección ' sección ' compartida modificable contiene reubicaciones; es posible que la imagen no se ejecute correctamente

El enlazador emite esta advertencia siempre que tenga una sección compartida para avisarle de un problema potencialmente grave.

Una manera de compartir datos entre varios procesos es marcar una sección como "compartida". Sin embargo, marcar una sección como compartida puede causar problemas. Por ejemplo, tiene un archivo DLL que contiene declaraciones como esta en una sección de datos compartidos:

```
int var = 1;
int *pvar = &var;
```

El enlazador no puede resolver `pvar` porque su valor depende de la carga de la DLL en la memoria, por lo que coloca un registro de reubicación en el archivo DLL. Cuando el archivo DLL se carga en la memoria, la dirección de `var` se puede resolver y `pvar` asignar. Si otro proceso carga el mismo archivo DLL pero no puede cargarlo en la misma dirección, la reubicación de la dirección de `var` se actualizará para el segundo proceso y el espacio de direcciones del primer proceso apuntará a la dirección equivocada.
