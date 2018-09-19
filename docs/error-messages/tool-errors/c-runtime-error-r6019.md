---
title: C Runtime Error R6019 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95bc763ab39df16c1cfc1b05689560edecf70570
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093314"
---
# <a name="c-runtime-error-r6019"></a>C Runtime Error R6019

no se puede abrir el dispositivo de consola

> [!NOTE]
>  Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque ha intentado acceder a la consola, pero no tiene permisos suficientes. Hay varias razones posibles para este error, pero suele ser porque se debe ejecutar el programa como administrador, o hay un error en el programa.
>
>  Puede intentar seguir estos pasos para corregir este error:
>
>  -   Ejecute el programa como administrador.
> -   Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> -   Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> -   Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error se produce porque la aplicación llama a una función de la consola, pero el sistema operativo no le ha concedido acceso a la consola. Excepto en el modo de depuración, consola generalmente no se permiten funciones en las aplicaciones de Microsoft Store. Si la aplicación requiere privilegios de administrador para su ejecución, asegúrese de que está instalado para ejecutarse como administrador de forma predeterminada.