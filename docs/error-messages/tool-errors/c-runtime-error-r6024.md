---
title: C Runtime Error R6024 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6024
dev_langs:
- C++
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df874ae68f786585e85a8bc1b01ea8d0ac831d87
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861296"
---
# <a name="c-runtime-error-r6024"></a>C Runtime Error R6024

No hay suficiente espacio para la tabla atexit/_onexit

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Este error ocurre normalmente extremadamente bajos memoria suficiente, o con poca frecuencia, por un error en el programa o por daños en las bibliotecas de Visual C++ que utiliza.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar todas las copias de Microsoft Visual C++ Redistributable.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error se produce porque no había ninguna memoria disponible para el `_onexit` o `atexit` función. Este error se debe a una condición de memoria baja. Es posible que considere la posibilidad de salir de los búferes de asignación previamente al iniciar la aplicación para ayudar a guardar los datos de usuario y la realización de una aplicación limpia en condiciones de memoria insuficiente.