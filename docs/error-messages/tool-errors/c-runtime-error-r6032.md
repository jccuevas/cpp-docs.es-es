---
title: C Runtime Error R6032 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6032
dev_langs:
- C++
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43155f24411fb5206a03d607f0551c2d34294aeb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024208"
---
# <a name="c-runtime-error-r6032"></a>C Runtime Error R6032

No hay espacio suficiente para obtener información de configuración regional

> [!NOTE]
>  Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero a menudo está provocada por una condición muy poca memoria o a un error en el programa.
>
>  Puede intentar seguir estos pasos para corregir este error:
>
>  -   Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> -   Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> -   Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> -   Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

El tiempo de ejecución mantiene información sobre la configuración regional en cada subproceso para que pueden procesar las llamadas a funciones de configuración regional. Si se produce un error en la asignación de memoria para esta información, el tiempo de ejecución no puede continuar porque muchos de sus funciones básicas dependen de él.