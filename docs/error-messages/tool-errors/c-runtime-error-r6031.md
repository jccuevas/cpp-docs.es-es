---
title: C Runtime Error R6031
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: 6ef3f5fa7d063fdc300e6ac28ca519992525851c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564234"
---
# <a name="c-runtime-error-r6031"></a>C Runtime Error R6031

Intento de inicializar la biblioteca CRT de más de una vez. Esto indica un error en la aplicación.

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Esto puede deberse errores en la aplicación o a un error en un complemento o una extensión que usa la aplicación.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para quitar, reparar o reinstalar los programas de complemento o extensión utilizados por la aplicación.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este diagnóstico indica que se estaban ejecutando instrucciones MSIL durante el bloqueo del cargador. Para obtener más información, consulte [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).