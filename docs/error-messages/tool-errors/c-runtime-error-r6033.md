---
title: Error en tiempo de ejecución de C R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 86ac98a2635975b811c7b50020e4d4782675ae4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197022"
---
# <a name="c-runtime-error-r6033"></a>Error en tiempo de ejecución de C R6033

Intento de usar código MSIL de este ensamblado durante la inicialización del código nativo. Esto indica un error en la aplicación. Lo más probable es que se deba a una llamada a una función compilada por MSIL (/CLR) desde un constructor nativo o desde DllMain.

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Este error puede deberse a un error en la aplicación o a un error en un complemento o extensión que usa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para quitar, reparar o reinstalar las extensiones o complementos.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este diagnóstico indica que las instrucciones de MSIL se estaban ejecutando durante el bloqueo del cargador. Esto puede ocurrir si ha compilado nativo C++ mediante el uso de la marca/CLR. Use la marca/CLR solo en módulos que contengan código administrado. Para obtener más información, vea [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).
