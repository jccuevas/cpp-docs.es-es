---
title: Error irrecuperable C1099
ms.date: 11/04/2016
f1_keywords:
- C1099
helpviewer_keywords:
- C1099
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
ms.openlocfilehash: 673a54f705a8ff46ad94167a4458ab538df69c88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387011"
---
# <a name="fatal-error-c1099"></a>Error irrecuperable C1099

El motor de la función Editar y continuar está deteniendo la compilación

Editar y continuar cargó un archivo de encabezado precompilado al preparar la compilación de cambios en el código, pero las acciones posteriores (como los cambios en el código antes de la instrucción `#include` del encabezado precompilado o la detención del depurador) impidieron que Editar y continuar finalizase la compilación con ese proceso. No es necesario realizar ninguna acción para corregir este error.