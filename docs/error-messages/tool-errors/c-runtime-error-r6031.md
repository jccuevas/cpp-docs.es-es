---
title: Error en tiempo de ejecución de C R6031
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: 4b75b0855f0f0d60304cfe8b7a00b4ce27a8daab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197111"
---
# <a name="c-runtime-error-r6031"></a>Error en tiempo de ejecución de C R6031

Intenta inicializar el CRT más de una vez. Esto indica un error en la aplicación.

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Esto puede deberse a un error en la aplicación o a un error en un complemento o extensión que utiliza la aplicación.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para quitar, reparar o reinstalar los complementos o programas de extensión usados por la aplicación.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este diagnóstico indica que las instrucciones de MSIL se estaban ejecutando durante el bloqueo del cargador. Para obtener más información, vea [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).
