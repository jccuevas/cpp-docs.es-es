---
title: C Runtime Error R6031 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6031
dev_langs:
- C++
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83dbcdc433ea731e6ddf0765b4b3a55d5707f429
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059503"
---
# <a name="c-runtime-error-r6031"></a>C Runtime Error R6031

Intento de inicializar la biblioteca CRT de más de una vez. Esto indica un error en la aplicación.

> [!NOTE]
>  Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Esto puede deberse errores en la aplicación o a un error en un complemento o una extensión que usa la aplicación.
>
>  Puede intentar seguir estos pasos para corregir este error:
>
>  -   Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> -   Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para quitar, reparar o reinstalar los programas de complemento o extensión utilizados por la aplicación.
> -   Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> -   Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este diagnóstico indica que se estaban ejecutando instrucciones MSIL durante el bloqueo del cargador. Para obtener más información, consulte [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).