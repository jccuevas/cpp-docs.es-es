---
title: Error en tiempo de ejecución de C R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 39d8a20dacb0cdeb2a767529e9716bd476f406dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400011"
---
# <a name="c-runtime-error-r6033"></a>Error en tiempo de ejecución de C R6033

Intento de utilizar código MSIL de este ensamblado durante la inicialización del código nativo. Esto indica un error en la aplicación. Lo más probable es que es el resultado de una llamada a una compilación de MSIL (/ clr) función desde un constructor nativo o desde DllMain.

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Este error puede deberse a un error en la aplicación, o a un error en un complemento o una extensión que utiliza.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para quitar, reparar o reinstalar las extensiones o complementos.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este diagnóstico indica que se estaban ejecutando instrucciones MSIL durante el bloqueo del cargador. Esto puede ocurrir si ha compilado C++ nativo mediante el indicador/CLR. Utilice solamente el indicador/CLR en módulos que contienen código administrado. Para obtener más información, consulte [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).